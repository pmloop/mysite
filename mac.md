---
layout: page
title: Mac & Stuffs
permalink: /mac/
---

## Mac Usage

### use brew

### ssh without password

```unix
ssh-keygen -q -f ~/.ssh/id_rsa -t rsa
ssh-copy-id <remote>
```
and set up your 

```unix
   ~/.ssh/config
```

### Open terminal here:

```
tell application "Finder" to set Dir to "'" & (POSIX path of (target of front window as text)) & "'"

if application "iTerm" is running then
	tell application "iTerm"
		set win to (create window with default profile)
		set sesh to (current session of win)
		tell sesh to write text "cd " & Dir & ";clear"
	end tell
else
	activate "iTerm"
	tell application "iTerm"
		set win to current window
		set sesh to (current session of win)
		tell sesh to write text "cd " & Dir & ";clear"
	end tell
end if

```

## Vim Usage

* gt to go to
* gT to go back
* :r !date to stamp time

## Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
