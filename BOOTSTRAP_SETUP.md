# Bootstrap static files for Django

Download the latest Bootstrap and place the CSS and JS in your Django static directory.

## Option 1: Use Bootstrap via CDN (recommended for quick setup)

In your Django template (e.g., `base.html`):

```
<!-- Bootstrap CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
<!-- Bootstrap JS -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
```

## Option 2: Serve Bootstrap locally

1. Download Bootstrap from https://getbootstrap.com/
2. Place the `css` and `js` folders inside your Django app's `static` directory (e.g., `static/bootstrap/css`, `static/bootstrap/js`).
3. In your template:

```
{% load static %}
<link href="{% static 'bootstrap/css/bootstrap.min.css' %}" rel="stylesheet">
<script src="{% static 'bootstrap/js/bootstrap.bundle.min.js' %}"></script>
```

---

For most learners, using the CDN is easiest and requires no extra setup.
