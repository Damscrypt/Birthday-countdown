# Birthday-countdown
# Birthday-countdown
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Countdown</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #ffd1e1, #c9a0dc);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .countdown-card {
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 12px;
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.15);
            backdrop-filter: blur(4px);
            padding: 30px;
            width: 100%;
            max-width: 600px;
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .icon-row {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .icon {
            font-size: 28px;
        }
        
        .title {
            font-size: 28px;
            color: #333;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #666;
            font-size: 16px;
        }
        
        .countdown-container {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 30px;
        }
        
        .countdown-item {
            text-align: center;
        }
        
        .countdown-value {
            font-size: 36px;
            font-weight: bold;
            color: #8a2be2;
            margin-bottom: 5px;
        }
        
        .countdown-label {
            font-size: 14px;
            color: #666;
        }
        
        .message {
            text-align: center;
            margin-top: 30px;
        }
        
        .friend-name {
            font-size: 20px;
            color: #333;
            margin-bottom: 10px;
        }
        
        .message-text {
            color: #666;
            line-height: 1.6;
        }
        
        @media (max-width: 500px) {
            .countdown-value {
                font-size: 28px;
            }
            
            .title {
                font-size: 24px;
            }
        }
    </style>
</head>
<body>
    <div class="countdown-card">
        <div class="header">
            <div class="icon-row">
                <!-- Unicode emojis instead of SVG icons -->
                <span class="icon">❤️</span>
                <span class="icon">⭐</span>
                <span class="icon">🎂</span>
                <span class="icon">🎁</span>
            </div>
            <h1 class="title">The Countdown to Your Special Day!</h1>
            <p class="subtitle">Can't wait to celebrate with you! ✨</p>
        </div>
        
        <div class="countdown-container">
            <div class="countdown-item">
                <div id="days" class="countdown-value">0</div>
                <div class="countdown-label">Days</div>
            </div>
            <div class="countdown-item">
                <div id="hours" class="countdown-value">0</div>
                <div class="countdown-label">Hours</div>
            </div>
            <div class="countdown-item">
                <div id="minutes" class="countdown-value">0</div>
                <div class="countdown-label">Minutes</div>
            </div>
            <div class="countdown-item">
                <div id="seconds" class="countdown-value">0</div>
                <div class="countdown-label">Seconds</div>
            </div>
        </div>
        
        <div class="message">
            <p class="friend-name">Dear <span id="friendName">Friend</span>,</p>
            <p class="message-text">
                Every second brings us closer to celebrating another amazing year of you! 
                Can't wait to make your day special! 💖
            </p>
        </div>
    </div>

    <script>
        // CONFIGURATION - Edit these values
        const birthdayDate = "2024-12-31"; // CHANGE THIS to your friend's birthday (YYYY-MM-DD)
        const friendName = "Best Friend"; // CHANGE THIS to your friend's name
        
        // Set friend's name in the message
        document.getElementById('friendName').textContent = friendName;
        
        // Countdown timer function
        function updateCountdown() {
            const now = new Date();
            const birthday = new Date(birthdayDate);
            
            // If the birthday has already passed this year, set it for next year
            if (now > birthday) {
                birthday.setFullYear(birthday.getFullYear() + 1);
            }
            
            const difference = birthday - now;
            
            if (difference > 0) {
                const days = Math.floor(difference / (1000 * 60 * 60 * 24));
                const hours = Math.floor((difference / (1000 * 60 * 60)) % 24);
                const minutes = Math.floor((difference / 1000 / 60) % 60);
                const seconds = Math.floor((difference / 1000) % 60);
                
                document.getElementById('days').textContent = days;
                document.getElementById('hours').textContent = hours;
                document.getElementById('minutes').textContent = minutes;
                document.getElementById('seconds').textContent = seconds;
            }
        }
        
        // Update the countdown every second
        updateCountdown();
        setInterval(updateCountdown, 1000);
    </script>
</body>
</html>
