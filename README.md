# NodeJS And Node Package Manager Crash Course

এই টিউটোরিয়ালটি Twinkle Cats YouTube Channel থেকে নেয়া হয়েছে। মূলতঃ এই টিউটোরিয়ালের সংক্ষিপ্তাসার দিয়ে এই লেখাটি সাজানো হয়েছে। এটি মূলতঃ আমার রেফারেন্স গাইড।

NodeJs হল Javascript এর একটি রানটাইম লাইব্রেরী যেখানে Javascript কে চালানো যায়। Javascript কে ব্রাউজারের বাইরে সার্ভারে বা ডেস্কটপে রান করানোর জন্য NodeJS ব্যবহার করা হয়।

ডাউনলোড করার পর উইন্ডোজে NodeJS ইন্সটল করলে এর মধ্যে Node Package Manager বা NPM ইন্সটল হয়।

পৃথিবীর বিভিন্ন দেশ থেকে জাভাস্ক্রিপ্ট ডেভেলপারগণ অন্য জাভাস্ক্রিপ্ট ডেভেলপারদের জন্য অসংখ্য  Javascript Module তৈরী করে রেখেছেন। npmjs.com ওয়েবসাইটে এই লাইব্রেরী বা module গুলো রাখা হয়েছে। ডেভেলপারগন তাদের প্রজেক্টে প্রয়োজনমত এই জাভাস্ক্রিপ্ট লাইব্রেরীগুলো এ্যাটাচ করে নেন এই NPM টুলকে ব্যবহার করে।

NPM কে Node.js command prompt থেকে ব্যবহার করতে হয়।

কমান্ড প্রম্পটে node -v এবং  npm -v ব্যবহার করে NodeJS এবং NPM এর ভার্সন সম্পর্কে জানা যায়।

কোন প্রজেক্টে NPM ব্যবহার করতে হলে cmd ব্যবহার করে আমার ফোল্ডারে আসব। এবার, কমান্ড প্রম্পটে টাইপ করব

```
npm init
```

npm আমাকে আমার প্রজেক্ট সম্পর্কে কিছু প্রশ্ন ধারাবাহিকভাবে জিজ্ঞাসা করবে। যেমনঃ

```
package name: (testnpm)
version: (1.0.0)
description: NPM Crash Course
entry point: (index.js) app.js
test command:
git repository:
keywords:
author: Manzur Ahmed
license: (ISC)
```

প্রত্যেকটা প্রশ্নের উত্তর লিখে Enter কি চাপ দিলে যে ফোল্ডারের মধ্যে আছি, সেখানে **package.json** নামে একটি ফাইল তৈরী হবে। এই ফাইলটি অনেকটা প্রজেক্টের মেনিফেস্ট ফাইলের মত যেখানে প্রজেক্টের কিছু মেটাডাটা লেখা থাকে।

npm init এর সাথে -y প্যারামিটার ব্যবহার করা হলে, কমান্ড প্রম্পটে কোন প্রশ্ন না করে package.json ফাইল বানিয়ে দিবে।
```
npm init -y
```

এছাড়াও, আমার প্রজেক্টে যে সকল থার্ড পার্টি লাইব্রেরী ব্যবহার করা হবে, যেগুলো NPM দ্বারা যুক্ত করা হলে সেগুলো npmjs.com রিপোজিটরি থেকে ডাউনলোড করে প্রজেক্টের ফোল্ডারের মধ্যে রাখবে এবং ব্যবহৃত মডিউলগুলোর একটি লিস্ট এই package.json ফাইলে মেইনটেইন করবে।

এই ক্র্যাশ প্রজেক্টের জেসন ফাইলে আমরা লিখেছি যে, এর এন্ট্রি পয়েন্ট হচ্ছে, app.js। সুতরাং app.js নামে একটি js ফাইল তৈরী করব।

এখন, মনে করি, আমাদের প্রজেক্টে underscore.js নামের একটি মডিউলকে ব্যবহার করার প্রয়োজন হয়ে পড়ল। আমি underscorejs.org ওয়েবসাইটি গিয়ে দেখতে পারলাম যে, এই মডিউলটি ব্যবহার করতে হলে আমাকে নিচের কমান্ডটি দিতে হবেঃ

```
npm install underscore
```

**বিদ্রঃ** NPM এর আগের ভার্সনগুলোতে কমান্ডের শেষে --save প্যারামিটার ব্যবহার করতে হত। সম্ভবত ভার্সন ৯ এর পর থেকে --save প্যারামিটার ব্যবহার করার প্রয়োজন হয় না। এটি ছাড়াই package.json ফাইলটি আপডেট হয়ে যায়।

এই কমান্ডটি রান করার পর আমার প্রজেক্টের মধ্যে "**node_modules**" নামে একটি ফোল্ডার এবং তার মধ্যে "underscore" নামে আরেকটি ফোল্ডার তৈরী হবে। এই ফোল্ডারের মধ্যে underscore js এর সাথে সংশ্লিষ্ট ফাইলগুলো রেখে দিবে NPM।

এখন এই underscore js কে আমাদের প্রজেক্টে ব্যবহার করব কি ভাবে? এর জন্য app.js ফাইলে underscore কে import করতে হবে।

```
var _ = require("underscore");
```

এবার, টেস্ট করার জন্য আমি একটা এ্যারে বানিয়ে underscore এর কিছু ফাংশন ব্যবহার করব।

```
var _ = require("underscore");

var arr = [3, 4, 2, 6, 4];

_.each( arr, function(elem){
	console.log(elem);
});
```

### Dependency নিয়ে দু'টি কথা

