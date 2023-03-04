Animations in CSS
=================

In this challenge, you will be learning how to create animations in CSS.

Example
-------

Let's start with a simple example. Suppose we have a `div` element that we want to animate. Here is the CSS code to achieve this:

```css
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 2s;
  animation-iteration-count: infinite;
}

@keyframes example {
  0% {background-color: red;}
  50% {background-color: yellow;}
  100% {background-color: blue;}
}`
```

In this example, we have created a `div` element with a red background color. We have also defined an animation using the `@keyframes` rule. The animation is named `example` and has a duration of 2 seconds. It will loop infinitely, thanks to the `animation-iteration-count` property. Finally, we have applied the animation to the `div` element using the `animation-name` property.

The `@keyframes` rule defines the different states of the animation. In this case, we are changing the background color of the `div` element from red to yellow to blue.

Releases
--------

#### Release 1:  Define a CSS class `.fade-in` that will fade in an element over a period of 1 second.

#### Release 2:  Define a CSS class `.bounce` that will make an element bounce up and down three times.

#### Release 3:  Define a CSS class `.rotate` that will rotate an element continuously.

#### Release 4:  Write CSS code to create a loading spinner using CSS animations.

#### Release 5:  Create a button with a hover effect that changes the background color of the button to a random color.



## Solution

#### Release 1:  Define a CSS class `.fade-in` that will fade in an element over a period of 1 second.
```css
.fade-in {
  opacity: 0;
  animation: fade-in 1s ease-in-out forwards;
}

@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```

#### Release 2:  Define a CSS class `.bounce` that will make an element bounce up and down three times.
```css
.bounce {
  animation: bounce 1s ease-in-out 0s 3 normal;
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}
```

#### Release 3:  Define a CSS class `.rotate` that will rotate an element continuously.
```css
.rotate {
  animation: rotate 2s linear infinite;
}

@keyframes rotate {
  0% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

#### Release 4:  Write CSS code to create a loading spinner using CSS animations.
```css
.spinner {
  display: inline-block;
  position: relative;
  width: 40px;
  height: 40px;
}

.spinner div {
  box-sizing: border-box;
  display: block;
  position: absolute;
  width: 32px;
  height: 32px;
  margin: 6px;
  border: 4px solid #000;
  border-radius: 50%;
  animation: spinner 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  border-color: #000 transparent transparent transparent;
}

.spinner div:nth-child(1) {
  animation-delay: -0.45s;
}

.spinner div:nth-child(2) {
  animation-delay: -0.3s;
}

.spinner div:nth-child(3) {
  animation-delay: -0.15s;
}

@keyframes spinner {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

#### Release 5:  Create a button with a hover effect that changes the background color of the button to a random color.
```css
button:hover {
  background-color: #${Math.floor(Math.random()*16777215).toString(16)};
}
```







#  CSS Animations Challenge

In this challenge, you will be creating CSS animations to add some interactivity and visual appeal to a website. 

## Example

```html
<div class="box"></div>
```

```css
.box {
  width: 100px;
  height: 100px;
  background-color: blue;
  animation: fade-in 1s;
}

@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```
This will fade in a blue box over a period of 1 second.

Releases
--------

### Release 1

Define a CSS class `.zoom-in` that will zoom in an element over a period of 1 second.

### Release 2

Define a CSS class `.rotate` that will rotate an element 360 degrees over a period of 2 seconds.

### Release 3

Define a CSS class `.flash` that will change the background color of an element from white to red to white over a period of 1 second.

### Release 4

Write CSS code to create a loading bar using CSS animations.

### Release 5

Create a button with a hover effect that changes the background color of the button to a different color. The color should be chosen randomly from a set of 5 colors.

Conclusion
----------

In this challenge, you have learned how to create CSS animations to add interactivity and visual appeal to a website. Animations can be a powerful tool to engage users and make your website stand out.


## Solution

### Release 1

```css
.zoom-in {
  animation-name: zoomIn;
  animation-duration: 1s;
}

@keyframes zoomIn {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(1);
  }
}
```

### Release 2

```css
.rotate {
  animation-name: rotate360;
  animation-duration: 2s;
}

@keyframes rotate360 {
  to {
    transform: rotate(360deg);
  }
}
```

### Release 3

```css
.flash {
  animation-name: flash;
  animation-duration: 1s;
}

@keyframes flash {
  0% {
    background-color: white;
  }
  50% {
    background-color: red;
  }
  100% {
    background-color: white;
  }
}

```

### Release 4

```css
.loading-bar {
  height: 10px;
  width: 100%;
  background-color: #eee;
  animation-name: loadingBar;
  animation-duration: 2s;
  animation-iteration-count: infinite;
}

@keyframes loadingBar {
  from {
    width: 0%;
  }
  to {
    width: 100%;
  }
}
```

### Release 5

```css
.random-color-button {
  background-color: blue;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.random-color-button:hover {
  background-color: #f6b352;
}

.random-color-button:hover {
  background-color: #f6b352;
}

.random-color-button:hover {
  background-color: #f6b352;
}

.random-color-button:hover {
  background-color: #f6b352;
}

.random-color-button:hover {
  background-color: #f6b352;
}
```