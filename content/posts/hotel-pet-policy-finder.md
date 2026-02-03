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
  <label for="hotel-select"><strong>Select a hotel chain:</strong></label>
  <select id="hotel-select">
    <option value="">-- Choose a chain --</option>
    <option value="hilton">Hilton</option>
    <option value="marriott">Marriott</option>
    <option value="ihg">IHG (Holiday Inn, Staybridge, etc.)</option>
    <option value="hyatt">Hyatt</option>
    <option value="kimpton">Kimpton Hotels (IHG)</option>
    <option value="wyndham">Wyndham (La Quinta, etc.)</option>
    <option value="bestwestern">Best Western</option>
    <option value="choice">Choice (Comfort Inn, Quality Inn, etc.)</option>
    <option value="motel6">Motel 6 / Studio 6</option>
    <option value="redroof">Red Roof Inn</option>
    <option value="drury">Drury Hotels</option>
    <option value="loews">Loews Hotels</option>
    <option value="extendedstay">Extended Stay America</option>
    <option value="sonesta">Sonesta</option>
    <option value="omni">Omni Hotels</option>
    <option value="fourseasons">Four Seasons</option>
  </select>

  <div id="policy-result" style="display: none; margin-top: 1.5rem; padding: 1.5rem; background: #f9f6f1; border-radius: 12px; border: 2px solid #2d5a47;">
  </div>
</div>

<script>
const policies = {
  hilton: {
    name: "Hilton",
    weight: "Typically 75 lbs (varies by brand/property)",
    fee: "$50-$95 per stay (varies by brand)",
    notes: "All Hilton brands accept pets. Home2 Suites, Homewood Suites, and Embassy Suites are most dog-friendly with more space. No corporate breed restrictions.",
    tip: "Book free with Hilton Honors points — pay only the pet fee. <a href='/posts/hilton-pet-policy-2026/'>Full Hilton pet policy guide →</a>",
    verdict: "🟢 Good for most dogs under 75 lbs"
  },
  marriott: {
    name: "Marriott",
    weight: "Varies widely (25-100 lbs depending on brand)",
    fee: "$50-$250 per stay (varies significantly)",
    notes: "Policies vary by brand and location. TownePlace Suites (up to 100 lbs), Residence Inn, and Element are most pet-friendly. Always call the specific property.",
    tip: "Book free with Marriott Bonvoy points. <a href='/posts/marriott-pet-policy-2026/'>Full Marriott pet policy guide →</a>",
    verdict: "🟡 Varies widely — always call ahead"
  },
  ihg: {
    name: "IHG (Holiday Inn, Staybridge, etc.)",
    weight: "Varies by brand (typically 40-80 lbs)",
    fee: "$25-$100 depending on brand",
    notes: "Staybridge Suites (50 lbs) and Candlewood Suites (80 lbs) are most pet-friendly non-Kimpton brands. Holiday Inn policies vary by location.",
    tip: "For large dogs, book Kimpton instead (also IHG). <a href='/posts/ihg-kimpton-pet-travel-guide/'>Full IHG pet policy guide →</a>",
    verdict: "🟡 Moderate — Kimpton is better for large dogs"
  },
  hyatt: {
    name: "Hyatt",
    weight: "Typically 50 lbs (Thompson/Andaz may have no limit)",
    fee: "$50-$150 per stay",
    notes: "Hyatt Place and Hyatt House are most consistent. Thompson and Andaz are boutique brands with more flexible policies. Always call the specific property.",
    tip: "Book free with Chase points (transfer to World of Hyatt). <a href='/posts/hyatt-pet-policy-2026/'>Full Hyatt pet policy guide →</a>",
    verdict: "🟡 Good — Thompson/Andaz best for large dogs"
  },
  wyndham: {
    name: "Wyndham (La Quinta, etc.)",
    weight: "La Quinta: No weight limit (policies changing)",
    fee: "$0-$25/night at La Quinta",
    notes: "La Quinta was famous for no pet fees and no weight limits. Since Wyndham acquired them, some locations have added restrictions. Always call to confirm.",
    tip: "La Quinta is still one of the best budget options for large dogs.",
    verdict: "🟢 La Quinta is great, call to confirm"
  },
  bestwestern: {
    name: "Best Western",
    weight: "Up to 80 lbs per dog",
    fee: "$20-$30 per night",
    notes: "Most locations allow up to 2 dogs. Policies can vary by property, so call ahead for specific rules.",
    tip: "One of the more consistent mid-range options for larger dogs.",
    verdict: "🟢 Good for dogs under 80 lbs"
  },
  choice: {
    name: "Choice Hotels (Comfort Inn, Quality Inn, etc.)",
    weight: "Varies (typically up to 50 lbs)",
    fee: "$20-$50 per night",
    notes: "Policies vary significantly by property. Many Choice hotels are franchised, so rules depend on the owner.",
    tip: "Always call the specific location to confirm their pet policy.",
    verdict: "🟡 Inconsistent — always call"
  },
  motel6: {
    name: "Motel 6 / Studio 6",
    weight: "No weight limit",
    fee: "$0 at Motel 6, ~$10/night at Studio 6",
    notes: "No breed restrictions. One of the most consistently pet-friendly budget chains. Pets must be attended or crated.",
    tip: "Best budget option for large dogs — no questions asked.",
    verdict: "🟢 Excellent for all dog sizes"
  },
  redroof: {
    name: "Red Roof Inn",
    weight: "No weight limit",
    fee: "$0 (free!)",
    notes: "No breed restrictions. One well-behaved pet per room. They even have designated pet walk areas at each location.",
    tip: "One of the best budget options — truly pet-friendly with no fees.",
    verdict: "🟢 Excellent — no fees, no limits"
  },
  drury: {
    name: "Drury Hotels",
    weight: "Up to 80 lbs combined (for multiple pets)",
    fee: "$50 per night",
    notes: "Up to 2 pets allowed. Known for excellent customer service and free extras (breakfast, evening drinks).",
    tip: "Great mid-range option with reliable pet policies.",
    verdict: "🟢 Good for dogs under 80 lbs"
  },
  loews: {
    name: "Loews Hotels",
    weight: "No weight limit",
    fee: "Varies ($50-$100 per stay)",
    notes: "The 'Loews Loves Pets' program provides beds, bowls, treats, and even a room service menu for dogs. Very upscale pet experience.",
    tip: "Splurge-worthy for special trips with your pup.",
    verdict: "🟢 Excellent — luxury pet experience"
  },
  kimpton: {
    name: "Kimpton Hotels",
    weight: "No weight limit",
    fee: "$0 (free!)",
    notes: "The gold standard for dog travel. If your dog fits through the door, they're welcome. No breed restrictions. Every property has a Director of Pet Relations. Wine hour welcomes pups.",
    tip: "Book free with IHG points. <a href='/posts/kimpton-pet-policy-2026/'>Full Kimpton guide →</a> | <a href='/posts/kimpton-points-guide/'>How to book free →</a>",
    verdict: "🟢 Best in class — no limits, no fees"
  },
  extendedstay: {
    name: "Extended Stay America",
    weight: "Up to 2 pets, combined weight under 50 lbs",
    fee: "$25 per night (max $150 per stay)",
    notes: "Budget extended-stay chain with kitchens in every room. Good for longer trips. Policies can vary by location — some franchise locations have different rules.",
    tip: "Good budget option if your dogs are small. Always call to confirm the specific location's policy.",
    verdict: "🟡 Budget-friendly but strict weight limit"
  },
  sonesta: {
    name: "Sonesta",
    weight: "No weight limit at most properties",
    fee: "$75-$100 per stay",
    notes: "Sonesta and Sonesta Simply Suites welcome dogs of all sizes at most locations. Royal Sonesta and other luxury tiers may have restrictions. Call to confirm.",
    tip: "Good option for large dogs when Kimpton isn't available.",
    verdict: "🟢 Good for large dogs — call to confirm"
  },
  omni: {
    name: "Omni Hotels",
    weight: "Up to 25 lbs (some locations 50 lbs)",
    fee: "$50-$150 per stay",
    notes: "Omni's 'Omni Sensational Pets' program provides beds, bowls, and treats. However, weight limits are strict and vary by property. Luxury chain with higher fees.",
    tip: "Call ahead — weight limits are strictly enforced at most locations.",
    verdict: "🟡 Nice amenities but strict weight limits"
  },
  fourseasons: {
    name: "Four Seasons",
    weight: "Varies by property (often no limit)",
    fee: "$0-$50 per stay (many waive fees)",
    notes: "Ultra-luxury chain that genuinely welcomes dogs. Many properties have no weight limits and provide luxury pet amenities — beds, treats, even room service menus for dogs.",
    tip: "If budget allows, this is the most pampered pet experience. Call to confirm specific property policies.",
    verdict: "🟢 Luxury experience — often no limits or fees"
  }
};

