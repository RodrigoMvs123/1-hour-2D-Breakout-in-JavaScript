# 1-hour-2D-Breakout-in-JavaScript

https://www.youtube.com/watch?v=sAnHM4D9e7U&t=2071s 

https://raw.githubusercontent.com/RodrigoMvs123/1-hour-2D-Breakout-in-JavaScript/main/README.md

https://github.com/RodrigoMvs123/1-hour-2D-Breakout-in-JavaScript/blame/main/README.md

Visual Studio Code
Explorer
Open Editors
index.html

index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2D Breakout Game</title>
    <link rel="stylesheet" href="styles.css"
</head>
<body>
    
    <h1 id="score">0</h1>
    <div class="grid"></div>

</body>
</html>

Visual Studio Code
Explorer
Open Editors
index.html
styles.css

styles.css

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

app.js

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2D Breakout Game</title>
    <link rel="stylesheet" href="styles.css"
</head>
<body>
    
    <h1 id="score">0</h1>
    <div class="grid"></div>

    <script src="app.js"></script>

</body>
</html>

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

styles.css
.grid {
    position: absolute;
    width: 560px;
    height: 300px;
    border: solid 1px black;
    margin-top: 100px;
}

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

app.js
const grid = document.querySelector('.grid')
const scoreDisplay = document.querySelector('#score')
const blockWidht = 100
const blockHight = 20
const boardWidth = 560
const boardHeight = 300

const userStart = [230, 10]
let currentPosition = userStart

const ballStart = [270, 40]
let ballCurrentPosition = ballStart

// add user
const user = document.createElement('div')
user.classList.add('user')

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

styles.css
.grid {
    position: absolute;
    width: 560px;
    height: 300px;
    border: solid 1px black;
    margin-top: 100px;
}

.user {
    position: absolute;
    width: 100px;
    height: 20px;
    background-color: blue;
}

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

app.js
const grid = document.querySelector('.grid')
const scoreDisplay = document.querySelector('#score')
const blockWidht = 100
const blockHight = 20
const boardWidth = 560
const boardHeight = 300

const userStart = [230, 10]
let currentPosition = userStart

const ballStart = [270, 40]
let ballCurrentPosition = ballStart

// add user
const user = document.createElement('div')
user.classList.add('user')
grid.appendChild(user)
drawUser()

// add ball
const ball = document.createElement('div')
ball.classList.add('ball')

function drawUser() {
    user.style.left = currentPosition[0] + 'px'
    user.style.bottom = currentPosition[1] + 'px'
}


Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

styles.css
.grid {
    position: absolute;
    width: 560px;
    height: 300px;
    border: solid 1px black;
    margin-top: 100px;
}

.user {
    position: absolute;
    width: 100px;
    height: 20px;
    background-color: blue;
}

.ball {
    position: absolute;
    width: 20px;
    height: 20px;
    border-radius: 10;
    background-color: red;
}

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

app.js
const grid = document.querySelector('.grid')
const scoreDisplay = document.querySelector('#score')
const blockWidht = 100
const blockHight = 20
const boardWidth = 560
const boardHeight = 300

const userStart = [230, 10]
let currentPosition = userStart

const ballStart = [270, 40]
let ballCurrentPosition = ballStart

// my block
class block {
    constructor(xAxis, yAxis) {
        this.bottomLeft = [xAxis, yAxis]
        this.bottomRight = [xAxis + blockWidht, yAxis] 
        this.topRight = [xAxis + blockWidht, yAxis + blockHight]
        this.topLeft = [xAxis, yAxis + blockHight]
    }
}

// all my blocks
const blocks = [
    new Block(10,270),
    new Block(120,270),
    new Block(230,270),
    new Block(340,270),
    new Block(450,270),
    new Block(10,240),
    new Block(120,240),
    new Block(230,240),
    new Block(340,240),
    new Block(450,240),
    new Block(10,210),
    new Block(120,210),
    new Block(230,210),
    new Block(340,210),
    new Block(450,210)
]

// draw my blocks
function addBlocks() {
    for(let i = 0; i < blocks.lenght; i++) {
        const block = document.createElement('div')
        block.classList.add('block')
    }
}

// add user
const user = document.createElement('div')
user.classList.add('user')
grid.appendChild(user)
drawUser()

// add ball
const ball = document.createElement('div')
ball.classList.add('ball')
grid.appendChild(ball)
drawBall()

function drawUser() {
    user.style.left = currentPosition[0] + 'px'
    user.style.bottom = currentPosition[1] + 'px'
}

function drawBall() {
    ball.style.left = ballCurrentPosition[0] + 'px'
    ball.style.bottom = ballCurrentPosition[1] + 'px'
}

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

styles.css
.grid {
    position: absolute;
    width: 560px;
    height: 300px;
    border: solid 1px black;
    margin-top: 100px;
}

.user {
    position: absolute;
    width: 100px;
    height: 20px;
    background-color: blueviolet;
}

.block {
    position: absolute;
    width: 100px;
    height: 20px;
    background-color: blue;
}

