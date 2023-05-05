---
title: "Css - Flexbox"
seoTitle: "CSS flex-box"
datePublished: Tue Aug 03 2021 06:01:14 GMT+0000 (Coordinated Universal Time)
cuid: ckrvnl5f607hdk4s100rrgko2
slug: css-flexbox
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1627970403907/-imEw40qo.png

---

Flexbox makes the layout flexible according to screen size. If the screen size is small it Contrasts and if the size is big it Expands. 

First, you need to understand this picture

![Screen Shot 2021-08-03 at 2.59.31 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627966797543/9eH_wLJxm.png)

- main axis along which flex objects are set up is the main axis of a flex container. Be aware that it is not always horizontal; it is determined by the flex-direction attribute. 

- main-start | main-end – Flex items are inserted in the container starting at main-start and working their way to main-end.

- main-size- The width or height of a flex item's major dimension, whichever is greater, is the item's main size. The major size property of a flex item is either the ‘width' or ‘height' property, depending on which is in the main dimension.

- cross-axis - The cross axis is the axis that runs perpendicular to the main axis. Its direction is determined by the primary axis.

- cross-start | cross-end - Starting on the cross-start side of the flex container and working towards the cross-end side, flex lines are filled with goods and inserted into the container.

- cross size - The cross size of a flex item is the width or height of the cross dimension, whichever is greater. Whichever of the ‘width' or ‘height' properties is present in the cross dimension is the cross size property.

If you dint Understood anything till here don't worry I got your back

1 ) Parent should have flex property its child automatically gets flex property. The box inside synchronizes and tries to fit into the screen. 

![Screen Shot 2021-08-03 at 3.27.36 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627968503422/yXGTbGSSab.png)

[ Important = The idea of flexbox is to give the container ability to fit the child element inside it, furthermore if we define px or em and rem then it might overflow the box but if we gave % it will fit the parent container because it gets parents to inherit size ] 

[ Important = If the height/ width is not mentioned it will take the whole size of its parent height and width to fit accordingly. ]

2 ) To use the horizontal we don't need to do anything but if we want to and change the position of the item inside parent (child) we need to use CSS properties [ justify-content: ] by default its flex-start, but we can change it to 
[ justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe; ]
 ---- Here I will give 3 example 

flex-end
![Screen Shot 2021-08-03 at 3.35.34 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627968982176/bwx3kCkRc.png)

space-around
![Screen Shot 2021-08-03 at 3.35.54 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627969018766/Tus_iK3lN.png)

space-between
![Screen Shot 2021-08-03 at 3.36.04 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627969034907/Z64g0ED37.png)


3) As earlier mention in all the pictures above we dint mention the height and width of the child that's why they stretched to fit inside the parent box by default, in a vertical way. But if we assign a certain height and width it will behave accordingly.

Let's change the height and of the child box differently.

![Screen Shot 2021-08-03 at 3.44.34 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627969632587/FhAdZSQOj.png)

4 ) Now suppose we want to change the position of the child inside the parent box we can use CSS properties [ align-items:  align-items: stretch | flex-start | flex-end | center ] 

Center
![Screen Shot 2021-08-03 at 3.49.20 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627969896353/3fTjGTVv7.png)

flex-end
![Screen Shot 2021-08-03 at 3.49.44 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627969899209/KZfNhz-ZoF.png)

5) As we now know that the size of a child increase or decreases when the screen does but we have another property to not decrease the size when we use static properties like px or em, rem instead it will flow the next box down on the screen. [  flex-wrap: nowrap | wrap | wrap-reverse;] 

flex-wrap:wrap
it will push the last element on the bottom
![Screen Shot 2021-08-03 at 3.56.35 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627970214777/ECBMHl31s.png)

flex-wrap:wrap-reverse
it will push all the element bottom except the item adjustable on screen and starts from the last element. 
![Screen Shot 2021-08-03 at 3.57.46 pm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627970349878/gQu9kNURb.png)
