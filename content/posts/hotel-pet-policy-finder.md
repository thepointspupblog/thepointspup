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

<div id="pet-policy-finder">

<div class="finder-tabs" id="finder-tabs">
  <button class="finder-tab active" data-tab="lookup">Look Up</button>
  <button class="finder-tab" data-tab="filter">Filter</button>
  <button class="finder-tab" data-tab="recommend">Recommend</button>
  <button class="finder-tab" data-tab="compare">Compare</button>
  <button class="finder-tab" data-tab="stats">Stats</button>
</div>

<!-- LOOK UP -->
<div class="finder-panel active" id="panel-lookup">
  <div id="loading-banner" class="loading-banner">
    <span class="loading-spinner"></span> Loading hotel data — this may take a moment on first visit...
  </div>
  <select id="hotel-select" disabled>
    <option value="">-- Loading hotel chains... --</option>
  </select>
  <div id="lookup-result"></div>
</div>

<!-- FILTER -->
<div class="finder-panel" id="panel-filter">
  <p class="finder-desc">Find hotel chains that match your needs.</p>
  <div class="finder-filters">
    <div class="filter-field">
      <label for="filter-weight">Dog's weight (lbs)</label>
      <input type="number" id="filter-weight" min="0" placeholder="e.g. 70">
    </div>
    <div class="filter-field">
      <label for="filter-fee">Max fee ($)</label>
      <input type="number" id="filter-fee" min="0" placeholder="e.g. 50">
    </div>
    <div class="filter-field">
      <label for="filter-rating">Rating</label>
      <select id="filter-rating">
        <option value="">Any</option>
        <option value="excellent">Excellent</option>
        <option value="good">Good</option>
        <option value="moderate">Moderate</option>
      </select>
    </div>
    <div class="filter-field">
      <label for="filter-search">Search</label>
      <input type="text" id="filter-search" placeholder="e.g. suites">
    </div>
  </div>
  <button class="finder-btn" id="btn-filter">Search</button>
  <div id="filter-results"></div>
</div>

<!-- RECOMMEND -->
<div class="finder-panel" id="panel-recommend">
  <p class="finder-desc">Tell us about your dog and budget — we'll rank the best hotel chains for you.</p>
  <div class="finder-filters">
    <div class="filter-field">
      <label for="rec-weight">Dog's weight (lbs)</label>
      <input type="number" id="rec-weight" min="0" placeholder="e.g. 70">
    </div>
    <div class="filter-field">
      <label for="rec-fee">Max fee ($)</label>
      <input type="number" id="rec-fee" min="0" placeholder="e.g. 50">
    </div>
  </div>
  <button class="finder-btn" id="btn-recommend">Get Recommendations</button>
  <div id="rec-results"></div>
</div>

<!-- COMPARE -->
<div class="finder-panel" id="panel-compare">
  <p class="finder-desc">Select 2–5 chains to compare side by side.</p>
  <div class="finder-checkboxes" id="compare-checks"></div>
  <button class="finder-btn" id="btn-compare">Compare Selected</button>
  <div id="compare-results"></div>
</div>

<!-- STATS -->
<div class="finder-panel" id="panel-stats">
  <div id="stats-results"><p class="finder-desc">Loading stats...</p></div>
</div>

<!-- ADMIN (only visible with ?admin=true URL parameter) -->
<div id="admin-gate" style="display:none; margin-top:2rem; padding-top:1rem; border-top:1px solid #e8e4df;">
  <button class="finder-tab" id="btn-admin-toggle" style="font-size:0.8rem;">Admin</button>
</div>

