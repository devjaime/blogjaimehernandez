---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
content: {{ replace .Content "<!--adsense-->" (partial "adsense-inarticle.html" .) | safeHTML }}
---

