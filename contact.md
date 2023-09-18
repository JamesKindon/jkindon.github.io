---
layout: page
title: Contact Form
description: Please feel free to contact me via the form below
---

<form method="post" action="https://forms.un-static.com/forms/93cd5c2516df52dfcbcb3d6e1ac7444a1ba4db8e">
  <div class="form-group">
    <label for="Name">Name</label>
    <input type="text" class="form-control" id="Name" placeholder="Please provide your name" required>
  </div>
  <div class="form-group">
    <label for="email">Email address</label>
    <input type="email" class="form-control" id="email" placeholder="name@example.com" required>
  </div>
  <div class="form-group">
    <label for="Message">Message</label>
    <textarea class="form-control" id="Message" rows="3" placeholder="What can I help you with?" required></textarea>
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="SpamBox" required>
    <label class="form-check-label" for="SpamBox">I am not a jerk trying to spam you</label>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>