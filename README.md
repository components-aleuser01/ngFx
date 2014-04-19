ng-Fx
===============

### A simple way to add beautiful animations to your angular apps. Animations based off [animate.css](http://daneden.github.io/animate.css/). All animations are built in JavaScript.

## Dependencies
+ Angular.js (1.2+)
+ ng-Animate 
+ [GSAP.js](http://www.greensock.com/gsap-js/)

## Downloading
1. The best way to install ng-Fx is to use bower
    + ```bower install ng-Fx --save```
2. Or, from this repo
  + you'll need the main file in ```dist/ng-fx.js```
  + [TweenMax](https://github.com/greensock/GreenSock-JS/) library from GSAP 
  + [ng-Animate](http://google.com)

## Installing
1. Include ```ng-animate.js``` and ```ng-fx.js``` into your html with script tags
2. Include the dependencies into your angular app,  ```fx.animations``` 
```javascript
angular.module('myApp', ['ng-animate', 'fx.animations'])
```
##Using
###Animations
+ All animations are used with ng-animate. So you can apply them to...
  + ng-hide / ng-show
  + ng-include
  + ng-if
  + ng-view
  + ui-view (if you're using ui.router)
  + ng-switch
  + ng-class
+ Adding the animations are as simple as adding a css class. ng-Fx uses the ```'fx'``` name space. Here's an example using a fade animation. The list items will enter / leave / and move with the 'fade-down' animation.
``` html
<ul ng-init="foods=['apple', 'chips', 'muffin']">
  <li class='fx-fade-down' ng-repeat="food in foods">
    {{ food }}
  </li>
</ul>
```
###Easings
+ You can also add a different easing to any animation you want. It is as easy as adding an animation, just use a CSS class. Building on the previous example, you can just add ```fx-easing-your easing here```
``` html
<ul ng-init="foods=['apple', 'chips', 'muffin']">
  <li class='fx-fade-down fx-easing-bounce' ng-repeat="food in foods">
    {{ food }}
  </li>
</ul>
```
###Speed
+ Adjusting the speed in the ng-fx is a snap too! Your animations speeds on which they enter and leave your app are totally up to you. You just have to add a CSS class. ```fx-speed-your speed in milliseconds```. All animations have their own default speed if not provided by you.
``` html
<ul ng-init="foods=['apple', 'chips', 'muffin']">
  <li class='fx-fade-down fx-easing-bounce fx-speed-800' ng-repeat="food in foods">
    {{ food }}
  </li>
</ul>
```
###Events
+ Animations will emit events to your app when they have finished. You can listen to these events in your controllers and directives to perform other things. When an animtion is complete the even will look like so '[ enter or leave] + [animation name]', 'enter fade-down'. You just have to add the CSS class ```fx-trigger``` to an animated element.
``` javascript
angular.module('myApp', ['ng-animate', 'fx.animations'])
.directive('goAway', function(){
  function link(scope, element){
    scope.$on('enter', function(){
      element.remove();
    });
  }
  return {
    restrict: 'A',
    link: link
  };
});
```
``` html
<h1 go-away> This will be removed when an animation is done</h1>
<ul ng-init="foods=['apple', 'chips', 'muffin']">
  <li class='fx-fade-down fx-easing-bounce fx-speed-800 fx-trigger' ng-repeat="food in foods">
    {{ food }}
  </li>
</ul>
```
###List of animations and easings
+ [Animations](https://github.com/)
+ [Easings](https://github.com/)

##What's next
+ More animations
+ More flexibility
+ Easy api to create your own animations
+ Events triggered unique to dom element and not just animation type

##Contributing
1. Fork it
2. Clone your fork
3. Create new branch
4. Make changes
5. Push to new branch on your forked repo
6. Pull request from your branch to ng-Fx master

###Format for pull request
+ Pretty standard
  + in your commit message; ```(type) message [issue # closed]```
    + ```(bug) killed that bug, closes #45```
  + if you're submitting new animations:
    + ```(new fx) added 3d rotation animation ```
+ Submit issues as you see them. There are probably better, faster, easier ways to achieve what ng-Fx is designed to do so.

     


