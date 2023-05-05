---
title: "Type conversion and coercion in Javascript"
seoTitle: "Type conversion and coercion in Javascript"
seoDescription: "This post describes the type of conversion and coercion in Javascript"
datePublished: Sun Oct 30 2022 03:03:18 GMT+0000 (Coordinated Universal Time)
cuid: cl9urp80v000b09mfb1il5c4f
slug: type-conversion-and-coercion-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/ztYmIQecyH4/upload/v1667097048352/S2WEbWPcb.jpeg
tags: type-conversion, javascript-type-coercion

---

Hey guys, welcome back In this post I am going to describe in the detail What type of conversion and coercion means in Javascript

<h3>**Conversion? **</h3>
It simply means manually converting the data. 


<h3>**coercion? **</h3>
It's the opposite of Conversion where JavaScript automatically converts the data. 


<h3>let's have a look at Conversion</h3>
For eg: When we get the data from users as input in Javascript they are usually string in nature no matter an integer or date until it's converted. let's, suppose we want to calculate the Date of Birth in this case. 

We have to manually convert it to Number 


![Screen Shot 2022-10-30 at 1.41.38 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667097705806/795vg8zwc.png align="left")

Here data is converted only inside the Number(dob+18) but the original is a string because it's inside ' '.

**Remember**, Converting does not mean we can convert anything to a Number by simply putting Number()  if we try to convert an actual string it returns NAN which also means not a number. 


![Screen Shot 2022-10-30 at 1.47.30 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667098061017/pGamrnyTt.png align="left")

<h3>lets, move to coercion </h3>

![Screen Shot 2022-10-30 at 1.52.43 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667098371369/xinL0c3Gk.png align="left")
It's quite tricky over here because the + sign triggers the coercion and concatenates the value if they are strings but the - sign subtracts if they are numbers in nature and values are integers even though they are strings. Concatenates don't mean adding but it means connecting.  This is all done by the Coercion feature of javascript automatically. 

