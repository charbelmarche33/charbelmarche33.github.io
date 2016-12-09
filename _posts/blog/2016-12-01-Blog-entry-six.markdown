---
layout: post
title:  "Found a Quick Way to Allow People to Contact Me Via Email on My Site"
date:   2016-12-01 12:34:11
categories: blog
---

Hi guys, I was just searching sharing that a very simple way to allow people to contact you is by using this simple code and FormSpree (no this is not an ad). All you have to do is add this piece of code to where you want your form to be:

```
<form method="POST" action="http://formspree.io/cmarche@mail.umw.edu">
  <input name="email" placeholder="Your email" type="email">
  <textarea name="message" placeholder="Your message"></textarea>
  <button type="submit">Send</button>
</form>
```

Just replace my email with whatever email you use. Then you have to confirm the email address for security reasons, and bam you have a perfectly functional contact me form set up!