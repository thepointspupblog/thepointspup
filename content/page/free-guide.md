---
title: "Free Guide"
---

## How to Book Free Hotel Stays with Your Dog 🐾

My step-by-step guide to earning points and traveling free with your pup.

---

<div style="background: #faf8f5; border-radius: 12px; padding: 20px; margin: 20px 0; border: 1px solid #e8e0d5;">

**What's Inside:**

- Which hotel chains actually welcome dogs (and which to avoid)
- The exact credit cards I use — Hilton, IHG, and Marriott compared
- How to earn 100,000+ points per year from everyday spending
- Smart booking tricks to stretch your points further
- How to handle pet fees when the room is free
- Quick reference chart: best hotels by dog size

</div>

<div style="background: #2d5a47; border-radius: 12px; padding: 24px; margin: 20px 0; color: white;">

**📧 Get the Free Guide**

Enter your email and I'll send you the download link instantly.

<form id="guide-form" style="margin-top: 16px;">
<input type="email" id="email-input" placeholder="you@example.com" required style="width: 100%; max-width: 350px; padding: 12px; border: none; border-radius: 6px; font-size: 16px;">
<br><br>
<button type="submit" style="background: white; color: #2d5a47; padding: 12px 24px; border: none; border-radius: 6px; font-size: 16px; font-weight: 600; cursor: pointer;">Send Me the Guide →</button>
</form>

<small style="opacity: 0.8;">No spam, ever. Unsubscribe anytime.</small>

</div>

<div id="download-section" style="display: none; background: #eef5f1; border-radius: 12px; padding: 24px; margin: 20px 0; border: 2px solid #2d5a47; text-align: center;">

**✅ You're In!**

Thanks for signing up! Click below to download your guide.

<br>

<a href="/free-hotel-stays-guide.pdf" download style="display: inline-block; background: #2d5a47; color: white; padding: 12px 24px; border-radius: 6px; text-decoration: none; font-weight: 600;">Download PDF →</a>

</div>

<script>
document.getElementById('guide-form').addEventListener('submit', function(e) {
  e.preventDefault();
  var email = document.getElementById('email-input').value;
  fetch('https://buttondown.com/api/emails/embed-subscribe/thepointspup', {
    method: 'POST',
    headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
    body: 'email=' + encodeURIComponent(email)
  }).then(function() {
    document.querySelector('[style*="background: #2d5a47"]').style.display = 'none';
    document.getElementById('download-section').style.display = 'block';
  }).catch(function() {
    document.querySelector('[style*="background: #2d5a47"]').style.display = 'none';
    document.getElementById('download-section').style.display = 'block';
  });
});
</script>
