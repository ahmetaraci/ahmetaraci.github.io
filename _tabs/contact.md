---
icon: fas fa-address-book
order: 4
layout: page
title: Contact Me
permalink: /contact/
---

Hello! You can reach out to me using the following methods.

### Contact Information

- **Email**: [muhammetahmet.araci@gmail.com](mailto:muhammetahmet.araci@gmail.com)
- **Microsoft Teams**: [muhammetahmet.araci@outlook.com](mailto:muhammetahmet.araci@outlook.com)

### Social Media

- **LinkedIn**: [linkedin.com/in/ahmet-araci/](https://www.linkedin.com/in/ahmet-araci/)
- **GitHub**: [github.com/ahmetaraci](https://github.com/ahmetaraci)

### Contact Form

If you'd like to reach me directly through a form, please fill out the form below:

{% if site.recaptcha.enabled %}

<script src="https://www.google.com/recaptcha/api.js?render={{ site.recaptcha.site_key }}"></script>
<script>
  function onSubmit(token) {
    document.getElementById("contact-form").submit();
  }

  function executeRecaptcha(e) {
    e.preventDefault();
    grecaptcha.ready(function() {
      grecaptcha.execute('{{ site.recaptcha.site_key }}', {action: 'submit'}).then(function(token) {
        onSubmit(token);
      });
    });
  }

  document.addEventListener('DOMContentLoaded', function() {
    document.getElementById('contact-form').addEventListener('submit', executeRecaptcha);
  });
</script>

{% endif %}

<form id="contact-form" action="https://formspree.io/f/movaaadz" method="POST" style="background: white; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); width: 100%; max-width: 400px; box-sizing: border-box;">
  <label style="display: block; margin-bottom: 10px; font-weight: bold;">
    Your email:
    <input type="email" name="email" required style="width: 100%; padding: 10px; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; font-size: 16px;">
  </label>
  <label style="display: block; margin-bottom: 10px; font-weight: bold;">
    Your message:
    <textarea name="message" rows="5" required style="width: 100%; padding: 10px; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; font-size: 16px;"></textarea>
  </label>
  {% if site.recaptcha.enabled %}
  <button type="submit" class="g-recaptcha" 
          data-sitekey="{{ site.recaptcha.site_key }}" 
          data-callback='onSubmit' 
          data-action='submit' 
          style="display: block; width: 100%; padding: 10px; background-color: #007BFF; color: white; border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">
    Send
  </button>
  {% else %}
  <button type="submit" 
          style="display: block; width: 100%; padding: 10px; background-color: #007BFF; color: white; border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">
    Send
  </button>
  {% endif %}
</form>
