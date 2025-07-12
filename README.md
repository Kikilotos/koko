<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Running Cat</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #87CEEB 0%, #98FB98 100%);
            height: 100vh;
            overflow: hidden;
            font-family: Arial, sans-serif;
        }

        .ground {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 100px;
            background: linear-gradient(to bottom, #90EE90, #228B22);
            border-top: 3px solid #32CD32;
        }

        .cat-container {
            position: absolute;
            bottom: 100px;
            left: -150px;
            animation: runAcross 8s linear infinite;
        }

        .cat {
            width: 120px;
            height: 80px;
            position: relative;
            animation: bounce 0.6s ease-in-out infinite;
        }

        .cat-body {
            width: 80px;
            height: 50px;
            background: #FF6B35;
            border-radius: 25px;
            position: absolute;
            bottom: 0;
            left: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }

        .cat-head {
            width: 60px;
            height: 55px;
            background: #FF6B35;
            border-radius: 50%;
            position: absolute;
            bottom: 30px;
            left: 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }

        .cat-ears {
            position: absolute;
            top: 5px;
        }

        .ear-left, .ear-right {
            width: 0;
            height: 0;
            border-left: 12px solid transparent;
            border-right: 12px solid transparent;
            border-bottom: 20px solid #FF6B35;
            position: absolute;
        }

        .ear-left {
            left: 8px;
            transform: rotate(-15deg);
        }

        .ear-right {
            right: 8px;
            transform: rotate(15deg);
        }

        .ear-inner-left, .ear-inner-right {
            width: 0;
            height: 0;
            border-left: 6px solid transparent;
            border-right: 6px solid transparent;
            border-bottom: 10px solid #FFB6C1;
            position: absolute;
            top: 5px;
        }

        .ear-inner-left {
            left: 6px;
        }

        .ear-inner-right {
            right: 6px;
        }

        .cat-face {
            position: absolute;
            top: 20px;
            left: 15px;
        }

        .eye {
            width: 8px;
            height: 8px;
            background: #000;
            border-radius: 50%;
            position: absolute;
            animation: blink 3s infinite;
        }

        .eye-left {
            left: 8px;
        }

        .eye-right {
            right: 8px;
        }

        .nose {
            width: 6px;
            height: 4px;
            background: #FFB6C1;
            border-radius: 50%;
            position: absolute;
            top: 12px;
            left: 50%;
            transform: translateX(-50%);
        }

        .mouth {
            width: 12px;
            height: 8px;
            border: 2px solid #000;
            border-top: none;
            border-radius: 0 0 12px 12px;
            position: absolute;
            top: 18px;
            left: 50%;
            transform: translateX(-50%);
        }

        .whiskers {
            position: absolute;
            top: 15px;
            left: 50%;
            transform: translateX(-50%);
        }

        .whisker {
            width: 20px;
            height: 1px;
            background: #000;
            position: absolute;
        }

        .whisker-1 {
            top: -2px;
            left: -25px;
            transform: rotate(-10deg);
        }

        .whisker-2 {
            top: 2px;
            left: -25px;
            transform: rotate(10deg);
        }

        .whisker-3 {
            top: -2px;
            right: -25px;
            transform: rotate(10deg);
        }

        .whisker-4 {
            top: 2px;
            right: -25px;
            transform: rotate(-10deg);
        }

        .cat-tail {
            width: 8px;
            height: 40px;
            background: #FF6B35;
            border-radius: 4px;
            position: absolute;
            bottom: 20px;
            right: -5px;
            transform-origin: bottom;
            animation: wagTail 0.8s ease-in-out infinite;
        }

        .cat-legs {
            position: absolute;
            bottom: 0;
            left: 25px;
        }

        .leg {
            width: 12px;
            height: 15px;
            background: #FF6B35;
            border-radius: 6px;
            position: absolute;
            bottom: 0;
        }

        .leg-front-1 {
            left: 5px;
            animation: runLeg1 0.6s ease-in-out infinite;
        }

        .leg-front-2 {
            left: 20px;
            animation: runLeg2 0.6s ease-in-out infinite;
        }

        .leg-back-1 {
            left: 35px;
            animation: runLeg1 0.6s ease-in-out infinite;
        }

        .leg-back-2 {
            left: 50px;
            animation: runLeg2 0.6s ease-in-out infinite;
        }

        .clouds {
            position: absolute;
            top: 20px;
            width: 100%;
            height: 200px;
        }

        .cloud {
            background: white;
            border-radius: 50px;
            position: absolute;
            opacity: 0.8;
            animation: float 20s linear infinite;
        }

        .cloud-1 {
            width: 100px;
            height: 40px;
            top: 30px;
            left: 200px;
            animation-delay: 0s;
        }

        .cloud-2 {
            width: 80px;
            height: 30px;
            top: 80px;
            left: 500px;
            animation-delay: -10s;
        }

        .cloud-3 {
            width: 120px;
            height: 50px;
            top: 50px;
            left: 800px;
            animation-delay: -15s;
        }

        @keyframes runAcross {
            0% {
                left: -150px;
            }
            100% {
                left: 100vw;
            }
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        @keyframes runLeg1 {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-8px) rotate(10deg);
            }
        }

        @keyframes runLeg2 {
            0%, 100% {
                transform: translateY(-8px) rotate(-10deg);
            }
            50% {
                transform: translateY(0) rotate(0deg);
            }
        }

        @keyframes wagTail {
            0%, 100% {
                transform: rotate(10deg);
            }
            50% {
                transform: rotate(-10deg);
            }
        }

        @keyframes blink {
            0%, 95%, 100% {
                height: 8px;
            }
            97.5% {
                height: 1px;
            }
        }

        @keyframes float {
            0% {
                transform: translateX(-200px);
            }
            100% {
                transform: translateX(calc(100vw + 200px));
            }
        }

        .restart-btn {
            position: absolute;
            top: 20px;
            left: 20px;
            padding: 10px 20px;
            background: #FF6B35;
            color: white;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 16px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }

        .restart-btn:hover {
            background: #FF5722;
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div class="clouds">
        <div class="cloud cloud-1"></div>
        <div class="cloud cloud-2"></div>
        <div class="cloud cloud-3"></div>
    </div>

    <div class="cat-container">
        <div class="cat">
            <div class="cat-body"></div>
            <div class="cat-head">
                <div class="cat-ears">
                    <div class="ear-left">
                        <div class="ear-inner-left"></div>
                    </div>
                    <div class="ear-right">
                        <div class="ear-inner-right"></div>
                    </div>
                </div>
                <div class="cat-face">
                    <div class="eye eye-left"></div>
                    <div class="eye eye-right"></div>
                    <div class="nose"></div>
                    <div class="mouth"></div>
                    <div class="whiskers">
                        <div class="whisker whisker-1"></div>
                        <div class="whisker whisker-2"></div>
                        <div class="whisker whisker-3"></div>
                        <div class="whisker whisker-4"></div>
                    </div>
                </div>
            </div>
            <div class="cat-tail"></div>
            <div class="cat-legs">
                <div class="leg leg-front-1"></div>
                <div class="leg leg-front-2"></div>
                <div class="leg leg-back-1"></div>
                <div class="leg leg-back-2"></div>
            </div>
        </div>
    </div>

    <div class="ground"></div>

    <button class="restart-btn" onclick="restartAnimation()">Restart</button>

    <script>
        function restartAnimation() {
            const catContainer = document.querySelector('.cat-container');
            catContainer.style.animation = 'none';
            catContainer.offsetHeight; // Trigger reflow
            catContainer.style.animation = 'runAcross 8s linear infinite';
        }

        // Auto-restart when animation completes
        setInterval(restartAnimation, 8000);
    </script>
</body>
</html>
