---
layout: page
tagline: A few more words about this theme
permalink: /contact
ref: contact
order: 0
form: true
background: /assets/images/contact.jpg
action: https://formspree.io/xyynbarr
img_credits:
  name: Melinda Gimpel
  url: https://unsplash.com/@melindagimpel
  website: Unsplash
---

<p>If you want to get in touch, please send me your details below and I will get back to you as soon as possible!</p>
<form name="sentMessage" id="contactForm" action="https://formspree.io/mdowpvqb" novalidate>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Name</label>
      <input type="text" class="form-control" placeholder="Name" id="name" required data-validation-required-message="Please enter your name.">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Email Address</label>
      <input type="email" class="form-control" placeholder="Email Address" id="email" required data-validation-required-message="Please enter your email address.">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Message</label>
      <textarea rows="5" class="form-control" placeholder="Message" id="message" required data-validation-required-message="Please enter a message."></textarea>
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <br>
  <div id="success"></div>
  <div class="form-group">
    <button type="submit" class="btn btn-primary">Send</button>
  </div>
</form>
