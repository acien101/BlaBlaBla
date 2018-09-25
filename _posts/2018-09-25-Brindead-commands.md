---
layout: post
published: true
title: Comandos UNIX para partir la pana
---

Algunos comandos que debería de saberme:

---

#### Recursively change permission to folders

To recursively give directories read&execute privileges:

```
find /path/to/base/dir -type d -exec chmod 755 {} +
```

To recursively give files read privileges:

```
find /path/to/base/dir -type f -exec chmod 644 {} +
```
