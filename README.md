<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Our 1st Year Anniversary Countdown</title>
    <style>
        :root {
            --primary-color: #ff6b81;
            --secondary-color: #ff8e9e;
            --accent-color: #ffd166;
            --text-color: #333;
            --light-color: #fff9f9;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: var(--light-color);
            background-image: radial-gradient(circle, rgba(255,214,220,0.3) 1px, transparent 1px);
            background-size: 20px 20px;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: var(--text-color);
            overflow-x: hidden;
        }

        .container {
            text-align: center;
            max-width: 800px;
            width: 90%;
            padding: 2rem;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }

        .container::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color), var(--accent-color));
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 1rem;
            font-size: 2.5rem;
            font-weight: 700;
        }

        .subtitle {
            color: var(--secondary-color);
            margin-bottom: 2rem;
            font-size: 1.2rem;
        }

        .countdown {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin: 2rem 0;
        }

        .countdown-item {
            background: white;
            border-radius: 10px;
            padding: 1rem;
            min-width: 120px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            position: relative;
        }

        .countdown-item::after {
            content: "";
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 30px;
            height: 3px;
            background-color: var(--primary-color);
            border-radius: 3px;
        }

        .countdown-number {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .countdown-label {
            font-size: 0.9rem;
            color: var(--text-color);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .message {
            margin: 2rem 0;
            padding: 1.5rem;
            background: linear-gradient(135deg, rgba(255,214,220,0.5), rgba(255,255,255,0.8));
            border-radius: 10px;
            font-style: italic;
            line-height: 1.6;
        }

        .hearts {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .heart {
            position: absolute;
            background-color: var(--primary-color);
            opacity: 0;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .countdown-item {
                min-width: 90px;
                padding: 0.8rem;
            }
            
            .countdown-number {
                font-size: 2rem;
            }
        }

        footer {
            margin-top: 2rem;
            font-size: 0.9rem;
            color: var(--secondary-color);
        }
    </style>
</head>
<body>
    <div class="hearts" id="hearts-container"></div>
    
    <div class="container">
        <h1>Our 1st Year Anniversary</h1>
        <p class="subtitle">Counting down to September 1, 2025</p>
        
        <div class="countdown">
            <div class="countdown-item">
                <div class="countdown-number" id="days">00</div>
                <div class="countdown-label">Days</div>
            </div>
            <div class="countdown-item">
                <div class="countdown-number" id="hours">00</div>
                <div class="countdown-label">Hours</div>
            </div>
            <div class="countdown-item">
                <div class="countdown-number" id="minutes">00</div>
                <div class="countdown-label">Minutes</div>
            </div>
            <div class="countdown-item">
                <div class="countdown-number" id="seconds">00</div>
                <div class="countdown-label">Seconds</div>
            </div>
        </div>
        
        <div class="message">
            <p>Every moment with you is special, but this first year has been extraordinary. Looking forward to celebrating our love on our anniversary!</p>
        </div>
    </div>
    
    <footer>
        Made with love for someone very special ❤
    </footer>
    
    <script>
        // Set the date we're counting down to (September 1, 2025)
        const anniversaryDate = new Date('September 1, 2025 00:00:00').getTime();
        
        // Update the countdown every 1 second
        const countdown = setInterval(function() {
            // Get today's date and time
            const now = new Date().getTime();
            
            // Find the distance between now and the countdown date
            const distance = anniversaryDate - now;
            
            // Time calculations for days, hours, minutes and seconds
            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);
            
            // Display the result
            document.getElementById('days').innerHTML = days.toString().padStart(2, '0');
            document.getElementById('hours').innerHTML = hours.toString().padStart(2, '0');
            document.getElementById('minutes').innerHTML = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').innerHTML = seconds.toString().padStart(2, '0');
            
            // If the countdown is finished
            if (distance < 0) {
                clearInterval(countdown);
                document.getElementById('countdown').innerHTML = "Happy Anniversary!";
            }
        }, 1000);
        
        // Create floating hearts animation
        function createHearts() {
            const heartsContainer = document.getElementById('hearts-container');
            const colors = ['#ff6b81', '#ff8e9e', '#ffb3c1', '#ffd166'];
            
            // Create 15 hearts
            for (let i = 0; i < 15; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.style.width = Math.random() * 15 + 5 + 'px';
                heart.style.height = heart.style.width;
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.top = Math.random() * 100 + 'vh';
                heart.style.opacity = Math.random() * 0.5;
                heart.style.transform = `rotate(${Math.random() * 360}deg)`;
                heart.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                
                // Heart shape created via CSS
                heart.style.borderRadius = '50%';
                heart.style.position = 'absolute';
                
                heartsContainer.appendChild(heart);
                
                // Animate heart
                animateHeart(heart);
            }
        }
        
        function animateHeart(heart) {
            let pos = parseInt(heart.style.top);
            let opacity = parseFloat(heart.style.opacity);
            let speed = Math.random() * 2 + 1;
            let floatDirection = Math.random() * 2 > 1 ? 1 : -1;
            let floatAmount = Math.random() * 2 + 1;
            
            setInterval(() => {
                pos -= speed;
                heart.style.top = pos + 'px';
                
                // Small left/right movement
                let currentLeft = parseFloat(heart.style.left);
                heart.style.left = currentLeft + (floatAmount * floatDirection) + 'px';
                
                // Fade out as it reaches the top
                if (pos < -50) {
                    pos = window.innerHeight + 10;
                    heart.style.opacity = opacity;
                    heart.style.left = Math.random() * 100 + 'vw';
                }
                
            }, 50);
        }
        
        // Initialize the page
        window.onload = function() {
            createHearts();
        };
    </script>
</body>
</html>
