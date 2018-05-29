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

## Video 2

ভেরিয়েবল ডিক্লেয়ার করার নিয়ম:

```
$primaryColor: #f00;
```

###Nesting

সিএসএস লেখা এই স্টেটমেন্টগুলো নেস্টিং করে খুব সহজেই লেখা সম্ভব

```
a { font-family: sans-serif; color: $primaryColor; }
a:hover, a:focus, a:visited  { color: blue; }
a.link-class { color: green; }
a.link-class:hover,
a.link-class:focus,
a.link-class:visited { color: black; }
```

নেস্টিং উদাহরণ:

```
a { font-family: sans-serif; color: $primaryColor;
   &:hover,
   &:focus,
   &:active { color: blue }

   &.link-class { color: green;
      &:hover,
      &:focus,
      &:visited { color: black; }
   }
}
```