NPM এ ডিপেনডেন্সি দুই প্রকার।

1. Local dependency
2. Global dependency

NPM ইন্সটল করার সময় **--save-dev** প্যারামিটার ব্যবহার করা হলে, যে মডিউলগুলো ডাউনলোড হয়, তা লোকাল ডিপেনডেনসি। এগুলো Development dependency। এই ধরণের ফাইলগুলো প্রজেক্টের কোন হার্ম করে না। যেমনঃ Gulp একটি ডেভেলপমেন্ট ডিপেনডেনসি।

Gulp ইন্সটল করা হলে package.json ফাইলে "devDependencies" নামে একটি নতুন এন্ট্রি যোগ হবে এবং gulp এর সাথে রিলেটেড ৩১৯ টা মডিউল ডাউনলোড হয়ে যাবে।

Globally কোন মডিউল ইন্সটল করতে হলে **-g** প্যারামিটার ব্যবহার করতে হবে। এমন মডিউলগুলো কোন নির্দিষ্ট প্রোজেক্টের জন্য নয়, বরং সব প্রোজেক্টে ব্যবহৃত হয়।

### nodemon

গ্লোবালি ব্যবহৃত মডিউলের মধ্যে একটি মডিউল এখন আমি ইন্সটল করব। এর নাম হল, nodemon। বহুল ব্যবহৃত এই মডিউলটি ইন্সটল করতে হলে, যে কমান্ড দিতে হবে, তা নিম্নরূপঃ

```
npm install -g nodemon
```

ইন্সটল হওয়ার পর এই nodemon স্ক্রিপ্টটি আমার app.js ফাইলকে মনিটর করবে। app.js ফাইলে নতুন কোন কিছু লিখে সেভ দেওয়ার সাথে সাথেই এর মধ্যে কোন আউটপুট থাকলে, তা কমান্ড প্রম্পটে দেখাবে। এই ভিডিওর 38:03 সেগমেন্টে এর প্র্যাকটিক্যাল দেখা যাবে।

### live-server

গ্লোবালি ব্যবহার করার মত আরেকটি মডিউল হল, live-server। ইন্সটল করতে হলে, নিচের মত করে কমান্ড দিবঃ

```
npm install -g live-server
live-server
```

সাধারণতঃ যারা ফ্রন্টএন্ডে কাজ করেন তাদের জন্য এই মডিউলটি দারুণ কাজে আসবে। কমান্ড প্রম্পটে **live-server** লিখে এন্টার কি চাপ দিলে ডিফল্ট ব্রাউজারে নতুন একটি ট্যাব খুলবে। সেখানে index.html ফাইলটি অটোমেটিক্যালি ওপেন হয়ে যাবে। index.html ফাইলে নতুন কোন কিছু যোগ করলে বা সেখান থেকে কোন কিছু মুছে ফেললে, সেই পরিবর্তন গুলো অটোমেটিক্যালি ব্রাউজারের সেই ট্যাবে দেখা যাবে।

বিস্তারিত জানতেঃ https://www.npmjs.com/package/live-server

### package.json এর scripts অংশের কাজ

package.json ফাইলের মধ্যে scripts নামে একটি অংশ রয়েছে। সেখান থেকে আমরা আমাদের কোন স্ক্রিপ্ট ফাইলকে রান করাতে পারি। যেমনঃ

```
"scripts": {
	"start": "node app.js"
}
```

এবার package.json ফাইলটি সেভ করে কমান্ড প্রম্পট থেকে এই কমান্ডটি দেইঃ

```
npm start
```

তাহলে দেখা যাবে যে, app.js ফাইলটিতে আমাদের যে সমস্ত Javascript কোড রয়েছে, সবগুলো রান হয়ে যাবে।

scripts অংশে যদি "live-server" ব্যবহার করতে চাই, তবে, "server" attribute ব্যবহার  করতে হবে। package.json ফাইলে লিখতে হবেঃ

```
"scripts": {
	"start": "node app.js",
	"server": "live-server"
}
```

মনে রাখতে হবে, live-server ব্যবহার করতে হলে একটি HTML ফাইল লাগবে, যেটাকে ব্রাউজারে দেখানো যেতে পারে।

## npm list -g

গ্লোবাল স্কোপে কি কি প্যাকেজ ইন্সটল করা আছে, তা দেখতে হলে নীচের কমান্ডটি চালাতে হবে। এই লিস্টটি সবগুলো প্যাকেজের নাম দেখাবে।

```
npm list -g
```

যদি এক স্ক্রিন করে দেখাবে, তবে নিচের কমান্ড লিখতে হবে

```
npm list -g | more
```

যদি **প্রথম লেভেলের** প্যাকেজ লিস্ট দেখতে চাই, তবে নিচের কমান্ড লিখতে হবেঃ

```
npm list -g --depth=0 | more
```

## Using npm update and npm outdated to update dependencies

**Updating to close-by version with npm update**

Use **npm update** to freshen already installed packages. Let's say we depend on lodash version **^3.9.2**, and we have that version installed under node_modules/lodash.

Then running npm update installs version 3.10.1 under node_modules/lodash but leaves **package.json untouched** (you can change this by passing --save option).

```
npm update
```

**Going for bigger update with @latest tag**

Updating a version that is beyond semantic versioning range requires two parts. First, you ask npm to list which packages have newer versions available using **npm outdated**.

```
npm outdated
```

Then you ask npm to install the latest version of a package. You can ask for the latest version with the @latest tag. You should also use the **--save** flag to update **package.json**.

```
npm install lodash@latest --save
```
