---
title: "Free Guide: How to Book Free Hotel Stays with Your Dog"
description: "Download my step-by-step guide to earning hotel points and traveling free with your pup."
layout: "page"
---

<style>
.guide-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.guide-hero {
  text-align: center;
  margin-bottom: 2rem;
}

.guide-hero h1 {
  font-size: 1.8rem;
  color: #2d5a47;
  margin-bottom: 0.5rem;
  line-height: 1.3;
}

.guide-subtitle {
  font-size: 1.1rem;
  color: #7d7167;
  margin-bottom: 1.5rem;
}

.guide-preview {
  background: #faf8f5;
  border-radius: 16px;
  padding: 1.5rem;
  margin-bottom: 2rem;
  border: 2px solid #e8e0d5;
}

.guide-preview h3 {
  color: #2d3a35;
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1.1rem;
}

.guide-preview ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.guide-preview li {
  padding: 0.5rem 0;
  padding-left: 1.5rem;
  position: relative;
  color: #4a5148;
}

.guide-preview li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: #2d5a47;
  font-weight: bold;
}

.signup-section {
  background: #2d5a47;
  border-radius: 16px;
  padding: 2rem;
  text-align: center;
  margin-bottom: 2rem;
}

.signup-section h3 {
  color: #ffffff;
  margin-top: 0;
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.signup-section > p {
  color: #c4d4c9;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
}

.signup-form {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  max-width: 400px;
  margin: 0 auto;
}

.signup-form input[type="email"] {
  width: 100%;
  padding: 14px 16px;
  border: 2px solid rgba(255,255,255,0.3);
  border-radius: 8px;
  font-size: 1rem;
  background: #ffffff;
  transition: border-color 0.2s;
  box-sizing: border-box;
}

.signup-form input[type="email"]:focus {
  outline: none;
  border-color: #ffffff;
}

.signup-form input[type="email"]::placeholder {
  color: #9a928a;
}

.signup-form button {
  width: 100%;
  padding: 14px 24px;
  background: #ffffff;
  border: none;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 700;
  color: #2d5a47;
  cursor: pointer;
  transition: all 0.2s;
}

.signup-form button:hover {
  background: #f0ebe3;
  transform: translateY(-2px);
}

.privacy-note {
  font-size: 0.85rem;
  color: rgba(255,255,255,0.7);
  margin-top: 1rem;
}

.privacy-note a {
  color: rgba(255,255,255,0.9);
}

/* Download section - hidden by default */
.download-section {
  display: none;
  background: #eef5f1;
  border-radius: 16px;
  padding: 2rem;
  text-align: center;
  margin-bottom: 2rem;
  border: 2px solid #2d5a47;
}

.download-section.visible {
  display: block;
}

.download-section h3 {
  color: #2d5a47;
  margin-top: 0;
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.download-section p {
  color: #4a5148;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
}

.download-btn {
  display: inline-block;
  padding: 16px 32px;
  background: #2d5a47;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 700;
  color: #ffffff !important;
  text-decoration: none;
  transition: all 0.2s;
}

.download-btn:hover {
  background: #245040;
  transform: translateY(-2px);
}

.success-check {
  font-size: 3rem;
  margin-bottom: 1rem;
}
</style>

<div class="guide-container">

<div class="guide-hero">
  <p style="font-size: 3rem; margin-bottom: 0.5rem;">🐾</p>
  <h1>How to Book Free Hotel Stays with Your Dog</h1>
  <p class="guide-subtitle">My step-by-step guide to earning points and traveling free with your pup.</p>
</div>

<div class="guide-preview">
  <h3>What's Inside:</h3>
  <ul>
    <li>Which hotel chains actually welcome dogs (and which to avoid)</li>
    <li>The exact credit cards I use — Hilton, IHG, and Marriott compared</li>
    <li>How to earn 100,000+ points per year from everyday spending</li>
    <li>Smart booking tricks to stretch your points further</li>
    <li>How to handle pet fees when the room is free</li>
    <li>Quick reference chart: best hotels by dog size</li>
  </ul>
</div>

<!-- Signup Form -->
<div class="signup-section" id="signup-section">
  <h3>📧 Get the Free Guide</h3>
  <p>Enter your email and I'll send you the download link instantly.</p>
  
  <form class="signup-form" id="guide-form">
    <input type="email" id="email-input" placeholder="you@example.com" required />
    <button type="submit">Send Me the Guide →</button>
  </form>
  
  <p class="privacy-note">No spam, ever. Unsubscribe anytime.</p>
</div>

<!-- Download Section - Shows after signup -->
<div class="download-section" id="download-section">
  <div class="success-check">✅</div>
  <h3>You're In!</h3>
  <p>Thanks for signing up! Click below to download your guide.</p>
  <a href="/free-hotel-stays-guide.pdf" class="download-btn" download>Download PDF →</a>
</div>

</div>

<script>
document.getElementById('guide-form').addEventListener('submit', function(e) {
  e.preventDefault();
  
  const email = document.getElementById('email-input').value;
  const signupSection = document.getElementById('signup-section');
  const downloadSection = document.getElementById('download-section');
  
  // Submit to Buttondown
  fetch('https://buttondown.com/api/emails/embed-subscribe/thepointspup', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/x-www-form-urlencoded',
    },
    body: 'email=' + encodeURIComponent(email)
  })
  .then(response => {
    // Hide signup, show download
    signupSection.style.display = 'none';
    downloadSection.classList.add('visible');
    
    // Scroll to download section
    downloadSection.scrollIntoView({ behavior: 'smooth' });
  })
  .catch(error => {
    // Even if there's an error, show download (don't punish user)
    signupSection.style.display = 'none';
    downloadSection.classList.add('visible');
  });
});
</script>