<div class="finder-panel" id="panel-admin" style="display:none;">
  <div class="admin-login" id="admin-login">
    <label for="admin-key"><strong>API Key</strong></label>
    <div style="display:flex;gap:0.5rem;">
      <input type="password" id="admin-key" placeholder="Enter admin key" style="flex:1;">
      <button class="finder-btn" id="btn-admin-auth">Unlock</button>
    </div>
    <p class="admin-msg" id="admin-msg"></p>
  </div>
  <div id="admin-tools" style="display:none;">
    <div class="admin-section">
      <h4>Update a Hotel Chain</h4>
      <div class="finder-filters">
        <div class="filter-field" style="flex:1 1 100%;">
          <label for="admin-select">Chain to edit</label>
          <select id="admin-select"><option value="">-- Select --</option></select>
        </div>
      </div>
      <div id="admin-edit-fields" style="display:none;">
        <div class="finder-filters">
          <div class="filter-field"><label>Name</label><input type="text" id="edit-name"></div>
          <div class="filter-field"><label>Weight Limit</label><input type="text" id="edit-weightLimit"></div>
          <div class="filter-field"><label>Fee</label><input type="text" id="edit-fee"></div>
          <div class="filter-field"><label>Max Weight (lbs)</label><input type="number" id="edit-maxWeightLbs"></div>
          <div class="filter-field"><label>Rating</label>
            <select id="edit-rating"><option value="excellent">Excellent</option><option value="good">Good</option><option value="moderate">Moderate</option></select>
          </div>
          <div class="filter-field"><label>Website URL</label><input type="text" id="edit-websiteUrl"></div>
        </div>
        <div class="filter-field" style="margin-top:0.5rem;"><label>Notes</label><textarea id="edit-notes" rows="3" style="width:100%;padding:0.5rem;border:2px solid #e8e4df;border-radius:8px;font-family:inherit;resize:vertical;"></textarea></div>
        <div class="filter-field" style="margin-top:0.5rem;"><label>Tip</label><textarea id="edit-tip" rows="2" style="width:100%;padding:0.5rem;border:2px solid #e8e4df;border-radius:8px;font-family:inherit;resize:vertical;"></textarea></div>
        <div class="filter-field" style="margin-top:0.5rem;"><label>Verdict</label><input type="text" id="edit-verdict" style="width:100%;"></div>
        <div style="display:flex;gap:0.5rem;margin-top:1rem;">
          <button class="finder-btn" id="btn-save">Save Changes</button>
          <button class="finder-btn finder-btn-danger" id="btn-delete">Delete Chain</button>
        </div>
      </div>
    </div>
    <div class="admin-section" style="margin-top:1.5rem;">
      <h4>Add New Hotel Chain</h4>
      <div class="finder-filters">
        <div class="filter-field"><label>ID (lowercase, no spaces)</label><input type="text" id="add-id" placeholder="e.g. newchain"></div>
        <div class="filter-field"><label>Name</label><input type="text" id="add-name" placeholder="e.g. New Chain Hotels"></div>
        <div class="filter-field"><label>Weight Limit</label><input type="text" id="add-weightLimit" placeholder="e.g. Up to 75 lbs"></div>
        <div class="filter-field"><label>Fee</label><input type="text" id="add-fee" placeholder="e.g. $50 per stay"></div>
        <div class="filter-field"><label>Rating</label>
          <select id="add-rating"><option value="good">Good</option><option value="excellent">Excellent</option><option value="moderate">Moderate</option></select>
        </div>
      </div>
      <button class="finder-btn" id="btn-add" style="margin-top:0.75rem;">Add Chain</button>
    </div>
    <p class="admin-msg" id="admin-result"></p>
  </div>
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
let adminKey = "";
const isAdmin = new URLSearchParams(window.location.search).get('admin') === 'true';
if (isAdmin) document.getElementById('admin-gate').style.display = 'block';

function card(p, rank) {
  const emoji = ratingEmoji[p.rating] || "🟡";
  const guide = guideLinks[p.id] ? ` <a href="${guideLinks[p.id]}">Full guide →</a>` : "";
  const badge = rank ? `<span class="rank-num">${rank}</span>` : "";
  const updated = p.lastUpdated ? `<span class="last-updated">Updated ${new Date(p.lastUpdated).toLocaleDateString()}</span>` : "";
  return `<div class="result-card">
    <div class="result-header">${badge}<strong>${p.name}</strong>${updated}</div>
    <div class="result-body">
      <div class="result-row"><span class="result-label">Weight Limit</span><span>${p.weightLimit || 'N/A'}</span></div>
      <div class="result-row"><span class="result-label">Pet Fee</span><span>${p.fee || 'N/A'}</span></div>
      <div class="result-row"><span class="result-label">Notes</span><span>${p.notes || ''}</span></div>
      <div class="result-row"><span class="result-label">Tip</span><span>${p.tip || ''}${guide}</span></div>
      <div class="result-verdict">${emoji} ${p.verdict || ''}</div>
    </div>
  </div>`;
}

