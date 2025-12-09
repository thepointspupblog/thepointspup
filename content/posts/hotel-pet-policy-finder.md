---
title: "Hotel Pet Policy Finder: Weight Limits, Fees & Rules by Chain"
description: "Instantly check pet weight limits, fees, and policies for major hotel chains — especially helpful for large dog owners."
date: 2025-12-08
categories:
  - Tools
tags:
  - Hotels
  - Large Dogs
---

Not sure if your dog is welcome? Use this tool to quickly check pet policies for major hotel chains.

<div id="pet-policy-finder">
  <label for="hotel-select"><strong>Select a hotel chain:</strong></label>
  <select id="hotel-select">
    <option value="">-- Choose a chain --</option>
    <option value="hilton">Hilton</option>
    <option value="marriott">Marriott</option>
    <option value="ihg">IHG (Holiday Inn, Kimpton, etc.)</option>
    <option value="hyatt">Hyatt</option>
    <option value="wyndham">Wyndham (La Quinta, etc.)</option>
    <option value="bestwestern">Best Western</option>
    <option value="choice">Choice (Comfort Inn, Quality Inn, etc.)</option>
    <option value="motel6">Motel 6 / Studio 6</option>
    <option value="redroof">Red Roof Inn</option>
    <option value="drury">Drury Hotels</option>
    <option value="loews">Loews Hotels</option>
    <option value="kimpton">Kimpton Hotels</option>
  </select>

  <div id="policy-result" style="display: none; margin-top: 1.5rem; padding: 1.5rem; background: #f9f6f1; border-radius: 12px; border: 2px solid #2d5a47;">
  </div>
</div>

<script>
const policies = {
  hilton: {
    name: "Hilton",
    weight: "Varies by property (typically 50-75 lbs)",
    fee: "$50-$100 per stay (varies by brand)",
    notes: "Most Hilton brands allow dogs. Home2 Suites, Homewood Suites, and Hilton Garden Inn tend to be most pet-friendly. Always call ahead to confirm.",
    tip: "Use Hilton points to book free nights — you'll still pay the pet fee, but the room is free!",
    verdict: "🟡 Good for most dogs under 75 lbs"
  },
  marriott: {
    name: "Marriott",
    weight: "Varies widely (25-75 lbs depending on brand)",
    fee: "$75-$150 per stay",
    notes: "Policies vary significantly by brand and location. Residence Inn and TownePlace Suites tend to be more pet-friendly. Some luxury brands don't allow pets.",
    tip: "Always call the specific property before booking.",
    verdict: "🟡 Hit or miss — call ahead"
  },
  ihg: {
    name: "IHG (Holiday Inn, Kimpton, etc.)",
    weight: "Varies by brand (Kimpton has NO weight limit)",
    fee: "$0-$100 depending on brand",
    notes: "Kimpton is the standout — no weight limits, no breed restrictions, no pet fees. Other IHG brands like Holiday Inn and Candlewood Suites typically cap at 50-80 lbs.",
    tip: "Book Kimpton if you have a large dog — they're the most pet-friendly hotel brand in the industry.",
    verdict: "🟢 Kimpton is excellent, others vary"
  },
  hyatt: {
    name: "Hyatt",
    weight: "Varies (typically 50 lbs, some no limit)",
    fee: "$75-$150 per stay",
    notes: "Policies vary by property. Hyatt Place and Hyatt House tend to be more pet-friendly. Some allow up to 2 pets.",
    tip: "Check the specific property's policy before booking.",
    verdict: "🟡 Moderate — check specific property"
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
    notes: "The gold standard for pet travel. If your dog fits through the door, they're welcome. No breed restrictions. Many have a Director of Pet Relations (a very good dog). Nightly wine hour often welcomes pups.",
    tip: "Best hotel chain for large dogs, period. <a href='/posts/kimpton-points-guide/'>Learn how to book free with points.</a>",
    verdict: "🟢 Best in class — no limits, no fees"
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

**Ready to book for free?** See [Best Credit Cards for Pet Travelers](/posts/best-credit-cards-pet-travelers/) to start earning points.