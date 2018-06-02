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

```css
$primaryColor: #f00;
```

###Nesting

সিএসএস লেখা এই স্টেটমেন্টগুলো নেস্টিং করে খুব সহজেই লেখা সম্ভব

```css
a { font-family: sans-serif; color: $primaryColor; }
a:hover, a:focus, a:visited  { color: blue; }
a.link-class { color: green; }
a.link-class:hover,
a.link-class:focus,
a.link-class:visited { color: black; }
```

নেস্টিং উদাহরণ:

```scss
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

## Video 3

### Operations and Functions

```css
$container: 1170px;
$padding: 25px;

.half {
   height: halfHeight(2, 2);
}
.half1 {
   height: halfHeight(2, 3);
}
.half2 {
   height: halfHeight(2, 2);
}
```

ফাংশন ডিক্লেয়ার করতে হলে **@function** কিওয়ার্ড লিখে ফাংশনের নাম লিখতে হয়। ফাংশন **প্যারামিটার** গ্রহণ করে।

```scss
@function halfHeight( $first, $second ) {
   @return $container / $first + $padding / $second;
}
```

## Video 4

### @mixin

একই সিএসএস ডিক্লারেশন একাধিক স্থানে ব্যবহৃত হলে, সেই কোডগুলোকে একটি নাম দিয়ে @mixin গ্রুপ তৈরী করে রাখা হয়। তারপর যেখানে যেখানে প্রয়োজন সেখানে সেখানে ব্যবহার করা যায়।

@mixin এর সাথে function এর মত **প্যারামিটার** পাস করানো যায়। প্যারামিটারের ডিফল্ট ভ্যালু দেওয়ার জন্য ভেরিয়েবলের সাথে কোলন চিহ্ন দিয়ে ভ্যালু ফিক্স করে দিতে হবে।

```css
@mixin translateX( $val: 15px ) {
	-webkit-transform: translateX( $val );
	-moz-transform: translateX( $val );
	-ms-transform: translateX( $val );
	-o-transform: translateX( $val );
	transform: translateX( $val );
}

.translateX {
	@include translateX( 15px );
}
.myTransform {
	@include translateX( 10px );
}
```

## Video 5

### @import and Partials

বড় স্টাইল ফাইলকে মাল্টিপল ফাইলে স্প্লিট করার পর মূল ফাইল থেকে অন্য ফাইলকে কল করতে @import ব্যবহার করা হয়। অন্য ফাইলের নাম reset.css হলে ইমপোর্ট করার সময় **এক্সটেনশন ছাড়া শুধু ফাইলের নাম** লিখতে হবে।

@import 'partials/reset';
@import 'partials/mixins';

Partials এ মাল্টিপল স্প্লিট ফাইলের নামের শুরুতে "_" (underscore) ব্যবহার করা হয়। কিন্তু, ইমপোর্ট করার সময় **আন্ডারস্কোর লিখতে হয় না**।

কনভেনশনালি স্প্লিট ফাইলগুলো partials নামের ফোল্ডারে রাখা হয়। ইমপোর্ট করার সময়, ফোল্ডারের নাম প্যারামিটার আকারে পাস করা হয়।

## Video 6

কাজের সুবিধার জন্য scss ফাইলগুলোকে scss ফোল্ডারে রাখা উচিত।

কম্পাইল্ড css ফাইলগুলোর জন্য css ফোল্ডার বানানো উচিত।

scss ফোল্ডারের ভিতরে যতগুলো সাবফোল্ডারের মধ্যে scss ফাইল থাকুক না কেন, তার ভিতরে কোন সিএসএস পরিবর্তন করলেও watch ট্রিগার করবে।

Alecaddd তার SASS টিউটোরিয়ালে Ruby'র SASS ব্যবহার করেছেন।

## Video 7


এই ভিডিওতে scss কে কম্পাইল করার সময় SASS এর cli compiler এর মাধ্যমে সিএসএস কে ৪টি ভিন্ন ভিন্নভাবে ফরম্যাট করা যায়।

ডিফল্ট = নেসটেড
কম্পাক্ট
কম্প্রেসড = প্রোডাকশন রেডি সাইট এর জন্য
এক্সপানডেড = কোন কম্প্রেশন নাই। ব্যাকরণসম্মত সিএসএস লেখার স্টাইল

## Video 8 LOOP

### How loop works in SAS

**FOR LOOP**

```scss
@for $space from 1 through 12
{
	.padding-top-#{$space}
	{
		padding-top: 10px * $space;
	}
}
```

**WHILE LOOP**

```scss
$num =6;
@while $num > 0
{
	$width: percentage( 1 / $space );

	.column-#{$num}
	{
		width: $width;
	}

	$num: $num + 1;
}
```

## VIDEO 9

### EACH LOOP

```scss
$white: #fff;
$black: #000;
$red: $f00;
$primary: #ccc;
$secondary: #333;

$colors: (
	'white': $white,
	'black': $black,
	'red': $red,
	'primary': $primary,
	'secondary': $secondary
);

@each $color, $hex in $colors
{
	.text-#{$color}
	{
		color: #hex;
	}

	.background-#{$color}
	{
		color: #hex;
	}
}
```
