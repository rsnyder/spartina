---
# the default layout is 'page'
title: Services
icon: fa-solid fa-screwdriver-wrench
layout: default
order: 7
published: true
permalink: /services/
toc: true
---

<style>
  header {
    /* display: none; */
  }
  .contact-wrap {
    max-width: 760px;
    margin: 2.5rem auto;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  }

  .contact-intro {
    text-align: center;
    margin-bottom: 1.75rem;
  }

  .contact-intro h4 {
    margin-bottom: 0.5rem;
    font-size: 1.75rem;
    line-height: 1.2;
    color: #1f3f3f;
  }

  .contact-intro p {
    max-width: 600px;
    margin: 0.4rem auto;
    color: #555;
    font-size: 1.05rem;
    line-height: 1.55;
  }

  .contact-card {
    display: grid;
    grid-template-columns: 1fr 1.4fr;
    gap: 0;
    background: #ffffff;
    border: 1px solid #dfe8e8;
    border-radius: 18px;
    box-shadow: 0 12px 30px rgba(31, 63, 63, 0.10);
    overflow: hidden;
  }

  .contact-side {
    background: linear-gradient(145deg, #2f8f8f, #1f5f5f);
    color: white;
    padding: 2rem;
  }

  .contact-side h4 {
    margin-top: 0;
    margin-bottom: 0.75rem;
    font-size: 1.25rem;
    color: rgba(255, 255, 255, 1);
    font-weight: bold;
  }

  .contact-side p {
    margin: 0 0 1rem;
    line-height: 1.55;
    color: rgba(255, 255, 255, 0.92);
  }

  .contact-side a {
    color: white;
    font-weight: 700;
    text-decoration: underline;
    text-underline-offset: 3px;
  }

  .contact-note {
    margin-top: 1.5rem;
    padding-top: 1.25rem;
    border-top: 1px solid rgba(255, 255, 255, 0.28);
    font-size: 0.95rem;
  }

  .contact-form {
    padding: 2rem;
    background: #fbfdfd;
  }

  .form-row {
    margin-bottom: 1.15rem;
  }

  .contact-form label {
    display: block;
    margin-bottom: 0.4rem;
    font-weight: 700;
    color: #233;
    font-size: 0.95rem;
  }

  .contact-form input,
  .contact-form textarea {
    width: 100%;
    padding: 0.8rem 0.9rem;
    border: 1px solid #cfdada;
    border-radius: 10px;
    font-size: 1rem;
    box-sizing: border-box;
    background: white;
  }

  .contact-form textarea {
    resize: vertical;
    min-height: 150px;
  }

  .contact-form input:focus,
  .contact-form textarea:focus {
    outline: none;
    border-color: #3aa0a0;
    box-shadow: 0 0 0 4px rgba(58, 160, 160, 0.18);
  }

  .contact-form button {
    width: 100%;
    background: #2f8f8f;
    color: white;
    font-size: 1.05rem;
    font-weight: 700;
    padding: 0.9rem 1.4rem;
    border: none;
    border-radius: 999px;
    cursor: pointer;
    transition: background 0.2s ease, transform 0.1s ease, box-shadow 0.2s ease;
    box-shadow: 0 6px 14px rgba(47, 143, 143, 0.24);
  }

  .contact-form button:hover {
    background: #267575;
    transform: translateY(-1px);
    box-shadow: 0 8px 18px rgba(47, 143, 143, 0.30);
  }

  .contact-form button:active {
    transform: translateY(0);
  }

.form-help {
    margin-top: 0.85rem;
    color: #667;
    font-size: 0.9rem !important;
    line-height: 1.45;
    text-align: center;
  }

  .hidden-field {
    position: absolute;
    left: -5000px;
  }

  @media (max-width: 720px) {
    .contact-wrap {
      margin: 1.5rem auto;
    }

    .contact-card {
      grid-template-columns: 1fr;
    }

    .contact-side,
    .contact-form {
      padding: 1.5rem;
    }

    .contact-intro {
      text-align: left;
    }

    .contact-intro h2 {
      font-size: 1.5rem;
    }
  }

</style>

## Spartina Techical Services

Spartina Technical Services offers friendly, practical technology help for residents of Sun City Hilton Head. The focus is on useful, right-sized support: getting devices working, solving everyday technical problems, preserving important photos and documents, and helping people make better use of today’s digital tools.

Services are intentionally small-scale and personal. This is not a large repair shop or a managed IT company. It is local, hands-on help from someone with a long background in technology and an interest in making modern tools more approachable.

Typical services include Mac setup and troubleshooting, basic home networking and peripheral setup, photo scanning and digital archiving, simple website creation, and one-on-one help with AI tools such as ChatGPT. The goal is to explain things clearly, avoid unnecessary complexity, and leave you with a setup or solution you can actually use.

<div class="post-index flex-grow-1 px-xl-1 view-list">
  {% for post in site.services %}
    {% include post_index_item.html post=post %}
  {% endfor %}
</div>

###
{: .contact-wrap }

### How can I help?
{: .contact-intro}

Have a question about Mac help, home technology, photo scanning, digital archiving, websites, or AI tutoring? Send a note and I’ll get back to you.

###
{: .contact-card}

#### Spartina Technical Services
{: .contact-side}

Friendly, practical technology help for Sun City Hilton Head residents.

You can also email me directly at [contact@spartina.io](mailto:contact@spartina.io)

For the most useful reply, briefly describe what you need help with and the device, service, or project involved.
{: .contact-note}

#### 

<form class="contact-form" action="https://spartina-contact-endpoint.netlify.app/.netlify/functions/contact" method="POST">
    <div class="form-row">
    <label for="name">Name</label>
    <input id="name" type="text" name="name" autocomplete="name" required>
    </div>

    <div class="form-row">
    <label for="email">Email</label>
    <input id="email" type="email" name="email" autocomplete="email" required>
    </div>

    <div class="form-row">
    <label for="message">Message</label>
    <textarea id="message" name="message" rows="6" required></textarea>
    </div>

    <input type="hidden" name="subject" value="Spartina Contact">

    <!-- Honeypot: bots fill it, humans never see it. The name must stay something
         browser autofill does not recognise (never "company"/"organization"). -->
    <div class="hidden-field" aria-hidden="true"><input type="text" name="spartina_hp" tabindex="-1" autocomplete="off"></div>

    <button type="submit">Send message</button>

    <p class="form-help">
    I’ll use your email only to respond to your request.
    </p>
</form>