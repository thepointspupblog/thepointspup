---
title: "Leave Your Pawprint"
---

## Share Your Pet Travel Story 🐾

Booked a free stay? Found the perfect dog-friendly hotel? Had an epic road trip with your pup? We'd love to hear about it — and maybe feature your story on the site.

---

### What counts as a pawprint?

- Booked a free hotel stay using points
- Got upgraded to a suite with your pup
- Found an amazing pet-friendly property
- Had an epic road trip with your dog
- Discovered a hidden gem destination

---

### Tell Us Your Story

<form id="pawprint-form" style="max-width: 500px;">
<p><label><strong>Your Name</strong></label><br><input type="text" name="name" placeholder="First name is fine!" required style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"></p>
<p><label><strong>Your Dog's Name</strong></label><br><input type="text" name="dog_name" placeholder="The real star ⭐" required style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"></p>
<p><label><strong>Email</strong></label><br><input type="email" name="email" placeholder="you@example.com" required style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"><br><small style="color: #888;">Only used to follow up — never shared</small></p>
<p><label><strong>Where'd You Go?</strong></label><br><input type="text" name="destination" placeholder="e.g., Panama City Beach, FL" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"></p>
<p><label><strong>Hotel/Chain</strong></label><br><input type="text" name="hotel" placeholder="e.g., Embassy Suites" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"></p>
<p><label><strong>Points/Card Used</strong></label><br><input type="text" name="card" placeholder="e.g., Hilton Surpass" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"></p>
<p><label><strong>Estimated Savings</strong></label><br><select name="savings" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"><option value="">Select...</option><option value="Under $100">Under $100</option><option value="$100-250">$100 - $250</option><option value="$250-500">$250 - $500</option><option value="$500-1000">$500 - $1,000</option><option value="$1000+">$1,000+</option><option value="Not sure">Not sure</option></select></p>
<p><label><strong>Your Story</strong></label><br><textarea name="story" rows="5" placeholder="Tell us about your trip! Where did you go? How did you book it? What was the best part?" required style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"></textarea><br><small style="color: #888;">2-3 sentences is perfect. We may edit for length.</small></p>
<p><label><strong>Photo Link (optional)</strong></label><br><input type="url" name="photo" placeholder="Link to a photo of your pup on the trip" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; margin-top: 4px;"><br><small style="color: #888;">Upload to Imgur or Google Photos and paste the link</small></p>
<p><label><input type="checkbox" name="permission" required> I give permission to feature my story on ThePointsPup</label></p>
<p><button type="submit" style="background: #2d5a47; color: white; padding: 12px 24px; border: none; border-radius: 6px; font-size: 16px; font-weight: 600; cursor: pointer;">Leave My Pawprint 🐾</button></p>
</form>

<div id="success-message" style="display: none; background: #eef5f1; border-radius: 12px; padding: 24px; margin: 20px 0; border: 2px solid #2d5a47; text-align: center;">

**🐾 Pawprint Received!**

Thanks for sharing your story. If we feature it, we'll send you an email!

[See all Pawprints →](/page/pawprints/)

</div>

<script>
document.getElementById('pawprint-form').addEventListener('submit', function(e) {
  e.preventDefault();
  var form = e.target;
  var formData = new FormData(form);
  fetch('https://formspree.io/f/mdkqwobv', {
    method: 'POST',
    body: formData,
    headers: { 'Accept': 'application/json' }
  }).then(function(response) {
    if (response.ok) {
      form.style.display = 'none';
      document.getElementById('success-message').style.display = 'block';
    }
  }).catch(function(error) {
    form.style.display = 'none';
    document.getElementById('success-message').style.display = 'block';
  });
});
</script>

---

*We'll email you if we feature your story!*