function msg(el, text, isError) {
  el.textContent = text;
  el.style.color = isError ? "#c0392b" : "#2d5a47";
}

// Tabs
document.getElementById('finder-tabs').addEventListener('click', function(e) {
  if (!e.target.classList.contains('finder-tab')) return;
  document.querySelectorAll('.finder-tab').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.finder-panel').forEach(p => p.classList.remove('active'));
  e.target.classList.add('active');
  document.getElementById('panel-' + e.target.dataset.tab).classList.add('active');
  if (e.target.dataset.tab === 'stats') loadStats();
});

// Load hotels
async function loadHotels() {
  const banner = document.getElementById('loading-banner');
  const select = document.getElementById('hotel-select');
  try {
    const res = await fetch(API + "/hotels", { signal: AbortSignal.timeout(60000) });
    if (!res.ok) throw new Error();
    const hotels = await res.json();
    hotels.sort((a, b) => a.name.localeCompare(b.name));
    const adminSelect = document.getElementById('admin-select');
    const checks = document.getElementById('compare-checks');
    select.innerHTML = '<option value="">-- Choose a hotel chain --</option>';
    hotels.forEach(h => {
      select.innerHTML += `<option value="${h.id}">${h.name}</option>`;
      if (isAdmin) adminSelect.innerHTML += `<option value="${h.id}">${h.name}</option>`;
      checks.innerHTML += `<label class="check-label"><input type="checkbox" value="${h.id}"><span>${h.name}</span></label>`;
    });
    select.disabled = false;
    banner.style.display = 'none';
  } catch (e) {
    banner.innerHTML = '<span class="loading-spinner"></span> Server is waking up — retrying...';
    setTimeout(loadHotels, 5000);
  }
}

// Look Up
document.getElementById('hotel-select').addEventListener('change', async function() {
  const div = document.getElementById('lookup-result');
  if (!this.value) { div.innerHTML = ''; return; }
  try {
    const res = await fetch(API + "/hotels/" + this.value);
    if (!res.ok) throw new Error();
    div.innerHTML = card(await res.json());
  } catch (e) { div.innerHTML = '<p class="finder-error">Unable to load. Try again.</p>'; }
});

// Filter
document.getElementById('btn-filter').addEventListener('click', async function() {
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
    const res = await fetch(API + "/hotels?" + params);
    const hotels = await res.json();
    div.innerHTML = hotels.length === 0
      ? '<p class="finder-error">No chains match your filters.</p>'
      : `<p class="result-count">${hotels.length} chain${hotels.length !== 1 ? 's' : ''} found</p>` + hotels.map(h => card(h)).join('');
  } catch (e) { div.innerHTML = '<p class="finder-error">Unable to load. Try again.</p>'; }
});

// Recommend
document.getElementById('btn-recommend').addEventListener('click', async function() {
  const params = new URLSearchParams();
  const w = document.getElementById('rec-weight').value;
  const f = document.getElementById('rec-fee').value;
  if (w) params.set('weight', w);
  if (f) params.set('maxFee', f);
  const div = document.getElementById('rec-results');
  try {
    const res = await fetch(API + "/hotels/recommend?" + params);
    const hotels = await res.json();
    div.innerHTML = hotels.length === 0
      ? '<p class="finder-error">No chains match.</p>'
      : hotels.map((h, i) => card(h, i + 1)).join('');
  } catch (e) { div.innerHTML = '<p class="finder-error">Unable to load. Try again.</p>'; }
});

