<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Termux Hacker Terminal | Rahmat Afghan</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Reset and Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-weight: bold;
        }
        
        body {
            background: #001a00;
            color: #0f0;
            font-family: 'Courier New', monospace;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(0, 80, 0, 0.1) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(0, 60, 0, 0.1) 0%, transparent 20%);
        }
        
        .terminal-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(0deg, rgba(0, 30, 0, 0.1), rgba(0, 30, 0, 0.1) 1px, transparent 1px, transparent 2px);
            z-index: -2;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            z-index: 10;
            position: relative;
        }
        
        /* Header Styles */
        header {
            text-align: center;
            padding: 30px 0;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            border-bottom: 2px solid #0f0;
        }
        
        .title-container {
            position: relative;
            padding: 20px;
            background: rgba(0, 20, 0, 0.3);
            border-radius: 5px;
            border: 1px solid #0f0;
            box-shadow: 0 0 30px rgba(0, 255, 0, 0.3);
            backdrop-filter: blur(5px);
        }
        
        .main-title {
            font-size: 3.5rem;
            margin-bottom: 10px;
            letter-spacing: 3px;
            font-family: 'Courier New', monospace;
            animation: flicker 2s infinite alternate;
            text-shadow: 0 0 15px rgba(0, 255, 0, 0.7);
            color: #0f0;
        }
        
        .sub-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            animation: glow 3s infinite alternate;
            color: #0f0;
        }
        
        .hacker-quote {
            color: #0f0;
            font-size: 1.2rem;
            animation: typing 8s steps(80, end), blink 0.7s step-end infinite alternate, float 4s infinite ease-in-out;
            white-space: nowrap;
            overflow: hidden;
            border-right: 2px solid #0f0;
            width: fit-content;
            margin: 0 auto;
            padding: 0 10px;
            font-family: monospace;
        }
        
        .terminal-strip {
            height: 4px;
            background: linear-gradient(90deg, transparent, #0f0, transparent);
            animation: scanline 3s linear infinite;
            margin: 15px 0;
        }
        
        /* Form Container */
        .form-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 40px;
        }
        
        @media (max-width: 900px) {
            .form-container {
                grid-template-columns: 1fr;
            }
        }
        
        /* Report Section - Terminal Style */
        .report-section {
            background: rgba(0, 15, 0, 0.3);
            border: 1px solid rgba(0, 255, 0, 0.3);
            border-radius: 5px;
            padding: 20px;
            box-shadow: 0 8px 32px 0 rgba(0, 31, 0, 0.37);
            transition: all 0.4s ease;
            backdrop-filter: blur(5px);
            position: relative;
            overflow: hidden;
        }
        
        .report-section:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 40px rgba(0, 255, 0, 0.5);
            border-color: rgba(0, 255, 255, 0.5);
        }
        
        .report-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, #0f0, transparent);
            animation: scanline 3s linear infinite;
        }
        
        .section-title {
            text-align: center;
            font-size: 1.8rem;
            margin-bottom: 25px;
            padding-bottom: 10px;
            border-bottom: 1px solid rgba(0, 255, 0, 0.3);
            font-family: 'Courier New', monospace;
            animation: glow 3s infinite alternate;
            color: #0ff;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 10px;
            font-size: 1.1rem;
            color: #0ff;
            font-family: 'Courier New', monospace;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            background: rgba(0, 10, 0, 0.4);
            border: 1px solid rgba(0, 255, 0, 0.3);
            border-radius: 5px;
            color: #0f0;
            font-size: 1rem;
            transition: all 0.3s;
            font-family: 'Courier New', monospace;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #0ff;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.5);
            background: rgba(0, 30, 0, 0.5);
        }
        
        input::placeholder {
            color: #0a0;
        }
        
        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }
        
        button {
            flex: 1;
            background: linear-gradient(to bottom, #003300, #001100);
            color: #0f0;
            border: 1px solid rgba(0, 255, 0, 0.3);
            padding: 15px;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
            letter-spacing: 1px;
            text-shadow: 0 0 5px #0f0;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
            font-family: 'Courier New', monospace;
        }
        
        button:hover {
            background: linear-gradient(to bottom, #005500, #003300);
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.5);
            transform: translateY(-3px);
        }
        
        button::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.1);
            transform: rotate(30deg);
            transition: all 0.6s;
        }
        
        button:hover::after {
            transform: rotate(30deg) translate(50%, 50%);
        }
        
        .btn-generate {
            background: linear-gradient(to bottom, #002244, #001122);
        }
        
        .btn-contact {
            background: linear-gradient(to bottom, #440000, #220000);
        }
        
        /* Contact Section */
        .contact-section {
            background: rgba(10, 0, 15, 0.3);
            border: 1px solid rgba(150, 0, 255, 0.3);
            border-radius: 5px;
            padding: 25px;
            margin-top: 30px;
            text-align: center;
            backdrop-filter: blur(5px);
            position: relative;
            overflow: hidden;
        }
        
        .contact-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            font-family: 'Courier New', monospace;
            animation: glow 3s infinite alternate;
            color: #f0f;
        }
        
        .contact-info {
            font-size: 1.2rem;
            margin-bottom: 25px;
            font-family: 'Courier New', monospace;
            color: #0ff;
        }
        
        .contact-links {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            margin-top: 20px;
        }
        
        .contact-link {
            display: inline-block;
            padding: 15px 30px;
            background: linear-gradient(to right, #008833, #006622);
            color: white;
            text-decoration: none;
            border-radius: 3px;
            font-size: 1.2rem;
            font-weight: bold;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0, 200, 83, 0.3);
            font-family: 'Courier New', monospace;
            width: 300px;
            max-width: 100%;
            text-align: center;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(0, 255, 0, 0.3);
        }
        
        .contact-link:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 25px rgba(0, 200, 83, 0.6);
        }
        
        .contact-link.ban {
            background: linear-gradient(to right, #882200, #661100);
            box-shadow: 0 5px 15px rgba(255, 61, 0, 0.3);
        }
        
        .contact-link.ban:hover {
            box-shadow: 0 8px 25px rgba(255, 61, 0, 0.6);
        }
        
        .contact-link i {
            margin-left: 10px;
        }
        
        /* Platforms Section - Terminal Design */
        .platforms-section {
            background: rgba(15, 15, 0, 0.3);
            border-radius: 5px;
            padding: 30px;
            margin-top: 30px;
            text-align: center;
            border: 1px solid rgba(255, 255, 0, 0.3);
            box-shadow: 0 8px 32px 0 rgba(100, 100, 0, 0.3);
            backdrop-filter: blur(5px);
            position: relative;
            overflow: hidden;
        }
        
        .platforms-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        
        .platform-card {
            background: rgba(5, 5, 10, 0.4);
            border-radius: 5px;
            padding: 25px;
            transition: all 0.4s;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(100, 255, 100, 0.3);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(5px);
        }
        
        .platform-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 255, 0, 0.4);
            border-color: rgba(0, 255, 255, 0.5);
        }
        
        .platform-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 0, 0.1), transparent);
            transition: 0.5s;
            z-index: 1;
        }
        
        .platform-card:hover::before {
            transform: rotate(180deg);
        }
        
        .platform-card-content {
            position: relative;
            z-index: 2;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        
        .platform-card i {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: #0f0;
            filter: drop-shadow(0 0 5px rgba(0, 255, 0, 0.7));
        }
        
        .platform-card h3 {
            color: #0f0;
            margin-bottom: 15px;
            font-family: 'Courier New', monospace;
            font-size: 1.5rem;
            text-shadow: 0 0 5px #0f0;
        }
        
        .platform-card a {
            display: inline-block;
            color: #0ff;
            text-decoration: none;
            font-size: 1.1rem;
            font-family: 'Courier New', monospace;
            transition: all 0.3s;
            padding: 10px 20px;
            border-radius: 3px;
            background: rgba(0, 15, 0, 0.4);
            border: 1px solid rgba(0, 255, 0, 0.3);
            margin-top: 10px;
        }
        
        .platform-card a:hover {
            background: rgba(0, 30, 0, 0.6);
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.5);
            transform: scale(1.05);
        }
        
        /* Copy Text Section - Terminal Design */
        .copy-section {
            background: rgba(10, 5, 15, 0.3);
            border-radius: 5px;
            padding: 30px;
            margin-top: 40px;
            border: 1px solid rgba(200, 0, 255, 0.3);
            box-shadow: 0 8px 32px 0 rgba(75, 0, 130, 0.3);
            backdrop-filter: blur(5px);
            position: relative;
            overflow: hidden;
        }
        
        .copy-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, #f0f, transparent);
            animation: scanline 3s linear infinite;
        }
        
        .copy-section-title {
            text-align: center;
            font-size: 1.8rem;
            margin-bottom: 30px;
            font-family: 'Courier New', monospace;
            color: #f0f;
            text-shadow: 0 0 10px rgba(255, 0, 255, 0.7);
            animation: glow 3s infinite alternate;
        }
        
        .copy-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .copy-item {
            background: rgba(8, 3, 13, 0.4);
            border-radius: 5px;
            padding: 20px;
            border: 1px solid rgba(150, 50, 255, 0.3);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
        }
        
        .copy-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(150, 50, 255, 0.5);
            border-color: rgba(200, 0, 255, 0.5);
        }
        
        .copy-item-title {
            color: #0ff;
            font-size: 1.3rem;
            margin-bottom: 15px;
            font-family: 'Courier New', monospace;
            text-align: center;
        }
        
        .copy-text {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(0, 255, 0, 0.3);
            border-radius: 5px;
            padding: 15px;
            margin-bottom: 15px;
            color: #ff0;
            font-size: 1.1rem;
            font-family: monospace;
            word-break: break-all;
            text-align: center;
            min-height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
        }
        
        .copy-text:hover {
            background: rgba(0, 20, 0, 0.5);
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.3);
        }
        
        .copy-text::after {
            content: 'کلیک کنید تا کپی شود';
            position: absolute;
            bottom: 5px;
            right: 5px;
            font-size: 0.7rem;
            color: #0f0;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .copy-text:hover::after {
            opacity: 1;
        }
        
        .copy-btn {
            display: block;
            width: 100%;
            padding: 12px;
            background: linear-gradient(to right, #5a189a, #3c096c);
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
            font-family: 'Courier New', monospace;
            box-shadow: 0 5px 15px rgba(138, 43, 226, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .copy-btn:hover {
            background: linear-gradient(to right, #7b2cbf, #5a189a);
            box-shadow: 0 8px 20px rgba(138, 43, 226, 0.6);
            transform: translateY(-3px);
        }
        
        .copy-btn i {
            margin-left: 8px;
        }
        
        /* WhatsApp Queen Card - Terminal Style */
        .whatsapp-queen-card {
            background: rgba(0, 15, 0, 0.4);
            border-radius: 5px;
            padding: 25px;
            transition: all 0.4s;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(0, 255, 0, 0.3);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(5px);
            cursor: pointer;
            display: block;
            text-decoration: none;
        }
        
        .whatsapp-queen-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 255, 0, 0.4);
            border-color: rgba(0, 255, 255, 0.5);
        }
        
        .whatsapp-queen-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 0, 0.1), transparent);
            transition: 0.5s;
            z-index: 1;
        }
        
        .whatsapp-queen-card:hover::before {
            transform: rotate(180deg);
        }
        
        .whatsapp-queen-content {
            position: relative;
            z-index: 2;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }
        
        .whatsapp-queen-card i {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: #25D366;
            filter: drop-shadow(0 0 5px rgba(37, 211, 102, 0.7));
        }
        
        .whatsapp-queen-card h3 {
            color: #0f0;
            margin-bottom: 15px;
            font-family: 'Courier New', monospace;
            font-size: 1.5rem;
            text-shadow: 0 0 5px #0f0;
        }
        
        .whatsapp-queen-card p {
            color: #0ff;
            font-size: 1.1rem;
            font-family: 'Courier New', monospace;
            margin-top: 10px;
        }
        
        /* Terminal-style Creator Section */
        .terminal {
            background: rgba(0, 5, 0, 0.3);
            border: 2px solid rgba(0, 255, 0, 0.3);
            border-radius: 5px;
            padding: 20px;
            margin: 30px 0;
            font-family: monospace;
            color: #0f0;
            box-shadow: 0 0 30px rgba(0, 255, 0, 0.3);
            overflow: hidden;
            position: relative;
            backdrop-filter: blur(5px);
        }
        
        .terminal-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid rgba(0, 255, 0, 0.3);
        }
        
        .terminal-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            margin-left: 5px;
        }
        
        .dot-red { background-color: #ff5f56; }
        .dot-yellow { background-color: #ffbd2e; }
        .dot-green { background-color: #27c93f; }
        
        .terminal-title {
            flex-grow: 1;
            text-align: center;
            font-size: 0.9rem;
            color: #0f0;
        }
        
        .terminal-content {
            line-height: 1.6;
        }
        
        .terminal-prompt {
            color: #0ff;
        }
        
        .terminal-command {
            color: #ff0;
        }
        
        .terminal-output {
            color: #0f0;
            margin-top: 10px;
        }
        
        .terminal-cursor {
            display: inline-block;
            width: 8px;
            height: 16px;
            background-color: #0f0;
            margin-left: 2px;
            animation: blink 1s infinite;
        }
        
        /* Footer */
        footer {
            text-align: center;
            margin-top: 50px;
            padding: 30px;
            border-top: 1px solid rgba(0, 255, 0, 0.3);
            font-size: 1rem;
            background: rgba(0, 10, 0, 0.3);
            border-radius: 5px;
            backdrop-filter: blur(5px);
        }
        
        .copyright {
            color: #0f0;
            margin-bottom: 15px;
            font-family: 'Courier New', monospace;
            animation: float 4s infinite ease-in-out;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 15px;
        }
        
        .social-links a {
            color: #0ff;
            font-size: 1.5rem;
            transition: all 0.3s;
            animation: float 3s infinite ease-in-out;
        }
        
        .social-links a:hover {
            color: #ff0;
            transform: scale(1.2);
        }
        
        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            background: rgba(0, 15, 0, 0.9);
            color: #0f0;
            border: 1px solid #0f0;
            border-radius: 5px;
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.5);
            font-family: 'Courier New', monospace;
            z-index: 1000;
            transform: translateX(200%);
            transition: transform 0.5s ease;
            backdrop-filter: blur(5px);
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.success {
            background: rgba(0, 15, 0, 0.9);
            color: #0f0;
            border-color: #0f0;
        }
        
        .notification.error {
            background: rgba(15, 0, 0, 0.9);
            color: #f00;
            border-color: #f00;
        }
        
        /* Animations */
        @keyframes flicker {
            0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
                text-shadow: 
                    0 0 10px #0f0,
                    0 0 20px #0f0,
                    0 0 30px #0f0,
                    0 0 40px #0f0;
                opacity: 1;
            }
            20%, 24%, 55% {
                opacity: 0.6;
                text-shadow: none;
            }
        }
        
        @keyframes rainbow {
            0% { color: #ff0000; text-shadow: 0 0 10px #ff0000; }
            14% { color: #ff7700; text-shadow: 0 0 10px #ff7700; }
            28% { color: #ffff00; text-shadow: 0 0 10px #ffff00; }
            42% { color: #00ff00; text-shadow: 0 0 10px #00ff00; }
            57% { color: #0000ff; text-shadow: 0 0 10px #0000ff; }
            71% { color: #8a2be2; text-shadow: 0 0 10px #8a2be2; }
            85% { color: #ff00ff; text-shadow: 0 0 10px #ff00ff; }
            100% { color: #ff0000; text-shadow: 0 0 10px #ff0000; }
        }
        
        @keyframes glow {
            0% { 
                color: #0ff;
                text-shadow: 0 0 5px #0ff;
            }
            50% { 
                color: #ff0;
                text-shadow: 0 0 20px #ff0;
            }
            100% { 
                color: #f0f;
                text-shadow: 0 0 10px #f0f;
            }
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink {
            50% { border-color: transparent }
        }
        
        @keyframes pulse {
            0% { 
                transform: scale(1); 
                text-shadow: 0 0 5px #0f0;
            }
            50% { 
                transform: scale(1.05); 
                text-shadow: 0 0 20px #0f0, 0 0 30px #0f0;
            }
            100% { 
                transform: scale(1); 
                text-shadow: 0 0 5px #0f0;
            }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        @keyframes scanline {
            0% {
                transform: translateY(-100%);
            }
            100% {
                transform: translateY(calc(100% + 5px));
            }
        }
    </style>
</head>
<body>
    <div class="terminal-bg"></div>
    <div id="notification" class="notification">متن با موفقیت کپی شد!</div>
    
    <div class="container">
        <header>
            <div class="title-container">
                <h1 class="main-title">TERMUX HACKER TERMINAL</h1>
                <h2 class="sub-title">سیستم گزارش حرفه‌ای واتساپ</h2>
                <p class="hacker-quote">هک برای عدالت - گزارش سوءاستفاده برای حفاظت از بی‌گناهان</p>
                <div class="terminal-strip"></div>
            </div>
        </header>
        
        <div class="form-container">
            <div class="report-section">
                <h2 class="section-title">گزارش رفع انسداد</h2>
                <div class="form-group">
                    <label for="unblockNumber">شماره واتساپ جهت رفع انسداد:</label>
                    <input type="text" id="unblockNumber" placeholder="مثال: 93795247500+" maxlength="20">
                </div>
                <div class="form-group">
                    <label for="unblockReason">علت درخواست رفع انسداد:</label>
                    <textarea id="unblockReason" rows="3" placeholder="علت انسداد حساب خود را شرح دهید..."></textarea>
                </div>
                <div class="btn-group">
                    <button class="btn-generate" onclick="generateUnblockReport()">
                        <i class="fas fa-lock-open"></i> ایجاد گزارش رفع انسداد
                    </button>
                </div>
            </div>
            
            <div class="report-section">
                <h2 class="section-title">گزارش بن کردن</h2>
                <div class="form-group">
                    <label for="banNumber">شماره واتساپ جهت بن کردن:</label>
                    <input type="text" id="banNumber" placeholder="مثال: 93795247500+" maxlength="20">
                </div>
                <div class="form-group">
                    <label for="banReason">علت درخواست بن کردن:</label>
                    <select id="banReason">
                        <option value="harassment">آزار و اذیت جنسی</option>
                        <option value="spam">ارسال اسپم و تبلیغات</option>
                        <option value="scam">کلاهبرداری اینترنتی</option>
                        <option value="threat">تهدید و ارعاب</option>
                        <option value="other">سایر موارد</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="banDetails">جزئیات بیشتر:</label>
                    <textarea id="banDetails" rows="3" placeholder="جزئیات سوءاستفاده را شرح دهید..."></textarea>
                </div>
                <div class="btn-group">
                    <button class="btn-contact" onclick="generateBanReport()">
                        <i class="fas fa-ban"></i> ایجاد گزارش بن کاربر
                    </button>
                </div>
            </div>
        </div>
        
        <div class="contact-section">
            <h2 class="contact-title">رفع انسداد مستقیم و آسان</h2>
            <p class="contact-info">برای ارتباط مستقیم با تیم پشتیبانی واتساپ، در جیمیل روی لینک زیر کلیک کنید:</p>
            
            <div class="contact-links">
                <a href="mailto:support@support.whatsapp.com,android@support.whatsapp.com?subject=Re: 2188416704954602&body=--Support Info--
Debug info: unregistered
Device ID: 0
Description: 2.23.21.88
Version: 2.23.21.88
App: com.whatsapp
MDEnabled: false
HasMdCompanion: false
LC: EG
LG: ar
Context: verify-bp +93
Carrier: etisalat by e&
Manufacturer: Xiaomi
Model: 22101316UG
useragent: WhatsApp/2.23.21.88 Android/14 Device/Xiaomi-22101316UG
CPU ABI: arm64-v8a
OS: 14
Socket Conn: DN
Radio MCC-MNC: 602-03
SIM MCC-MNC: 602-03
Free Space Built-In: 110055321600 (110 غ.ب)
Free Space Removable: mounted
FAQ Results Returned: 10
FAQ Results Read: 0
Smb count: 0
Ent count: 0
CCode: +93
Target: release
Product: rubypro_global
Device: rubypro
Build: UP1A.231005.007
Board: rubypro
Kernel: Unknown release unknown version
Connection: W.I.F.I.
Device ISO8601: 2024-02-24 12: 52: 42.705+0200
Phone Type: G.S.M.
Network Type: U.N.K.N.O.W.N.
Missing Permissions: android.permission.ACCESS_COARSE_LOCATION, android.permission.ACCESS_FINE_LOCATION, android.permission.READ_PHONE_STATE, android.permission.READ_PHONE_NUMBERS, android.permission.RECEIVE_SMS, android.permission.SYSTEM_ALERT_WINDOW, android.permission.GET_ACCOUNTS, android.permission.CAMERA, android.permission.INSTALL_SHORTCUT, android.permission.READ_CONTACTS, android.permission.RECORD_AUDIO, android.permission.SCHEDULE_EXACT_ALARM, android.permission.SEND_SMS, android.permission.WRITE_CONTACTS, android.permission.WRITE_EXTERNAL_STORAGE, android.permission.REQUEST_INSTALL_PACKAGES, com.sec.android.provider.badge.permission.READ, com.sec.android.provider.badge.permission.WRITE, com.htc.launcher.permission.READ_SETTINGS, com.htc.launcher.permission.UPDATE_SHORTCUT, com.sonyericsson.home.permission.BROADCAST_BADGE, com.sonymobile.home.permission.PROVIDER_INSERT_BADGE, com.huawei.android.launcher.permission.READ_SETTINGS, com.huawei.android.launcher.permission.WRITE_SETTINGS, com.huawei.android.launcher.permission.CHANGE_BADGE, android.permission.CALL_PHONE, android.permission.ANSWER_PHONE_CALLS, android.permission.READ_CALL_LOG, android.permission.READ_EXTERNAL_STORAGE, android.permission.POST_NOTIFICATIONS, android.permission.READ_MEDIA_AUDIO, android.permission.READ_MEDIA_VIDEO, android.permission.READ_MEDIA_IMAGES, android.permission.READ_MEDIA_VISUAL_USER_SELECTED
Architecture: aarch64
Diagnostic Codes: FE-GDE FE-GDC FE-VIDC
Sim: null 5
Network metered: 107: false; 113: false
Network restricted: 107: true; 113: false
AutoConf status: null
Data roaming: false
Tel roaming: false
ABprops hash state: unregistered
Serverprops hash state: unregistered
Video transcode: supported
anid: a4c9aa1d-4890-409d-9d11-eef08a0e93f6
XPMigrated: no
Screen reader: false
Fingerprint eligible: true
Last local backup time: never
Google account added: false
Groups media visibility: default
  Individual media visibility: default
  In scoped mode: true
  Has unexpected .nomedia: false
  Is Tablet: false
  Is Foldable: false
 " class="contact-link">
                    <i class="fas fa-headset"></i> رفع انسداد شماره ابتدایی
                </a>
                
                <a href="mailto:support@support.whatsapp.com,android@support.whatsapp.com?subject=Request for Review and Unblocking of My WhatsApp Number&body=Dear WhatsApp Support Team,

I hope this message finds you well.

My WhatsApp number *+93796868704* has been unexpectedly blocked. I believe this may have happened by mistake, as I am aware of WhatsApp’s terms of use and have always tried to follow them responsibly.

I kindly request you to review my case and, if possible, unblock my number.
So far, I have not been able to resolve the issue, and my access remains restricted.

Thank you very much for your time and support.
 " class="contact-link ban">
                    <i class="fas fa-ban"></i> در پاسخ ایمیل پشتیبانی
                </a>
            </div>
        </div>
        
        <!-- Platforms Section - Modern Design -->
        <div class="platforms-section">
            <h2 class="section-title">ارتباط با ما از طریق پلتفرم‌های دیگر</h2>
            <p class="contact-info">برای ارتباط با ما از طریق پلتفرم‌های مختلف، از لینک‌های زیر استفاده کنید:</p>
            
            <div class="platforms-grid">
                <div class="platform-card">
                    <div class="platform-card-content">
                        <i class="fab fa-youtube"></i>
                        <h3>کانال یوتیوب</h3>
                        <a href="https://www.youtube.com/@user-rahmat.afghan" target="_blank">youtube.com/@user-rahmat.afghan</a>
                    </div>
                </div>
                
                <div class="platform-card">
                    <div class="platform-card-content">
                        <i class="fab fa-whatsapp"></i>
                        <h3>تماس در واتساپ</h3>
                        <a href="https://wa.me/93795247500" target="_blank">+93795247500</a>
                    </div>
                </div>
                
                <div class="platform-card">
                    <div class="platform-card-content">
                        <i class="fas fa-globe"></i>
                        <h3>وب سایت رسمی</h3>
                        <a href="https://hackerafghanwebsites.blogspot.com/2025/01/blog-post.html?m=1" target="_blank">hackerafghanwebsites.blogspot.com</a>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Copy Text Section - Modern Design -->
        <div class="copy-section">
            <h2 class="copy-section-title">کپی متن‌های ویژه با یک کلیک</h2>
            <p class="contact-info" style="text-align: center; margin-bottom: 25px;">روی هر متن کلیک کنید تا به طور خودکار کپی شود</p>
            
            <div class="copy-container">
                <div class="copy-item">
                    <h3 class="copy-item-title">متن ویژه ریپورترها 1</h3>
                    <div class="copy-text" onclick="copyText('text1')" id="text1">Hello failed WhatsApp users.I am a businessman who has two companies specialized in hacking WhatsApp servers .I hack the devices of WhatsApp users and spy on them and display their information on the deep web.I also publish pornographic videos of girls I kidnapped under the age of 3 years.
https://www.xnxx.com/video-14d74b9c/die
https://www.xnxx.com/video-14d74b9c/die
 If I want to hack someone's WhatsApp for you, it will cost you$ 100, I will hack all WhatsApp user accounts, and I have collaborated with Mark Zuckerberg. I invite you to join me and work with me otherwise I will hack your WhatsApp and kidnap your daughter and your wife and kill them in front of your eyes and then kill you. What are you waiting for contact me via my WhatsApp account 
https://api.whatsapp.com/send?phone=+93</div>
                    <button class="copy-btn" onclick="copyText('text1')">
                        <i class="fas fa-copy"></i> کپی متن ویژه 1
                    </button>
                </div>
                
                <div class="copy-item">
                    <h3 class="copy-item-title">متن ویژه ریپورترها 2</h3>
                    <div class="copy-text" onclick="copyText('text2')" id="text2">Здравствуйте, уважаемый пользователь WhatsApp, вы ищете работу? 🤜🤛🌟
Есть работа, которая позволит вам зарабатывать ежемесячную сумму от 100 000 до 9 000 000 долларов. Вот условия:

1. Вам должно быть от 30 до 55 лет. Вы должны отправить нам свои личные файлы, такие как кредитная карта, удостоверение личности и личное фото, чтобы подтвердить, что вы не робот.


2. Отправьте информацию администратору и наш адрес электронной почты здесь:
android@support.whatsapp.com
https://api.whatsapp.com/send?phone=+93
</div>
                    <button class="copy-btn" onclick="copyText('text2')">
                        <i class="fas fa-copy"></i> کپی متن ویژه 2
                    </button>
                </div>
                
                <div class="copy-item">
                    <h3 class="copy-item-title">متن ویژه ریپورترها 3</h3>
                    <div class="copy-text" onclick="copyText('text3')" id="text3">حذف حساب

Здравствуйте, я работаю в WhatsApp бизнесе, я продаю, покупаю и торгую через приложение WhatsApp, но я хотел бы сообщить вам, что я больше не хочу использовать WhatsApp, потому что некоторые пользователи отправляют раздражающие и неконтролируемые сообщения, и я сообщаю о них, и мой номер телефона всегда заблокирован, и я больше не хочу использовать WhatsApp по этой причине
</div>
                    <button class="copy-btn" onclick="copyText('text3')">
                        <i class="fas fa-copy"></i> کپی متن ویژه 3
                    </button>
                </div>
                
                <!-- WhatsApp Queen Card - Fixed and Enhanced -->
                <a href="https://www.hawhats.com/2023/06/blog-post_29.html" target="_blank" class="whatsapp-queen-card">
                    <div class="whatsapp-queen-content">
                        <i class="fab fa-whatsapp"></i>
                        <h3>واتساپ ملکه</h3>
                        <p>کلیک کنید برای باز کردن لینک</p>
                    </div>
                </a>
            </div>
        </div>
        
        <!-- Terminal-style Creator Section -->
        <div class="terminal">
            <div class="terminal-header">
                <div class="terminal-dot dot-red"></div>
                <div class="terminal-dot dot-yellow"></div>
                <div class="terminal-dot dot-green"></div>
                <div class="terminal-title">root@hacker-afg:~</div>
            </div>
            <div class="terminal-content">
                <div><span class="terminal-prompt">root@hacker-afg</span>:<span class="terminal-command">~# whoami</span></div>
                <div class="terminal-output">TERMUX HACKER - Professional System</div>
                
                <div><span class="terminal-prompt">root@hacker-afg</span>:<span class="terminal-command">~# system --status</span></div>
                <div class="terminal-output">
                    <p>وضعیت سیستم: <span style="color: #0ff;">فعال</span></p>
                    <p>گزارش‌های امروز: <span style="color: #ff0;">27 گزارش</span></p>
                    <p>آخرین به‌روزرسانی: <span style="color: #0f0;">امروز 14:35</span></p>
                </div>
                
                <div><span class="terminal-prompt">root@hacker-afg</span>:<span class="terminal-command">~# </span><span class="terminal-cursor"></span></div>
            </div>
        </div>
        
        <footer>
            <p class="copyright">© 2023 TERMUX HACKER | سیستم گزارش حرفه‌ای واتساپ</p>
            <p>تمامی حقوق برای تیم توسعه ترمینال ترمیکس محفوظ است</p>
            
            <div class="social-links">
                <a href="#"><i class="fab fa-telegram"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-github"></i></a>
                <a href="#"><i class="fab fa-youtube"></i></a>
            </div>
        </footer>
    </div>

    <script>
        // Report Generation Functions
        function generateUnblockReport() {
            const number = document.getElementById('unblockNumber').value;
            const reason = document.getElementById('unblockReason').value;
            
            if (!number) {
                showNotification('لطفاً شماره واتساپ را وارد کنید!', 'error');
                return;
            }
            
            // Set email subject and body
            const subject = 'Urgent Report – Unblock Request';
            const body = `Hello WhatsApp Support Team,

I am writing to request unblocking my WhatsApp account with the number: ${number}.

Reason for unblocking:
${reason || 'No additional details provided'}

I confirm that I have not violated any of WhatsApp's terms of service.

Thank you for your urgent attention to this matter.

Sincerely,
[Your Name]`;

            // Prepare email
            const emailRecipients = [
                'support@support.whatsapp.com',
                'android@support.whatsapp.com'
            ].join(',');

            const mailtoLink = `mailto:${emailRecipients}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            
            // Open email client
            window.location.href = mailtoLink;
        }
        
        function generateBanReport() {
            const number = document.getElementById('banNumber').value;
            const reason = document.getElementById('banReason').value;
            const details = document.getElementById('banDetails').value;
            
            if (!number) {
                showNotification('لطفاً شماره واتساپ را وارد کنید!', 'error');
                return;
            }
            
            const reasons = {
                harassment: 'Sexual harassment',
                spam: 'Spam and advertisements',
                scam: 'Internet fraud',
                threat: 'Threats and intimidation',
                other: 'Other abuses'
            };
            
            // Set email subject and body
            const subject = 'Urgent Report – Ban Request';
            const body = `Hello WhatsApp Support Team,

I am writing to request banning a WhatsApp user with the number: ${number}.

Type of abuse: ${reasons[reason]}
Additional details: 
${details || 'No additional details provided'}

This user has been violating WhatsApp's terms of service.

I request the immediate blocking and permanent ban of this number: ${number}.

Thank you for your urgent attention to this matter.

Sincerely,
[Your Name]`;

            // Prepare email
            const emailRecipients = [
                'support@support.whatsapp.com',
                'android@support.whatsapp.com'
            ].join(',');

            const mailtoLink = `mailto:${emailRecipients}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            
            // Open email client
            window.location.href = mailtoLink;
        }
        
        // Enhanced Copy Text Functionality
        function copyText(elementId) {
            const textElement = document.getElementById(elementId);
            const text = textElement.innerText;
            
            navigator.clipboard.writeText(text)
                .then(() => {
                    showNotification('متن با موفقیت کپی شد!', 'success');
                    
                    // Visual feedback for the copied text
                    textElement.style.background = 'rgba(0, 50, 0, 0.7)';
                    textElement.style.boxShadow = '0 0 15px rgba(0, 255, 0, 0.5)';
                    
                    setTimeout(() => {
                        textElement.style.background = 'rgba(0, 0, 0, 0.3)';
                        textElement.style.boxShadow = 'none';
                    }, 1000);
                })
                .catch(err => {
                    showNotification('خطا در کپی کردن متن', 'error');
                    console.error('Could not copy text: ', err);
                });
        }
        
        function showNotification(message, type) {
            const notification = document.getElementById('notification');
            notification.innerText = message;
            notification.className = 'notification'; // Reset classes
            notification.classList.add(type);
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        // Initialize copy text elements
        document.addEventListener('DOMContentLoaded', function() {
            const copyTexts = document.querySelectorAll('.copy-text');
            copyTexts.forEach(text => {
                text.addEventListener('click', function() {
                    const elementId = this.id;
                    copyText(elementId);
                });
            });
            
            // Animated terminal cursor
            setInterval(() => {
                const cursor = document.querySelector('.terminal-cursor');
                cursor.style.opacity = cursor.style.opacity === '0' ? '1' : '0';
            }, 500);
        });
    </script>
</body>
</html>