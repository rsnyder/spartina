---
# the default layout is 'page'
title: Contact
icon: fas fa-envelope
layout: page
order: 8
published: true
permalink: /contact
---

<style>
    .contact-form {
      max-width: 500px;
      margin: 2rem auto;
      padding: 1.5rem;
      background: #fdfdfd;
      border: 1px solid #e0e0e0;
      border-radius: 12px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.05);
      font-family: system-ui, sans-serif;
    }

    .contact-form label {
      display: block;
      margin-bottom: 0.3rem;
      font-weight: 600;
      color: #333;
    }

    .contact-form input,
    .contact-form textarea {
      width: 100%;
      padding: 0.7rem;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
      box-sizing: border-box;
    }

    .contact-form input:focus,
    .contact-form textarea:focus {
      outline: none;
      border-color: #3aa0a0; /* coastal teal accent */
      box-shadow: 0 0 0 3px rgba(58,160,160,0.2);
    }

    .contact-form button {
      display: inline-block;
      background: #3aa0a0; /* coastal teal accent */
      color: white;
      font-size: 1rem;
      font-weight: 600;
      padding: 0.8rem 1.5rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.2s ease-in-out;
    }

    .contact-form button:hover {
      background: #317c7c;
    }

    .hidden-field {
      position: absolute;
      left: -5000px;
  }
</style>

Contact me at [contact@spartina.io](mailto:contact@spartina.io) or use the form below.

<form class="contact-form" action="https://spartina-contact-endpoint.netlify.app/.netlify/functions/contact" method="POST">
  <label for="name">Name</label>
  <input id="name" type="text" name="name" autocomplete="name" required>
  <label for="email">Email</label>
  <input id="email" type="email" name="email" autocomplete="email" required>
  <label for="message">Message</label>
  <textarea id="message" name="message" rows="6" required></textarea>
  <input type="hidden" name="subject" value="Spartina Contact">

  <!-- Honeypot: bots fill it, humans never see it. The name must stay something
       browser autofill does not recognise (never "company"/"organization"). -->
  <div class="hidden-field" aria-hidden="true"><input type="text" name="spartina_hp" tabindex="-1" autocomplete="off"></div>

  <button type="submit">Send</button>

</form>