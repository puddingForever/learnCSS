# Simple Editor

## FlexBox

## Some Tips

1. BEM (Block Element Modifier )
   how we name the css class. \_\_ indicates the class is the child element of the parent class

```
 <button class="dd-toggle">
            <i class="fas fa-crown dd-toogle__icon"></i>
 </button>
```

2. fontawesome

Check the versions and get the CDN

version webiste
https://fontawesome.com/versions

CDN website
https://cdnjs.com/libraries/font-awesome

3. When the app takes all the screen(fixed), use 100vh, 100vw

'v' indicates viewport which takes all the screen, there will be no scrolls
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

element:hover gives the element hover effect , after giving an hover effect, give transition also

```
.dd-toggle:hover{
    color:#fff;
    background-color: rgba(255,255,255,0.07);
}
```