// Compare
document.getElementById('btn-compare').addEventListener('click', async function() {
  const ids = [...document.querySelectorAll('#compare-checks input:checked')].map(c => c.value);
  const div = document.getElementById('compare-results');
  if (ids.length < 2 || ids.length > 5) {
    div.innerHTML = '<p class="finder-error">Select 2–5 chains to compare.</p>';
    return;
  }
  try {
    const res = await fetch(API + "/hotels/compare?ids=" + ids.join(','));
    if (!res.ok) throw new Error();
    const hotels = await res.json();
    div.innerHTML = '<div class="compare-grid">' + hotels.map(h => card(h)).join('') + '</div>';
  } catch (e) { div.innerHTML = '<p class="finder-error">Unable to load. Try again.</p>'; }
});

// Stats
async function loadStats() {
  const div = document.getElementById('stats-results');
  try {
    const res = await fetch(API + "/stats");
    const s = await res.json();
    div.innerHTML = `<div class="stats-grid">
      <div class="stat-card"><div class="stat-num">${s.totalChains}</div><div class="stat-label">Hotel Chains</div></div>
      <div class="stat-card"><div class="stat-num">${s.noFeeChains}</div><div class="stat-label">No Pet Fee</div></div>
      <div class="stat-card"><div class="stat-num">${s.noWeightLimitChains}</div><div class="stat-label">No Weight Limit</div></div>
      <div class="stat-card"><div class="stat-num">${s.ratingBreakdown.excellent}</div><div class="stat-label">Excellent</div></div>
      <div class="stat-card"><div class="stat-num">${s.ratingBreakdown.good}</div><div class="stat-label">Good</div></div>
      <div class="stat-card"><div class="stat-num">${s.ratingBreakdown.moderate}</div><div class="stat-label">Moderate</div></div>
    </div>`;
  } catch (e) { div.innerHTML = '<p class="finder-error">Unable to load stats.</p>'; }
}

// Admin toggle
document.getElementById('btn-admin-toggle').addEventListener('click', function() {
  const panel = document.getElementById('panel-admin');
  panel.style.display = panel.style.display === 'none' ? 'block' : 'none';
});

// Admin auth
document.getElementById('btn-admin-auth').addEventListener('click', async function() {
  adminKey = document.getElementById('admin-key').value;
  const msgEl = document.getElementById('admin-msg');
  try {
    const res = await fetch(API + "/hotels/kimpton", { method: 'PUT', headers: { 'X-API-Key': adminKey, 'Content-Type': 'application/json' },
      body: '{"id":"kimpton","name":"Kimpton Hotels","weightLimit":"No weight limit","fee":"$0 (free!)","breedRestrictions":false,"maxWeightLbs":null,"notes":"The gold standard for dog travel. If your dog fits through the door, they\'re welcome. No breed restrictions. Every property has a Director of Pet Relations. Wine hour welcomes pups.","tip":"Book free with IHG points. Part of IHG One Rewards. The IHG Premier card\'s 4th night free benefit saves 25% on points stays.","verdict":"Best in class -- no limits, no fees","rating":"excellent","websiteUrl":"https://www.kimptonhotels.com"}'
    });
    if (res.status === 401) { msg(msgEl, "Invalid API key.", true); adminKey = ""; return; }
    document.getElementById('admin-login').style.display = 'none';
    document.getElementById('admin-tools').style.display = 'block';
  } catch (e) { msg(msgEl, "Connection error.", true); }
});

// Admin: load chain for editing
document.getElementById('admin-select').addEventListener('change', async function() {
  const fields = document.getElementById('admin-edit-fields');
  if (!this.value) { fields.style.display = 'none'; return; }
  try {
    const res = await fetch(API + "/hotels/" + this.value);
    const h = await res.json();
    document.getElementById('edit-name').value = h.name || '';
    document.getElementById('edit-weightLimit').value = h.weightLimit || '';
    document.getElementById('edit-fee').value = h.fee || '';
    document.getElementById('edit-maxWeightLbs').value = h.maxWeightLbs || '';
    document.getElementById('edit-rating').value = h.rating || 'good';
    document.getElementById('edit-websiteUrl').value = h.websiteUrl || '';
    document.getElementById('edit-notes').value = h.notes || '';
    document.getElementById('edit-tip').value = h.tip || '';
    document.getElementById('edit-verdict').value = h.verdict || '';
    fields.style.display = 'block';
  } catch (e) { fields.style.display = 'none'; }
});

