---
title: "Hotel Pet Policy Finder: Weight Limits, Fees & Rules by Chain"
description: "Instantly check pet weight limits, fees, and policies for major hotel chains — especially helpful for large dog owners."
date: 2025-12-08
categories:
  - Tools
tags:
  - Pet Policy
  - Large Dogs
  - Hotels
---

Not sure if your dog is welcome? Use this tool to quickly check pet policies for major hotel chains.

<style>
#pet-policy-finder { max-width: 700px; }
#pet-policy-finder select, #pet-policy-finder input {
  padding: 0.5rem; border: 1px solid #ccc; border-radius: 6px; font-size: 0.95rem;
}
#pet-policy-finder select { width: 100%; margin-top: 0.25rem; }
#pet-policy-finder input { width: 80px; }
.tool-tabs { display: flex; gap: 0.5rem; margin-bottom: 1.5rem; flex-wrap: wrap; }
.tool-tabs button {
  padding: 0.5rem 1rem; border: 2px solid #2d5a47; border-radius: 8px;
  background: transparent; color: #2d5a47; font-weight: 600; cursor: pointer; font-size: 0.85rem;
}
.tool-tabs button.active { background: #2d5a47; color: white; }
.tool-section { display: none; }
.tool-section.active { display: block; }
.policy-card {
  margin-top: 1rem; padding: 1.25rem; background: #f9f6f1;
  border-radius: 12px; border: 2px solid #2d5a47;
}
.policy-card h3 { margin-top: 0; color: #2d5a47; }
.policy-card p { margin: 0.4rem 0; }
.compare-grid { display: grid; gap: 1rem; margin-top: 1rem; }
.filter-row { display: flex; gap: 1rem; flex-wrap: wrap; align-items: end; margin-bottom: 1rem; }
.filter-row label { font-size: 0.85rem; font-weight: 600; }
.filter-row > div { display: flex; flex-direction: column; gap: 0.25rem; }
.btn {
  padding: 0.5rem 1.25rem; background: #2d5a47; color: white;
  border: none; border-radius: 6px; cursor: pointer; font-weight: 600; font-size: 0.85rem;
}
.btn:hover { background: #1e3d30; }
.stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 1rem; margin-top: 1rem; }
.stat-card {
  padding: 1rem; background: #f9f6f1; border-radius: 10px;
  border: 1px solid #ddd; text-align: center;
}
.stat-card .number { font-size: 1.75rem; font-weight: 700; color: #2d5a47; }
.stat-card .label { font-size: 0.8rem; color: #666; margin-top: 0.25rem; }
.compare-check { display: flex; flex-wrap: wrap; gap: 0.5rem; margin: 0.75rem 0; }
.compare-check label {
  padding: 0.35rem 0.75rem; border: 1px solid #ccc; border-radius: 6px;
  font-size: 0.8rem; cursor: pointer; user-select: none;
}
.compare-check input:checked + span { color: #2d5a47; font-weight: 600; }
.compare-check input { display: none; }
.compare-check label:has(input:checked) { border-color: #2d5a47; background: #edf5f0; }
#api-status { font-size: 0.75rem; margin-left: 0.5rem; }
.rank-badge {
  display: inline-block; width: 24px; height: 24px; border-radius: 50%;
  background: #2d5a47; color: white; text-align: center; line-height: 24px;
  font-size: 0.75rem; font-weight: 700; margin-right: 0.5rem;
}
</style>

<div id="pet-policy-finder">

<div class="tool-tabs">
  <button class="active" onclick="switchTab('lookup')">Look Up</button>
  <button onclick="switchTab('filter')">Filter</button>
  <button onclick="switchTab('recommend')">Recommend</button>
  <button onclick="switchTab('compare')">Compare</button>
  <button onclick="switchTab('stats')">Stats</button>
</div>

<!-- LOOK UP -->
<div id="tab-lookup" class="tool-section active">
  <label for="hotel-select"><strong>Select a hotel chain:</strong></label>
  <span id="api-status"></span>
  <select id="hotel-select">
    <option value="">-- Choose a chain --</option>
  </select>
  <div id="lookup-result"></div>
</div>

<!-- FILTER -->
<div id="tab-filter" class="tool-section">
  <div class="filter-row">
    <div>
      <label>Dog's weight (lbs)</label>
      <input type="number" id="filter-weight" min="0" placeholder="e.g. 70">
    </div>
    <div>
      <label>Max fee ($)</label>
      <input type="number" id="filter-fee" min="0" placeholder="e.g. 50">
    </div>
    <div>
      <label>Rating</label>
      <select id="filter-rating">
        <option value="">Any</option>
        <option value="excellent">Excellent</option>
        <option value="good">Good</option>
        <option value="moderate">Moderate</option>
      </select>
    </div>
    <div>
      <label>Search</label>
      <input type="text" id="filter-search" placeholder="e.g. suites" style="width: 120px;">
    </div>
    <button class="btn" onclick="runFilter()">Search</button>
  </div>
  <div id="filter-results"></div>
</div>

<!-- RECOMMEND -->
<div id="tab-recommend" class="tool-section">
  <p>Tell us about your dog and budget — we'll rank the best hotel chains for you.</p>
  <div class="filter-row">
    <div>
      <label>Dog's weight (lbs)</label>
      <input type="number" id="rec-weight" min="0" placeholder="e.g. 70">
    </div>
    <div>
      <label>Max fee ($)</label>
      <input type="number" id="rec-fee" min="0" placeholder="e.g. 50">
    </div>
    <button class="btn" onclick="runRecommend()">Get Recommendations</button>
  </div>
  <div id="rec-results"></div>
</div>

<!-- COMPARE -->
<div id="tab-compare" class="tool-section">
  <p><strong>Select 2-5 chains to compare side by side:</strong></p>
  <div id="compare-checkboxes" class="compare-check"></div>
  <button class="btn" onclick="runCompare()">Compare</button>
  <div id="compare-results"></div>
</div>

<!-- STATS -->
<div id="tab-stats" class="tool-section">
  <div id="stats-results"><p>Loading stats...</p></div>
</div>

</div>

<script>
const API = "https://pet-policy-api.onrender.com/api";

const guideLinks = {
  hilton: "/posts/hilton-pet-policy-2026/",
  marriott: "/posts/marriott-pet-policy-2026/",
  ihg: "/posts/ihg-kimpton-pet-travel-guide/",
  hyatt: "/posts/hyatt-pet-policy-2026/",
  kimpton: "/posts/kimpton-pet-policy-2026/"
};
const ratingEmoji = { excellent: "🟢", good: "🟢", moderate: "🟡" };

function policyCard(p, rank) {
  const emoji = ratingEmoji[p.rating] || "🟡";
  const guide = guideLinks[p.id] ? ` <a href="${guideLinks[p.id]}">Full guide →</a>` : "";
  const badge = rank ? `<span class="rank-badge">${rank}</span>` : "";
  return `<div class="policy-card">
    <h3>${badge}${p.name}</h3>
    <p><strong>Weight Limit:</strong> ${p.weightLimit}</p>
    <p><strong>Pet Fee:</strong> ${p.fee}</p>
    <p><strong>Notes:</strong> ${p.notes}</p>
    <p><strong>💡 Tip:</strong> ${p.tip}${guide}</p>
    <p style="font-size: 1.05rem; font-weight: 600;">${emoji} ${p.verdict}</p>
  </div>`;
}

function switchTab(name) {
  document.querySelectorAll('.tool-section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.tool-tabs button').forEach(b => b.classList.remove('active'));
  document.getElementById('tab-' + name).classList.add('active');
  event.target.classList.add('active');
  if (name === 'stats') loadStats();
}

// --- LOOK UP ---
async function loadHotels() {
  const select = document.getElementById('hotel-select');
  const status = document.getElementById('api-status');
  try {
    const res = await fetch(API + "/hotels", { signal: AbortSignal.timeout(8000) });
    if (!res.ok) throw new Error();
    const hotels = await res.json();
    hotels.sort((a, b) => a.name.localeCompare(b.name));
    hotels.forEach(h => {
      const opt = document.createElement('option');
      opt.value = h.id;
      opt.textContent = h.name;
      select.appendChild(opt);
    });
    populateCompareCheckboxes(hotels);
    status.textContent = "✓ Live data";
    status.style.color = "#2d5a47";
  } catch (e) {
    status.textContent = "⏳ Connecting...";
    setTimeout(loadHotels, 5000);
  }
}

document.getElementById('hotel-select').addEventListener('change', async function() {
  const div = document.getElementById('lookup-result');
  if (!this.value) { div.innerHTML = ''; return; }
  try {
    const res = await fetch(API + "/hotels/" + this.value, { signal: AbortSignal.timeout(5000) });
    if (!res.ok) throw new Error();
    div.innerHTML = policyCard(await res.json());
  } catch (e) {
    div.innerHTML = '<div class="policy-card"><p>Unable to load. Please try again.</p></div>';
  }
});

// --- FILTER ---
async function runFilter() {
  const params = new URLSearchParams();
  const w = document.getElementById('filter-weight').value;
  const f = document.getElementById('filter-fee').value;
  const r = document.getElementById('filter-rating').value;
  const s = document.getElementById('filter-search').value;
  if (w) params.set('minWeight', w);
  if (f) params.set('maxFee', f);
  if (r) params.set('rating', r);
  if (s) params.set('search', s);

  const div = document.getElementById('filter-results');
  try {
    const res = await fetch(API + "/hotels?" + params, { signal: AbortSignal.timeout(5000) });
    if (!res.ok) throw new Error();
    const hotels = await res.json();
    if (hotels.length === 0) {
      div.innerHTML = '<div class="policy-card"><p>No chains match your filters. Try broadening your search.</p></div>';
    } else {
      div.innerHTML = `<p style="margin-top:0.5rem;color:#666;font-size:0.85rem;">${hotels.length} chain${hotels.length > 1 ? 's' : ''} found</p>` + hotels.map(h => policyCard(h)).join('');
    }
  } catch (e) {
    div.innerHTML = '<div class="policy-card"><p>Unable to load. Please try again.</p></div>';
  }
}

// --- RECOMMEND ---
async function runRecommend() {
  const params = new URLSearchParams();
  const w = document.getElementById('rec-weight').value;
  const f = document.getElementById('rec-fee').value;
  if (w) params.set('weight', w);
  if (f) params.set('maxFee', f);

  const div = document.getElementById('rec-results');
  try {
    const res = await fetch(API + "/hotels/recommend?" + params, { signal: AbortSignal.timeout(5000) });
    if (!res.ok) throw new Error();
    const hotels = await res.json();
    if (hotels.length === 0) {
      div.innerHTML = '<div class="policy-card"><p>No chains match. Try adjusting your criteria.</p></div>';
    } else {
      div.innerHTML = hotels.map((h, i) => policyCard(h, i + 1)).join('');
    }
  } catch (e) {
    div.innerHTML = '<div class="policy-card"><p>Unable to load. Please try again.</p></div>';
  }
}

// --- COMPARE ---
function populateCompareCheckboxes(hotels) {
  const container = document.getElementById('compare-checkboxes');
  hotels.sort((a, b) => a.name.localeCompare(b.name)).forEach(h => {
    container.innerHTML += `<label><input type="checkbox" value="${h.id}"><span>${h.name}</span></label>`;
  });
}

async function runCompare() {
  const checked = [...document.querySelectorAll('#compare-checkboxes input:checked')].map(c => c.value);
  const div = document.getElementById('compare-results');
  if (checked.length < 2 || checked.length > 5) {
    div.innerHTML = '<div class="policy-card"><p>Please select 2-5 chains to compare.</p></div>';
    return;
  }
  try {
    const res = await fetch(API + "/hotels/compare?ids=" + checked.join(','), { signal: AbortSignal.timeout(5000) });
    if (!res.ok) throw new Error();
    const hotels = await res.json();
    div.innerHTML = '<div class="compare-grid">' + hotels.map(h => policyCard(h)).join('') + '</div>';
  } catch (e) {
    div.innerHTML = '<div class="policy-card"><p>Unable to load. Please try again.</p></div>';
  }
}

// --- STATS ---
async function loadStats() {
  const div = document.getElementById('stats-results');
  try {
    const res = await fetch(API + "/stats", { signal: AbortSignal.timeout(5000) });
    if (!res.ok) throw new Error();
    const s = await res.json();
    div.innerHTML = `<div class="stats-grid">
      <div class="stat-card"><div class="number">${s.totalChains}</div><div class="label">Hotel Chains</div></div>
      <div class="stat-card"><div class="number">${s.noFeeChains}</div><div class="label">No Pet Fee</div></div>
      <div class="stat-card"><div class="number">${s.noWeightLimitChains}</div><div class="label">No Weight Limit</div></div>
      <div class="stat-card"><div class="number">${s.ratingBreakdown.excellent}</div><div class="label">Excellent Rated</div></div>
      <div class="stat-card"><div class="number">${s.ratingBreakdown.good}</div><div class="label">Good Rated</div></div>
      <div class="stat-card"><div class="number">${s.ratingBreakdown.moderate}</div><div class="label">Moderate Rated</div></div>
    </div>`;
  } catch (e) {
    div.innerHTML = '<div class="policy-card"><p>Unable to load stats. Please try again.</p></div>';
  }
}

loadHotels();
</script>

---

## The Bottom Line

Weight limits are frustrating, but there are great options for dogs of all sizes. For large dogs, **Kimpton**, **Red Roof Inn**, **Motel 6**, and **Loews** are your best bets.

**Want the full breakdown?** Check out my complete guide: [Traveling with a Large Dog: Hotel Policies You Need to Know](/posts/traveling-with-large-dogs-hotel-policies/)

**Ready to book for free?** See [Best Credit Cards for Dog Travelers](/posts/best-credit-cards-pet-travelers/) to start earning points.
