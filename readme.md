# Project1 : Social Editor

![image](https://github.com/puddingForever/learnCSS/assets/126591306/347d3164-4ce3-4da4-9b36-fe0cc4862214)

**Header**

- [Basic](#Basic)
- [Animation](#Animation)
- [FlexBox](#FlexBox)

**Layout**

- [FixHeight](#Fix)
- [FlexBox2](#FlexBox2)

**SideBar**

- [FlexBox3](#FlexBox3)
- [Position](#position)
- [FlexBox4](#flexbox4)
- [@media](#media)

# Project 2

- [basic](#basicP2)
- [grid](#grid)

# Basic

![image](https://github.com/puddingForever/learnCSS/assets/126591306/0b2d5868-e949-44b8-80c6-d095251ada96)

1. BEM (Block Element Modifier )
   how we name the css class. \_\_ indicates the class is the child element of the parent class

```
 <button class="dd-toggle">
            <i class="fas fa-crown dd-toogle__icon"></i>
 </button>
```

2. fontawesome

Check the versions and get the CDN <br>
<br>
version webiste <br>
https://fontawesome.com/versions <br>
<br>
CDN website<br>
https://cdnjs.com/libraries/font-awesome<br>

3. When the app takes all the screen(fixed), use 100vh, 100vw

'v' indicates viewport which takes all the screen, there will be no scrolls <br>
vh => viewport height, vw => viewport width

```
.app{
    font-family : 'Lato', sans-serif;
    font-size : 15px;
    color : #fff;
    height : 100vh;
    width : 100vw;
}
```

4. initial indicates no styles , inherit inherits from parent element

child element doesnt automatically inhereit from parent element

```
button{
    border : initial;
    background-color: initial;
    color: inherit;
    font : inherit;
}

```

5. when working with the image use "object-fit : cover " to match aspect ratio
   <br>
   When I stretched the header, img px didnt fit.

```
.dd-toggle__img{
    height : 30px;
    width : 30px;
    object-fit : cover;
    border-radius : 50%; /*perfect round*/
    margin-right : 7px;

}

```

6. transparent & hover effect
   rgba => combine red,green,blue to some color
   when the number is close to 1 , it is close to opacity .
   but if the number is close to 0, it is close to transparent;

```
   .dd-toggle{
   color : rgba(255,255,255,0.7);
    /* color white with opacity 70%*/
   padding: 0 13px; /*top down : 0 left right 13px */
   /* when we have hover effect,  change will
   happen after 0.4s*/
    transition : all 0.4s;

   }

```

hover effect should be done seperately

```
.dd-toggle:hover{
    color:#fff;
    background-color: rgba(255,255,255,0.07);
}
```

7. Recent design color trend is to mix blue color

![image](https://github.com/puddingForever/learnCSS/assets/126591306/a897067f-f3d9-4ec4-a039-9de820f621da)

mix blueish color to its original color for the cool effect

# Animation

Use @keyframes

```
@keyframes fade-in-from-top{
    0%{
        opacity : 0;
        transform : translateY(-50px);
    }

    100%{
        opacity : 1;
        transform : translateY(0px);
    }
}

```

0% means starts and 100% means last. <br>
It will starts from opacity 0 and starts from 50px upwards(vertical) <br>
If we wanna move horizontally, use translateX <br>
![image](https://github.com/puddingForever/learnCSS/assets/126591306/b562c1c4-c437-4659-8850-967df1f8c516)

after completing @keyframes, style elements with variable

```
.logo{
    align-self: center ;
    margin-left : 20px;
    margin-right: 30px;
    animation: fade-in-from-top 0.5s;
}
```

logo will appear from upwards to original position in 0.5 seconds

# FlexBox

<a href="https://github.com/ByteGrad/Professional-CSS-Course/blob/master/slides.md">course slides from bytegrad</a>

# Fix

![image](https://github.com/puddingForever/learnCSS/assets/126591306/117768cd-01df-4958-9917-715a26fde986)

We already set the 100vh in our DOM, and since header takes the space (55px), simply substract 55px from 100vh

```
.app__container{
    height: calc(100vh -  55px);
    display: flex;
}
```

# FlexBox2

We can distribute the block size automatically <br>
First, make parent element becomes flex container

```
.app__container{
    height: calc(100vh -  55px);
    display: flex;
}
```

After that, assign sizes to each blocks

```
.sidebar{
    background-color : #10171a;
    flex : 1;
}

.panel{
    background-color : #2B363C;
    flex : 3;
}

.main{
    background-color: #edf1f3;
    flex : 12;
}
```

The size of the each elements will get smaller as the screen of devices gets smaller <br>
If we dont want that, we can just simply assign specific px

```
.sidebar{
    background-color : #10171a;
    width : 75px;
}

.panel{
    background-color : #2B363C;
    flex : 350px;
}

.main{
    background-color: #edf1f3;
    flex : 1;
}
```

the size of the sidebar and panel will remain same, cuz we assigned specific px size into it <br>
![image](https://github.com/puddingForever/learnCSS/assets/126591306/0cf0fb1f-eb56-4cd3-ae9f-f643d109e033)

# FlexBox3

![image](https://github.com/puddingForever/learnCSS/assets/126591306/d1255d17-b55f-4e14-be0a-94313dd07f41)

we have to style the icon and text in the middle.

```
<div class="sidebar">
            <section class="menu">
                <button class="menu__button">
                    <i class="fas fa-layer-group menu__icon"></i>
                    <span class="menu__text">Templates</span>
                </button>
                <button class="menu__button">
                    <i class="fas fa-image menu__icon"></i>
                    <span class="menu__text">Images</span>
                </button>
                <button class="menu__button">
                    <i class="fas fa-font menu__icon"></i>
                    <span class="menu__text">Text/Font</span>
                </button>
                <button class="menu__button">
                    <i class="fas fa-shapes menu__icon"></i>
                    <span class="menu__text">Shapes</span>
                </button>
            </section>
```

We wrap the button as flexbox. and then align-items center <br>
**(!!)** However align-items center will align items horizontally, but we need to align vertically. <br>
Therefore, use flex-direction as column **(!!!)**

```
.menu__button{
    padding : 19px 0;
    color : rgba(255,255,255,0.4);
    display: flex;
    flex-direction : column;
    align-items:center;
    width:100%;

}

```

This is without flex-direction : column <br>
![image](https://github.com/puddingForever/learnCSS/assets/126591306/6933e0ae-7caf-49f6-9847-7115885e0cba)

# position

Appearing bluebar happens when clicked, so we seperated another style element for the button element <br>
and then , it is positioned absolute when it's clicked , but since new style is inside of original element, we spare position relative to its original element <br>

```
.menu__button--active{
    background-color: #2B363B;
    color:#fff;

    position:relative;
}


.menu__button--active::before{
    content : '';
    width:3px;
    height:100%;
    background-color: #375bb6;
    position:absolute;
    left:0;
    top:0;
}

```

# flexbox4

To display &copyright logo in the bottom of the sidebar, we use flexbox <br>

make the parent container be flex container also elements are displayed in vertical way so flex-direction is column<br>

```
.sidebar{
    background-color : #10171a;
    width : 75px;
    display:flex;
    flex-direction: column;
}

```

footer has the child element which has a copyright <br>
margin-top auto means that margin top will take the top of the elements. <br>
therefore this element will go bottom <br>

```
.footer{
    /*margin will take the top . footer will go bottom*/
    margin-top:auto;

    margin-bottom:60px;
    transform:rotate(-90deg);
}

```

since we used flexbox, the copyright element is wrapped like below <br>
![image](https://github.com/puddingForever/learnCSS/assets/126591306/00e8e3ea-9f41-4845-82d2-967deb18b4f7)

use white-space nowrap to avoid it.

```
.copyright{
    color:rgba(255,255,255,0.15);
    font-size:12px;

    white-space : nowrap;
}
```

![image](https://github.com/puddingForever/learnCSS/assets/126591306/7f3719cb-bdd2-4642-92b2-fe0149465a94)

# media

@media makes the project responsive for mobile

```
/* MEDIA QUERIES*/
@media (max-width:1200px){
    .panel{
        display:none;
    }
}
```

if the panel is less than 1200px, panel disappears

# basicP2

1. google fonts

https://fonts.google.com/

```
<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
```

2. box-sizing

```
*,
*::before,
*::after{
    margin : 0;
    padding : 0;
    box-sizing: border-box;
}
```

if we add box-sizing : border-box, we are adding the border to the contents,<br>
when we calculate the width of the contents , it counts border too <br>
if we don't add box-sizing : border-box, width gets larger cuz it does not calculate the border <br>
if we add box-sizing , we should add pseudo selector too(before, after) <br>

# grid

diplay element as grid and then use grid-template-columns to specify the column width <br>
rest can assign fr keywords <br>

```
display:grid;
grid-template-columns: 355px 1fr;
```

![image](https://github.com/puddingForever/learnCSS/assets/126591306/305a7933-47c2-4880-acfd-793a34c62404)

```
display : grid;
grid-template-rows:  grid-template-rows: 65px 724px 1fr;

```

![image](https://github.com/puddingForever/learnCSS/assets/126591306/66e9e543-c471-44c5-848f-01a4b3b07a11)

Now, we assign the space for each elements using grid. <br>
if we click grid on the html below <br>
![image](https://github.com/puddingForever/learnCSS/assets/126591306/b055d7b0-29e1-4bf8-a502-7c1effa22c2d)
<br>
we will see the grid box <br>

<br>

header will take column grid 1 to 3 and row to 1 to 2

```
grid-column : 1/3;
grid-row : 1/2;
```

grid slides <br>
https://github.com/ByteGrad/Professional-CSS-Course/blob/master/slides.md