// Admin: save
document.getElementById('btn-save').addEventListener('click', async function() {
  const id = document.getElementById('admin-select').value;
  const msgEl = document.getElementById('admin-result');
  if (!id) return;
  const body = {
    id: id,
    name: document.getElementById('edit-name').value,
    weightLimit: document.getElementById('edit-weightLimit').value,
    fee: document.getElementById('edit-fee').value,
    maxWeightLbs: document.getElementById('edit-maxWeightLbs').value ? parseInt(document.getElementById('edit-maxWeightLbs').value) : null,
    breedRestrictions: false,
    rating: document.getElementById('edit-rating').value,
    websiteUrl: document.getElementById('edit-websiteUrl').value,
    notes: document.getElementById('edit-notes').value,
    tip: document.getElementById('edit-tip').value,
    verdict: document.getElementById('edit-verdict').value
  };
  try {
    const res = await fetch(API + "/hotels/" + id, {
      method: 'PUT', headers: { 'X-API-Key': adminKey, 'Content-Type': 'application/json' },
      body: JSON.stringify(body)
    });
    if (res.ok) msg(msgEl, "Saved successfully!", false);
    else { const e = await res.json(); msg(msgEl, e.message || "Error saving.", true); }
  } catch (e) { msg(msgEl, "Connection error.", true); }
});

// Admin: delete
document.getElementById('btn-delete').addEventListener('click', async function() {
  const id = document.getElementById('admin-select').value;
  const msgEl = document.getElementById('admin-result');
  if (!id || !confirm("Delete " + id + "? This cannot be undone.")) return;
  try {
    const res = await fetch(API + "/hotels/" + id, {
      method: 'DELETE', headers: { 'X-API-Key': adminKey }
    });
    if (res.ok) { msg(msgEl, "Deleted.", false); document.getElementById('admin-edit-fields').style.display = 'none'; }
    else msg(msgEl, "Error deleting.", true);
  } catch (e) { msg(msgEl, "Connection error.", true); }
});

// Admin: add
document.getElementById('btn-add').addEventListener('click', async function() {
  const msgEl = document.getElementById('admin-result');
  const body = {
    id: document.getElementById('add-id').value,
    name: document.getElementById('add-name').value,
    weightLimit: document.getElementById('add-weightLimit').value,
    fee: document.getElementById('add-fee').value,
    breedRestrictions: false,
    rating: document.getElementById('add-rating').value,
    notes: "", tip: "", verdict: "", websiteUrl: "", maxWeightLbs: null
  };
  if (!body.id || !body.name) { msg(msgEl, "ID and Name are required.", true); return; }
  try {
    const res = await fetch(API + "/hotels", {
      method: 'POST', headers: { 'X-API-Key': adminKey, 'Content-Type': 'application/json' },
      body: JSON.stringify(body)
    });
    if (res.ok) msg(msgEl, "Added " + body.name + "!", false);
    else { const e = await res.json(); msg(msgEl, e.message || "Error adding.", true); }
  } catch (e) { msg(msgEl, "Connection error.", true); }
});

loadHotels();
</script>

---

## The Bottom Line

Weight limits are frustrating, but there are great options for dogs of all sizes. For large dogs, **Kimpton**, **Red Roof Inn**, **Motel 6**, and **Loews** are your best bets.

**Want the full breakdown?** Check out my complete guide: [Traveling with a Large Dog: Hotel Policies You Need to Know](/posts/traveling-with-large-dogs-hotel-policies/)

**Ready to book for free?** See [Best Credit Cards for Dog Travelers](/posts/best-credit-cards-pet-travelers/) to start earning points.