document.getElementById('hotel-select').addEventListener('change', function() {
  const resultDiv = document.getElementById('policy-result');
  const selected = this.value;
  
  if (!selected) {
    resultDiv.style.display = 'none';
    return;
  }
  
  const policy = policies[selected];
  
  resultDiv.innerHTML = `
    <h3 style="margin-top: 0; color: #2d5a47;">${policy.name}</h3>
    <p><strong>Weight Limit:</strong> ${policy.weight}</p>
    <p><strong>Pet Fee:</strong> ${policy.fee}</p>
    <p><strong>Notes:</strong> ${policy.notes}</p>
    <p><strong>💡 Tip:</strong> ${policy.tip}</p>
    <p style="font-size: 1.1rem; font-weight: 600; margin-bottom: 0;">${policy.verdict}</p>
  `;
  resultDiv.style.display = 'block';
});
</script>

---

## The Bottom Line

Weight limits are frustrating, but there are great options for dogs of all sizes. For large dogs, **Kimpton**, **Red Roof Inn**, **Motel 6**, and **Loews** are your best bets.

**Want the full breakdown?** Check out my complete guide: [Traveling with a Large Dog: Hotel Policies You Need to Know](/posts/traveling-with-large-dogs-hotel-policies/)

**Ready to book for free?** See [Best Credit Cards for Dog Travelers](/posts/best-credit-cards-pet-travelers/) to start earning points.