.ball {
    position: absolute;
    width: 20px;
    height: 20px;
    border-radius: 10;
    background-color: red;
}

Visual Studio Code
Explorer
Open Editors
index.html
styles.css
app.js

app.js
const grid = document.querySelector('.grid')
const scoreDisplay = document.querySelector('#score')
const blockWidht = 100
const blockHight = 20
const ballDiameter = 20       
const boardWidth = 560
const boardHeight = 300
let xDirection = -2
let yDirection = 2

let timerId
let score = 0

const userStart = [230, 10]
let currentPosition = userStart

const ballStart = [270, 40]
let ballCurrentPosition = ballStart

// my block
class block {
    constructor(xAxis, yAxis) {
        this.bottomLeft = [xAxis, yAxis]
        this.bottomRight = [xAxis + blockWidht, yAxis] 
        this.topRight = [xAxis + blockWidht, yAxis + blockHight]
        this.topLeft = [xAxis, yAxis + blockHight]
    }
}

// all my blocks
const blocks = [
    new Block(10,270),
    new Block(120,270),
    new Block(230,270),
    new Block(340,270),
    new Block(450,270),
    new Block(10,240),
    new Block(120,240),
    new Block(230,240),
    new Block(340,240),
    new Block(450,240),
    new Block(10,210),
    new Block(120,210),
    new Block(230,210),
    new Block(340,210),
    new Block(450,210)
]

// draw my blocks
function addBlocks() {
    for(let i = 0; i < blocks.lenght; i++) {
        const block = document.createElement('div')
        block.classList.add('block')
        block.style.left = blocks[i].bottomLeft[0] + 'px'
        block.style.bottom = blocks[i].bottomLeft[1] + 'px'

        grid.appendChild(block)
    }
}
addBlocks()

// add user
const user = document.createElement('div')
user.classList.add('user')
grid.appendChild(user)
drawUser()

// add ball
const ball = document.createElement('div')
ball.classList.add('ball')
grid.appendChild(ball)
drawBall()

function drawUser() {
    user.style.left = currentPosition[0] + 'px'
    user.style.bottom = currentPosition[1] + 'px'
}

function drawBall() {
    ball.style.left = ballCurrentPosition[0] + 'px'
    ball.style.bottom = ballCurrentPosition[1] + 'px'
}

// move user
function moveUser(e) {
    switch(e.key) {
        case 'ArrowLeft': 
            if (currentPosition[0] > 0) {
                currentPosition[0] -= 10
                drawUser()
            }
            break
        case 'ArrowRight':
            if (currentPosition[0] < (boardWidth - blockWidht)) {
                currentPosition[0] += 10
                drawUser()
            }
            break
    }
}
document.addEventListener('keydown', moveUser)

// move ball
function moveBall() {
    ballCurrentPosition[0] += xDirection
    ballCurrentPosition[1] += yDirection
    drawBall()  
    checkForCollision()
}
timerId = setInterval(moveBall, 30)

// check for collision
function checkForCollision() {
    // check for block collision
    for (let i = 0; i < block.length; i++) {
        if
        (
            ballCurrentPosition[0] > blocks[i].bottomLeft[0] && 
            ballCurrentPosition[0] < blocks[i].bottomRight[0] &&
            (ballCurrentPosition[1] + ballDiameter) > blocks[i].bottomLeft[1] &&
            ballCurrentPosition[1] < blocks[i].topLeft[1]
        ) {
            const allBlocks = document.querySelectorAll('.block')
            allBlocks[i].classList.remove('block')
            blocks.splice(i, 1)
            changeDirection()
            score++
            scoreDisplay.innerHTML = score
            if (blocks.length == 0) {
                scoreDisplay.innerHTML = 'You Win !'
                clearInterval(timerId)
                document.removeEventListener('keydow', moveUser)
            }
        }
    }
    // check for wall hits
    if
    (
        ballCurrentPosition[0] >= (boardWidth - ballDiameter) || 
        ballCurrentPosition[0] <= 0 || 
        ballCurrentPosition[1] >= (boardHeight - ballDiameter)
    ) {
        changeDirection()
    }

    // check for user collision
    if
    (
        ballCurrentPosition[0] > currentPosition[0] &&
        ballCurrentPosition[0] < currentPosition[0] + blockWidht &&
        (ballCurrentPosition[1] + currentPosition[1] && 
            ballCurrentPosition[1] < currentPosition[1] + blockHight)
    ) {
        changeDirection()
    }

    // game over
    if (ballCurrentPosition[1] <= 0) {
        clearInterval(timerId)
        scoreDisplay.innerHTML = 'You lose !'
        document.removeEventListener('keydown', moveUser)
    }
}

function changeDirection() {
    if (xDirection === 2 & yDirection === 2) {
        yDirection = -2
        return
    }
    if (xDirection === 2 & yDirection === -2) {
        xDirection = -2
        return
    }
    if (xDirection === -2 & yDirection === -2) {
        yDirection = 2
        return
    }
    if (xDirection === -2 & yDirection === 2) {
        xDirection = 2
        return
    }
}


