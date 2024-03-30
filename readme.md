# Project1 : Social Editor

- [Basic](#Basic)
- [Animation](#Animation)
- [FlexBox](#FlexBox)

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
   when the number is close to 1 , it is close to opacity.
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
