---
# the default layout is 'page'
title: Services
icon: fa-solid fa-screwdriver-wrench
layout: page
order: 7
published: true
permalink: /services
---

Contact me at [contact@spartina.io](mailto:contact@spartina.io) or use the form below.

<form class="contact-form" action="https://spartina-contact-endpoint.netlify.app/.netlify/functions/contact" method="POST">
  <label for="name">Name</label>
  <input id="name" type="text" name="name" autocomplete="name" required>
  <label for="email">Email</label>
  <input id="email" type="email" name="email" autocomplete="email" required>
  <label for="message">Message</label>
  <textarea id="message" name="message" rows="6" required></textarea>
  <input type="hidden" name="subject" value="Spartina Technical Services">

  <!-- Honeypot field: hide with CSS if preferred -->

  <input class="hidden-field" type="text" name="company" tabindex="-1" autocomplete="off">  <button type="submit">Send</button>

</form>