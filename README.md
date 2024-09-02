## Hi I'm Nurmukhamed Akimbekov
## Languages and Tools:
<p>
    <img src="https://brandslogos.com/wp-content/uploads/images/large/java-logo-1.png" height="70"/>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/44/Spring_Framework_Logo_2018.svg/1280px-Spring_Framework_Logo_2018.svg.png" height="40"/>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Git_icon.svg/2048px-Git_icon.svg.png" height="50"/>
    <img src="https://www.postgresql.org/media/img/about/press/elephant.png" height="50"/>
      <img src="https://www.mysql.com/common/logos/logo-mysql-170x115.png" height="40"/>
    <img src="https://cdn4.iconfinder.com/data/icons/logos-brands-in-colors/3000/figma-logo-512.png" height="50"/>
</p>

## Here are some ideas to get you started:
🎓 Passionate backend Java developer from Kyrgyzstan<br>
🔭 I’m currently working on backend development projects<br>
🌱 I’m currently learning cloud technologies and microservices<br>
💬 Ask me about Java, Spring, and backend development<br>
📫 How to reach me: [LinkedIn](https://lnkd.in/d6iKxnky)<br>
⚡ Fun fact: I love coding and solving complex problems<br>

</p>


## Fun Feature: Snake Game
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snake Game</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        canvas {
            background-color: #ffffff;
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas" width="400" height="400"></canvas>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const scale = 20;
        const rows = canvas.height / scale;
        const columns = canvas.width / scale;

        let snake = [{ x: 0, y: 0 }];
        let dx = scale;
        let dy = 0;
        let food = { x: Math.floor(Math.random() * columns) * scale, y: Math.floor(Math.random() * rows) * scale };
        let score = 0;

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Draw food
            ctx.fillStyle = 'red';
            ctx.fillRect(food.x, food.y, scale, scale);

            // Draw snake
            ctx.fillStyle = 'green';
            snake.forEach(part => ctx.fillRect(part.x, part.y, scale, scale));

            // Move snake
            const head = { x: snake[0].x + dx, y: snake[0].y + dy };
            snake.unshift(head);

            if (head.x === food.x && head.y === food.y) {
                score++;
                food = { x: Math.floor(Math.random() * columns) * scale, y: Math.floor(Math.random() * rows) * scale };
            } else {
                snake.pop();
            }

            // Check for collisions
            if (head.x < 0 || head.y < 0 || head.x >= canvas.width || head.y >= canvas.height || snake.some(part => part.x === head.x && part.y === head.y)) {
                snake = [{ x: 0, y: 0 }];
                dx = scale;
                dy = 0;
                score = 0;
            }
        }

        function update() {
            draw();
            setTimeout(update, 100);
        }

        document.addEventListener('keydown', e => {
            switch (e.key) {
                case 'ArrowUp':
                    dx = 0;
                    dy = -scale;
                    break;
                case 'ArrowDown':
                    dx = 0;
                    dy = scale;
                    break;
                case 'ArrowLeft':
                    dx = -scale;
                    dy = 0;
                    break;
                case 'ArrowRight':
                    dx = scale;
                    dy = 0;
                    break;
            }
        });

        update();
    </script>
</body>
</html>
