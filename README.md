# Hack Google Chrome and Make your Dinosaur Immortal
The game can be hacked pretty easily, making your dinosaur not even flinch at the sight of a cactus.

To hack the game, first go the the error message page where your dinosaur is hanging out.

Go ahead and press the space bar to start the game. Once the game starts, right-click and select ``Inspect” to open up Chrome DevTools``, then select the ``Console`` tab.``Inspect” to open up Chrome DevTools``, then select the ``Console`` tab.

You can also do this by using the Ctrl+Shift+I shortcut, which takes you straight to the  Console tab of DevTools.



### Open Chrome Console

- Make sure you are on the No Internet Connection page.
- Right click anywhere on the page and select Inspect.
- Go to Console tab. This is where we will enter the commands to tweak the game.



#### Tweaking Speed

Type the following command in Console and press enter. You can use any other speed in place of 1000.

```js
Runner.instance_.setSpeed(1000)
```



#### Immortality

After every command press enter. All the commands are case-sensitive.

We store the original game over function in a variable:

```js
var original = Runner.prototype.gameOver
```

Then, we make the game over function empty:

```js
Runner.prototype.gameOver = function(){}
```

Stopping the game after using Immortality

When you want to stop the game, Revert back to the original game over function:

```js
Runner.prototype.gameOver = original
```



#### Setting the current score

Let’s set the score to 12345. You can set any other score less than 99999. The current score is reset on game over.

```js
Runner.instance_.distanceRan = 12345 / Runner.instance_.distanceMeter.config.COEFFICIENT
```



#### Dino jumping too high?

You can control how high the dino jumps by using the below function. Adjust the value as necessary.

```js
Runner.instance_.tRex.setJumpVelocity(10)
```


#### Automatic jumping and Crouching

I have compiled it into a script along with a cool tool i found that automates jumping and crouching.

```js
function keyDown(e){Podium={};var n=document.createEvent("KeyboardEvent");Object.defineProperty(n,"keyCode",{get:function(){return this.keyCodeVal}}),n.initKeyboardEvent?n.initKeyboardEvent("keydown",!0,!0,document.defaultView,e,e,"","",!1,""):n.initKeyEvent("keydown",!0,!0,document.defaultView,!1,!1,!1,!1,e,0),n.keyCodeVal=e,document.body.dispatchEvent(n)}function keyUp(e){Podium={};var n=document.createEvent("KeyboardEvent");Object.defineProperty(n,"keyCode",{get:function(){return this.keyCodeVal}}),n.initKeyboardEvent?n.initKeyboardEvent("keyup",!0,!0,document.defaultView,e,e,"","",!1,""):n.initKeyEvent("keyup",!0,!0,document.defaultView,!1,!1,!1,!1,e,0),n.keyCodeVal=e,document.body.dispatchEvent(n)}setInterval(function(){Runner.instance_.horizon.obstacles.length>0&&(Runner.instance_.horizon.obstacles[0].xPos<25*Runner.instance_.currentSpeed-Runner.instance_.horizon.obstacles[0].width/2&&Runner.instance_.horizon.obstacles[0].yPos>75&&(keyUp(40),keyDown(38)),Runner.instance_.horizon.obstacles[0].xPos<30*Runner.instance_.currentSpeed-Runner.instance_.horizon.obstacles[0].width/2&&Runner.instance_.horizon.obstacles[0].yPos<=75&&keyDown(40))},5);
Runner.instance_.setSpeed(1000)
var original = Runner.prototype.gameOver
Runner.prototype.gameOver = function(){}
//Runner.prototype.gameOver = original
Runner.instance_.distanceRan = 12345 / Runner.instance_.distanceMeter.config.COEFFICIENT
Runner.instance_.tRex.setJumpVelocity(10)
```

#### Laser

T-rex shoot laser hit.

```js
b = Runner.instance_.clearCanvas;
window.addEventListener("keydown", checkKeyPressed, false); function checkKeyPressed(l) { if (l.keyCode == "68" ) {drawline()}};
function drawline() {
if (Runner.instance_.horizon.obstacles.length>0){
Runner.instance_.clearCanvas=function(){};
Runner.instance_.canvasCtx.beginPath();
Runner.instance_.canvasCtx.moveTo(Runner.instance_.tRex.xPos+23,Runner.instance_.tRex.yPos+20);
Runner.instance_.canvasCtx.lineTo(Runner.instance_.horizon.obstacles[0].xPos+10,Runner.instance_.horizon.obstacles[0].yPos+10);
Runner.instance_.canvasCtx.stroke();
setTimeout(function(){Runner.instance_.clearCanvas = b;}, 15);
Runner.instance_.horizon.removeFirstObstacle();}}
```

#### Change Enviroment Speed

Changes Enviroment Speed

```js
Runner.config.ACCELERATION = 10000
```

#### Do Nothing but gain Points

stand still and gain points

```js
Runner.instance_.playingIntro = true;
```
to set it back to normal

```js
Runner.instance_.playingIntro = false;
```
