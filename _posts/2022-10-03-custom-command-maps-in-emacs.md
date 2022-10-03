---
layout: post
title: Custom command maps in Emacs
categories: [Emacs]
---

I've come to really like how `<menu>` in Ergoemacs lets you enter commands as a
sequence of characters without having to use modal editing. I like it so much
that I now set anything up with a command map to use `<menu>` and a relevant
key (e.g. `p` for projectile) as its prefix. In fact, I'll even do it for
things that don't have command maps by making my own. Here's an example for
org-roam. I use use-package, but it should be fairly easy to figure out how to
do it using global- or local-set-key.

```elisp
(use-package org-roam
  :config
  (defvar tfm/org-roam-command-map (let ((map (make-sparse-keymap)))
				     (define-key map (kbd "b") #'org-roam-buffer-toggle)
				     (define-key map (kbd "c") #'org-roam-capture)
				     (define-key map (kbd "d") #'org-roam-buffer-display-dedicated)
				     (define-key map (kbd "f") #'org-roam-node-find)
				     (define-key map (kbd "i") #'org-roam-node-insert)
				     map)
    "Custom command map for use with org-roam.")
  (fset 'tfm/org-roam-command-map tfm/org-roam-command-map)
  ;; other configuration goes here...
  :bind
  (:map ergoemacs-user-keymap ("<menu> r" . tfm/org-roam-command-map)))
```
