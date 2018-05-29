# SASS-Tutorial

This tutorial is gist of what I have learnt from Alecaddd's series video tutorial on SASS.

GitHub Markdown syntax: https://help.github.com/articles/basic-writing-and-formatting-syntax/

## Video 1

###@extend .class-name;

মনে করি, দুইটি ক্লাস .class-one এবং .class-two আছে। .class-one এ যে সব css declaration আছে .class-two তেও হুবহু সেগুলো থাকে, কিন্তু, .class-two তে এক বা একাধিক অন্য কোন প্রোপার্টি ডিক্লারেশন থাকতে পারে। যেমন:

```css
.class-one (
	color: #f00;
	font-family: sans-serif;
	text-decoration: underline;
}
.second-one (
	@extend .class-one;
	border-color: #fff;
}
```
