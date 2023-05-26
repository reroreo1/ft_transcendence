<template>
    <div id="movingDiv">
    </div>
</template>

<script>
import p5 from 'p5';
export default {
    name: 'animateDiv',
    mounted() {
        this.createSketch();
    },
    methods: {
        createSketch() {
            new p5((sketch) => {
                let width = 400;
                let height = 200;
                let ballX, ballY, ballSpeedX, ballSpeedY, ballSize;
                let paddle1Y, paddle2Y, paddleWidth, paddleHeight, paddleSpeed;
                let ballColor, paddleColor;
                sketch.setup = function () {
                    var cnv = sketch.createCanvas(width, height);
                    cnv.parent("movingDiv");
                    // console.log(myp5.parent);
                    ballX = width / 2;
                    ballY = height / 2;
                    ballSpeedX = -5; // Random initial X speed
                    ballSpeedY = -5; // Random initial Y speed
                    ballSize = 20;
                    ballColor = sketch.color(255, 255, 255); // White color
                    // Initialize paddle variables
                    paddleWidth = 10;
                    paddleHeight = 100;
                    paddleSpeed = 5;
                    paddle1Y = height / 2 - paddleHeight / 2; // Left paddle position
                    paddle2Y = height / 2 - paddleHeight / 2; // Right paddle position
                    paddleColor = sketch.color(255, 255, 255); // White color
                };

                sketch.draw = function () {
                    sketch.clear();
                    // sketch.background(255); // Black background
                    sketch.strokeWeight(5);
                    sketch.stroke(255);
                    setLineDash([15, 15, 15, 15]); //another dashd line pattern
                    sketch.line(200, 0, 200, 200);
                    // Update ball position
                    ballX += ballSpeedX;
                    ballY += ballSpeedY;
                    sketch.fill(50);
                    setLineDash([0]);
                    sketch.rect(200 - 15, 100 - 15, 30, 30);
                    sketch.noStroke();
                    // Draw ball
                    sketch.drawingContext.shadowBlur = 80;
                    sketch.drawingContext.shadowColor = sketch.color(255, 255, 255);
                    sketch.fill(ballColor);
                    sketch.ellipse(ballX, ballY, ballSize, ballSize);
                    sketch.drawingContext.shadowBlur = 0;
                    sketch.drawingContext.shadowColor = sketch.color(0);
                    // Draw left paddle
                    sketch.fill(paddleColor);
                    sketch.rect(0, paddle1Y, paddleWidth, paddleHeight);
                    // Draw right paddle
                    sketch.fill(paddleColor);
                    sketch.rect(width - paddleWidth, paddle2Y, paddleWidth, paddleHeight);
                    // Move the paddles automatically
                    if (ballY < paddle1Y + paddleHeight / 2) {
                        paddle1Y -= paddleSpeed;
                    } else {
                        paddle1Y += paddleSpeed;
                    }
                    if (ballY < paddle2Y + paddleHeight / 2) {
                        paddle2Y -= paddleSpeed;
                    } else {
                        paddle2Y += paddleSpeed;
                    }

                    // Keep paddles within canvas boundaries
                    paddle1Y = sketch.constrain(paddle1Y, 0, height - paddleHeight);
                    paddle2Y = sketch.constrain(paddle2Y, 0, height - paddleHeight);

                    // Check ball collision with paddles
                    if (
                        ballY + ballSize / 2 > paddle1Y &&
                        ballY - ballSize / 2 < paddle1Y + paddleHeight &&
                        ballX - ballSize / 2 < paddleWidth
                    ) {
                        ballSpeedX *= -1;
                    }

                    if (
                        ballY + ballSize / 2 > paddle2Y &&
                        ballY - ballSize / 2 < paddle2Y + paddleHeight &&
                        ballX + ballSize / 2 > width - paddleWidth
                    ) {
                        ballSpeedX *= -1;
                    }

                    // Check ball collision with top and bottom walls
                    if (ballY - ballSize / 2 < 0 || ballY + ballSize / 2 > height) {
                        ballSpeedY *= -1;
                    }

                    // Check ball going off the sides of the canvas
                    if (ballX - ballSize / 2 > width || ballX + ballSize / 2 < 0) {
                        resetBall();
                    }
                };

                function setLineDash(list) {
                    sketch.drawingContext.setLineDash(list);
                }
                // Reset the ball to the center of the canvas
                function resetBall() {
                    ballX = width / 2;
                    ballY = height / 2;
                    ballSpeedX = 5;
                    ballSpeedY = 5;
                }
            }, this.$refs.movingDiv);
        }
    }
}
</script>

<style>
#movingDiv {
    width: 400px;
    height: 200px;
    box-shadow: rgb(238, 238, 238) 0px 0px 0px 2px inset, rgb(0, 0, 0) 10px -10px 0px -3px, rgb(238, 238, 238) 10px -10px, rgb(0, 0, 0) 20px -20px 0px -3px, rgb(238, 238, 238) 20px -20px, rgb(0, 0, 0) 30px -30px 0px -3px, rgb(238, 238, 238) 30px -30px, rgb(0, 0, 0) 40px -40px 0px -3px, rgb(238, 238, 238) 40px -40px;
    position: absolute;
    animation-name: moveAnimation;
    animation-duration: 4s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
}

@keyframes moveAnimation {
    0% {
        top: 20%;
        left: 54%;
    }

    25% {
        top: 45%;
        left: 54%;
    }

    50% {
        top: 20%;
        left: 54%;
    }

    75% {
        top: 45%;
        left: 54%;
    }

    100% {
        top: 20%;
        left: 54%;
    }
}</style>