---
title: "Contact Me"
date: 2025-03-02
description: "Reach out to me!"
layout: "index"
draft: false
showAuthor: false

---

Contact Details

<form id="contact-form" action="https://formspree.io/f/xvgveqzd" method="POST" novalidate>
  <label for="contact-email">
    Your email
    <input id="contact-email" type="email" name="email" required autocomplete="email" />
  </label>

  <label for="contact-message">
    Your message
    <textarea id="contact-message" name="message" rows="6" required></textarea>
  </label>

  <!-- Honeypot to catch bots -->
  <div style="position:absolute;left:-10000px;top:auto;overflow:hidden;">
    <label>Leave this field empty
      <input name="_gotcha" tabindex="-1" autocomplete="off" />
    </label>
  </div>

  <input type="hidden" name="_subject" value="New contact form submission" />
  <input type="hidden" name="_next" value="/contact/thanks/" />

  <button type="submit">Send</button>
</form>

<div id="form-status" role="status" aria-live="polite"></div>

<script>
  (function () {
    const form = document.getElementById('contact-form');
    const status = document.getElementById('form-status');

    form.addEventListener('submit', function (e) {
      e.preventDefault();

      // HTML5 validation
      if (!form.checkValidity()) {
        form.reportValidity();
        return;
      }

      const data = new FormData(form);

      fetch(form.action, {
        method: form.method,
        body: data,
        headers: { 'Accept': 'application/json' }
      })
        .then(response => {
          if (response.ok) {
            status.textContent = 'Thanks — your message has been sent!';
            form.reset();
          } else {
            return response.json().then(data => {
              status.textContent = data && data.error ? data.error : 'Oops — there was a problem submitting the form.';
            });
          }
        })
        .catch(() => {
          status.textContent = 'Network error. Please try again later.';
        });
    });
  })();
</script>




