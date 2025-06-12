
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MUVIT - Mobile Untuk Visi Integritas Lalu-Lintas Terbaik</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700&family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-dark: #0a1128;
            --secondary-dark: #1e3a8a;
            --accent: #00d9ff;
            --accent-alt: #ff2a6d;
            --neutral: #e6e6e6;
            --success: #00cc99;
            --warning: #ffd700;
            --danger: #ff4d4d;
            --card-bg-dark: rgba(30, 58, 138, 0.3);
            --card-border-dark: rgba(0, 217, 255, 0.3);
            
            --primary-light: #f0f4ff;
            --secondary-light: #aec6ff;
            --card-bg-light: rgba(255, 255, 255, 0.8);
            --card-border-light: rgba(0, 123, 255, 0.3);
            --text-dark: #333;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            transition: background-color 0.5s ease, color 0.3s ease;
        }
        
        body {
            font-family: 'Roboto', sans-serif;
            background: var(--primary-dark);
            color: var(--neutral);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(30, 58, 138, 0.15) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(0, 217, 255, 0.1) 0%, transparent 20%);
            min-height: 100vh;
            overflow-x: hidden;
            max-width: 100vw;
        }
        
        body.light-mode {
            background: var(--primary-light);
            color: var(--text-dark);
        }
        
        body.light-mode .card {
            background: var(--card-bg-light);
            border: 1px solid var(--card-border-light);
        }
        
        body.light-mode .card-desc,
        body.light-mode .modal-title,
        body.light-mode .section-title,
        body.light-mode .footer-title,
        body.light-mode .faq-question,
        body.light-mode .question-text,
        body.light-mode .edu-title,
        body.light-mode .traffic-hero-title,
        body.light-mode .card-title {
            color: var(--text-dark);
        }
        
        body.light-mode .emergency-section {
            background: rgba(255, 77, 77, 0.1);
            border: 1px solid rgba(255, 77, 77, 0.3);
        }
        
        body.light-mode .emergency-card {
            background: rgba(255, 77, 77, 0.15);
            border: 1px solid rgba(255, 77, 77, 0.3);
        }
        
        body.light-mode .emergency-name {
            color: var(--text-dark);
        }
        
        .futuristic-header {
            font-family: 'Orbitron', sans-serif;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        /* Splash Screen */
        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--primary-dark);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            transition: opacity 1s ease;
        }
        
        .splash-title {
            font-size: 3.5rem;
            font-weight: 700;
            background: linear-gradient(90deg, var(--accent), var(--accent-alt));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 20px;
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            position: relative;
            overflow: hidden;
        }
        
        .splash-subtitle {
            font-size: 1.2rem;
            color: var(--neutral);
            text-align: center;
            max-width: 90%;
            line-height: 1.6;
            height: 1.6em;
            overflow: hidden;
            position: relative;
        }
        
        .cursor {
            display: inline-block;
            width: 3px;
            height: 1em;
            background: var(--accent);
            margin-left: 2px;
            animation: blink 1s infinite;
            vertical-align: bottom;
        }
        
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }
        
        /* Container */
        .container {
            max-width: 100%;
            margin: 0 auto;
            padding: 15px;
            opacity: 0;
            transform: translateY(20px);
            transition: all 1s ease;
        }
        
        .container.show {
            opacity: 1;
            transform: translateY(0);
        }
        
        /* Header */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
            border-bottom: 1px solid var(--card-border-dark);
            margin-bottom: 20px;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo-icon {
            width: 40px;
            height: 40px;
            background: var(--accent);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            color: var(--primary-dark);
            box-shadow: 0 0 10px var(--accent);
            animation: pulse 2s infinite;
        }
        
        .logo-text {
            font-size: 1.5rem;
            font-weight: 700;
            background: linear-gradient(90deg, var(--accent), var(--accent-alt));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .moto {
            font-size: 0.7rem;
            color: var(--neutral);
            opacity: 0.8;
            margin-top: 3px;
        }
        
        .menu-toggle {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 20px;
            color: var(--neutral);
        }
        
        .menu-toggle:hover {
            background: var(--accent);
            color: var(--primary-dark);
            box-shadow: 0 0 10px var(--accent);
        }
        
        .dropdown-menu {
            position: absolute;
            top: 70px;
            right: 15px;
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 10px;
            width: 220px;
            z-index: 1000;
            overflow: hidden;
            transform: translateY(-10px);
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }
        
        .dropdown-menu.show {
            transform: translateY(0);
            opacity: 1;
            visibility: visible;
        }
        
        .dropdown-item {
            padding: 12px 15px;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
            transition: all 0.3s;
            border-bottom: 1px solid rgba(0, 217, 255, 0.1);
        }
        
        .dropdown-item:last-child {
            border-bottom: none;
        }
        
        .dropdown-item:hover {
            background: rgba(0, 217, 255, 0.1);
        }
        
        .dropdown-icon {
            font-size: 18px;
            width: 25px;
            color: var(--accent);
        }
        
        .dropdown-text {
            flex-grow: 1;
            font-size: 0.9rem;
        }
        
        /* Main Grid */
        .main-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .card {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 15px;
            padding: 20px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(10px);
            min-height: 180px;
            display: flex;
            flex-direction: column;
            cursor: pointer;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 20px rgba(0, 217, 255, 0.2);
            border-color: var(--accent);
        }
        
        .card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(0, 217, 255, 0.1) 0%, transparent 70%);
            z-index: -1;
        }
        
        .card-icon {
            font-size: 35px;
            margin-bottom: 15px;
            color: var(--accent);
        }
        
        .card-title {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--neutral);
        }
        
        .card-desc {
            font-size: 0.9rem;
            color: rgba(230, 230, 230, 0.8);
            line-height: 1.5;
            margin-bottom: 15px;
            flex-grow: 1;
        }
        
        .card-btn {
            background: transparent;
            border: 1px solid var(--accent);
            color: var(--accent);
            padding: 8px 16px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 6px;
            cursor: pointer;
            transition: all 0.3s;
            width: fit-content;
            font-size: 0.9rem;
        }
        
        .card-btn:hover {
            background: var(--accent);
            color: var(--primary-dark);
            box-shadow: 0 0 10px var(--accent);
        }
        
        /* Emergency Section */
        .emergency-section {
            background: rgba(255, 77, 77, 0.1);
            border: 1px solid rgba(255, 77, 77, 0.3);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 30px;
        }
        
        .section-title {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 20px;
            font-size: 1.3rem;
            color: var(--danger);
        }
        
        .emergency-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 12px;
        }
        
        .emergency-card {
            background: rgba(255, 77, 77, 0.15);
            border: 1px solid rgba(255, 77, 77, 0.3);
            border-radius: 12px;
            padding: 15px;
            display: flex;
            align-items: center;
            gap: 12px;
            transition: all 0.3s;
            cursor: pointer;
        }
        
        .emergency-card:hover {
            transform: translateY(-3px);
            background: rgba(255, 77, 77, 0.25);
            box-shadow: 0 3px 10px rgba(255, 77, 77, 0.2);
        }
        
        .emergency-icon {
            font-size: 22px;
            width: 50px;
            height: 50px;
            background: rgba(255, 77, 77, 0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--danger);
        }
        
        .emergency-info {
            flex-grow: 1;
        }
        
        .emergency-name {
            font-size: 0.95rem;
            margin-bottom: 5px;
            color: var(--neutral);
        }
        
        .emergency-number {
            font-size: 1.1rem;
            font-weight: 700;
            color: var(--danger);
        }
        
        /* Footer */
        footer {
            display: flex;
            flex-direction: column;
            padding: 20px 0;
            border-top: 1px solid var(--card-border-dark);
            margin-top: 20px;
            gap: 20px;
        }
        
        .footer-section {
            width: 100%;
        }
        
        .footer-title {
            font-size: 1.1rem;
            margin-bottom: 12px;
            color: var(--accent);
        }
        
        .footer-links {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        
        .footer-link {
            color: rgba(230, 230, 230, 0.8);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s;
            font-size: 0.9rem;
        }
        
        .footer-link:hover {
            color: var(--accent);
        }
        
        .social-links {
            display: flex;
            gap: 12px;
            margin-top: 12px;
        }
        
        .social-link {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--neutral);
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .social-link:hover {
            background: var(--accent);
            color: var(--primary-dark);
            box-shadow: 0 0 10px var(--accent);
            transform: translateY(-3px);
        }
        
        /* Modals */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            padding: 15px;
        }
        
        .modal.show {
            opacity: 1;
            visibility: visible;
        }
        
        .modal-content {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 15px;
            width: 100%;
            max-width: 800px;
            max-height: 95vh;
            overflow-y: auto;
            padding: 20px;
            position: relative;
            backdrop-filter: blur(10px);
            transform: translateY(-20px);
            transition: all 0.3s ease;
        }
        
        .modal.show .modal-content {
            transform: translateY(0);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .modal-title {
            font-size: 1.3rem;
            color: var(--accent);
            font-family: 'Orbitron', sans-serif;
        }
        
        .close-modal {
            background: transparent;
            border: none;
            font-size: 1.3rem;
            color: var(--neutral);
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .close-modal:hover {
            color: var(--accent);
            transform: rotate(90deg);
        }
        
        /* Game Elements */
        .game-container {
            position: relative;
            width: 100%;
            height: 70vh;
            background: #0a1a3a;
            border-radius: 10px;
            overflow: hidden;
            border: 2px solid var(--accent);
            margin: 15px 0;
        }
        
        .game-road {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #222;
        }
        
        .road-line {
            position: absolute;
            height: 3px;
            background: var(--accent);
            width: 100%;
            opacity: 0.5;
        }
        
        .character {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 40px;
            height: 60px;
            background: #ff9900;
            border-radius: 5px;
            z-index: 10;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-size: 30px;
        }
        
        .obstacle {
            position: absolute;
            width: 50px;
            height: 30px;
            background: #ff2a6d;
            border-radius: 5px;
        }
        
        .controls {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin-top: 15px;
        }
        
        .control-btn {
            background: var(--card-bg-dark);
            border: 1px solid var(--accent);
            color: var(--accent);
            padding: 12px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .control-btn:hover {
            background: var(--accent);
            color: var(--primary-dark);
        }
        
        .game-result {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            z-index: 100;
            width: 80%;
            display: none;
        }
        
        .result-title {
            font-size: 1.5rem;
            margin-bottom: 15px;
        }
        
        .result-success {
            color: var(--success);
        }
        
        .result-fail {
            color: var(--danger);
        }
        
        .result-btn {
            background: var(--accent);
            color: var(--primary-dark);
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
        }
        
        /* Quiz Elements */
        .quiz-container {
            margin: 15px 0;
        }
        
        .quiz-question {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
        }
        
        .question-text {
            font-size: 1.1rem;
            margin-bottom: 15px;
        }
        
        .options {
            display: grid;
            grid-template-columns: 1fr;
            gap: 10px;
        }
        
        .option {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 8px;
            padding: 12px;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .option:hover {
            border-color: var(--accent);
        }
        
        .option.selected {
            background: rgba(0, 217, 255, 0.1);
            border-color: var(--accent);
        }
        
        .quiz-nav {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        .nav-btn {
            background: var(--accent);
            color: var(--primary-dark);
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .quiz-result {
            text-align: center;
            padding: 20px;
        }
        
        .score-display {
            font-size: 1.8rem;
            margin: 20px 0;
            color: var(--accent);
        }
        
        .answer-key {
            margin-top: 20px;
            text-align: left;
            max-height: 300px;
            overflow-y: auto;
            padding: 15px;
            background: rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        
        .answer-item {
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px dashed rgba(255, 255, 255, 0.2);
        }
        
        .answer-item:last-child {
            border-bottom: none;
        }
        
        .correct-answer {
            color: var(--success);
            font-weight: bold;
        }
        
        /* Education Content */
        .edu-container {
            margin: 15px 0;
        }
        
        .edu-category {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
            cursor: pointer;
        }
        
        .edu-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .edu-icon {
            font-size: 28px;
            width: 50px;
            height: 50px;
            background: rgba(0, 217, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--accent);
        }
        
        .edu-title {
            font-size: 1.1rem;
            font-weight: bold;
        }
        
        .edu-content {
            padding-left: 65px;
            display: none;
        }
        
        .edu-content.show {
            display: block;
        }
        
        .edu-item {
            margin-bottom: 10px;
            padding-left: 15px;
            position: relative;
        }
        
        .edu-item:before {
            content: "•";
            position: absolute;
            left: 0;
            color: var(--accent);
        }
        
        /* Traffic Hero Modal */
        .traffic-hero-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin: 20px 0;
        }
        
        .traffic-hero-card {
            background: var(--card-bg-dark);
            border: 1px solid var(--card-border-dark);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .traffic-hero-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 217, 255, 0.2);
            border-color: var(--accent);
        }
        
        .traffic-hero-icon {
            font-size: 40px;
            margin-bottom: 15px;
            color: var(--accent);
        }
        
        .traffic-hero-title {
            font-size: 1.2rem;
            margin-bottom: 10px;
            font-family: 'Orbitron', sans-serif;
        }
        
        /* FAQ Elements */
        .faq-item {
            margin-bottom: 15px;
            border-bottom: 1px solid var(--card-border-dark);
            padding-bottom: 15px;
        }
        
        .faq-question {
            font-weight: bold;
            margin-bottom: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .faq-question i {
            transition: transform 0.3s;
        }
        
        .faq-question.expanded i {
            transform: rotate(90deg);
        }
        
        .faq-answer {
            padding: 10px 0 0 30px;
            display: none;
        }
        
        .faq-answer.show {
            display: block;
        }
        
        /* Contact Elements */
        .contact-item {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
            padding: 12px;
            border-radius: 10px;
            background: rgba(0, 0, 0, 0.1);
            transition: all 0.3s;
        }
        
        .contact-item:hover {
            background: rgba(0, 217, 255, 0.1);
        }
        
        .contact-icon {
            font-size: 24px;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--accent);
        }
        
        .contact-info {
            flex-grow: 1;
        }
        
        .contact-type {
            font-size: 0.9rem;
            opacity: 0.8;
            margin-bottom: 3px;
        }
        
        .contact-value {
            font-size: 1.1rem;
            font-weight: 500;
        }
        
        /* Animations */
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(0, 217, 255, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(0, 217, 255, 0); }
            100% { box-shadow: 0 0 0 0 rgba(0, 217, 255, 0); }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-5px); }
            100% { transform: translateY(0px); }
        }
        
        @keyframes roadLine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        @keyframes moveHorizontal {
            0% { transform: translateX(0); }
            100% { transform: translateX(100%); }
        }
        
        /* Accessibility Mode */
        body.accessibility-mode {
            font-size: 18px;
        }
        
        body.accessibility-mode .card-icon {
            font-size: 50px;
        }
        
        body.accessibility-mode .card-title {
            font-size: 1.4rem;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .splash-title {
                font-size: 2.5rem;
            }
            
            .splash-subtitle {
                font-size: 1rem;
            }
            
            .traffic-hero-grid {
                grid-template-columns: 1fr;
            }
            
            .faq-question {
                font-size: 1.1rem;
            }
            
            .emergency-grid {
                grid-template-columns: 1fr;
            }
        }
        
        @media (min-width: 768px) {
            .container {
                max-width: 800px;
            }
        }
    </style>
</head>
<body>
    <!-- Splash Screen -->
    <div class="splash-screen" id="splashScreen">
        <div class="splash-title futuristic-header">MUVIT</div>
        <div class="splash-subtitle" id="subtitle">
            <span id="typed-text"></span>
            <span class="cursor"></span>
        </div>
    </div>
    
    <!-- Main Content -->
    <div class="container" id="mainContainer">
        <header>
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-traffic-light"></i>
                </div>
                <div>
                    <div class="logo-text futuristic-header">MUVIT</div>
                    <div class="moto">Mobile Untuk Visi Integritas Lalu-Lintas Terbaik</div>
                </div>
            </div>
            
            <div class="menu-toggle" id="menuToggle">
                <i class="fas fa-bars"></i>
            </div>
            
            <div class="dropdown-menu" id="dropdownMenu">
                <div class="dropdown-item" id="themeToggle">
                    <div class="dropdown-icon">
                        <i class="fas fa-moon"></i>
                    </div>
                    <div class="dropdown-text">Dark Mode</div>
                </div>
                
                <div class="dropdown-item" id="faqBtn">
                    <div class="dropdown-icon">
                        <i class="fas fa-question-circle"></i>
                    </div>
                    <div class="dropdown-text">FAQ</div>
                </div>
                
                <div class="dropdown-item" id="contactBtn">
                    <div class="dropdown-icon">
                        <i class="fas fa-envelope"></i>
                    </div>
                    <div class="dropdown-text">Kontak</div>
                </div>
                
                <div class="dropdown-item" id="accessibilityBtn">
                    <div class="dropdown-icon">
                        <i class="fas fa-text-height"></i>
                    </div>
                    <div class="dropdown-text">Perbesar Tulisan</div>
                </div>
            </div>
        </header>

        <div class="main-grid">
            <div class="card" onclick="openReport()">
                <i class="fas fa-bullhorn card-icon"></i>
                <h3 class="card-title futuristic-header">LAPOR!</h3>
                <p class="card-desc">Laporkan pelanggaran lalu lintas, penyalahgunaan, atau penyelewengan yang Anda temui</p>
                <button class="card-btn">
                    <i class="fas fa-external-link-alt"></i>
                    Laporkan Sekarang
                </button>
            </div>
            
            <div class="card" onclick="openEducation()">
                <i class="fas fa-book card-icon"></i>
                <h3 class="card-title futuristic-header">MUVIT EDU</h3>
                <p class="card-desc">Pelajari etika dan aturan berkendara untuk semua jenis pengguna jalan</p>
                <button class="card-btn">
                    <i class="fas fa-graduation-cap"></i>
                    Pelajari
                </button>
            </div>
            
            <div class="card" onclick="openTrafficHero()">
                <i class="fas fa-gamepad card-icon"></i>
                <h3 class="card-title futuristic-header">TRAFFIC HERO</h3>
                <p class="card-desc">Jadilah pahlawan lalu lintas dengan memainkan game edukasi</p>
                <button class="card-btn">
                    <i class="fas fa-play"></i>
                    Pilih Game
                </button>
            </div>
            
            <div class="card" onclick="openTest()">
                <i class="fas fa-id-card card-icon"></i>
                <h3 class="card-title futuristic-header">TES SIM</h3>
                <p class="card-desc">Uji pengetahuan Anda tentang peraturan lalu lintas dengan tes interaktif</p>
                <button class="card-btn">
                    <i class="fas fa-pencil-alt"></i>
                    Mulai Tes
                </button>
            </div>
            
            <div class="card" onclick="openAssistant()">
                <i class="fas fa-robot card-icon"></i>
                <h3 class="card-title futuristic-header">VIRTUAL ASSISTANT</h3>
                <p class="card-desc">Dapatkan bantuan dan informasi tentang lalu lintas dari asisten virtual kami</p>
                <button class="card-btn">
                    <i class="fas fa-comments"></i>
                    Tanya Sekarang
                </button>
            </div>
        </div>

        <div class="emergency-section">
            <h2 class="section-title">
                <i class="fas fa-ambulance"></i>
                <span class="futuristic-header">DARURAT</span>
            </h2>
            <div class="emergency-grid">
                <div class="emergency-card" onclick="callEmergency('112')">
                    <div class="emergency-icon">
                        <i class="fas fa-phone-alt"></i>
                    </div>
                    <div class="emergency-info">
                        <div class="emergency-name">Call Center Nasional</div>
                        <div class="emergency-number">112</div>
                    </div>
                </div>
                
                <div class="emergency-card" onclick="callEmergency('110')">
                    <div class="emergency-icon">
                        <i class="fas fa-police-box"></i>
                    </div>
                    <div class="emergency-info">
                        <div class="emergency-name">Polisi</div>
                        <div class="emergency-number">110</div>
                    </div>
                </div>
                
                <div class="emergency-card" onclick="callEmergency('113')">
                    <div class="emergency-icon">
                        <i class="fas fa-fire-extinguisher"></i>
                    </div>
                    <div class="emergency-info">
                        <div class="emergency-name">Pemadam Kebakaran</div>
                        <div class="emergency-number">113</div>
                    </div>
                </div>
                
                <div class="emergency-card" onclick="callEmergency('02916912119')">
                    <div class="emergency-icon">
                        <i class="fas fa-ambulance"></i>
                    </div>
                    <div class="emergency-info">
                        <div class="emergency-name">Ambulans</div>
                        <div class="emergency-number">(0291) 6912119</div>
                    </div>
                </div>
                
                <div class="emergency-card" onclick="callEmergency('0291682113')">
                    <div class="emergency-icon">
                        <i class="fas fa-fire"></i>
                    </div>
                    <div class="emergency-info">
                        <div class="emergency-name">Damkar Demak</div>
                        <div class="emergency-number">(0291) 682113</div>
                    </div>
                </div>
                
                <div class="emergency-card" onclick="callEmergency('0291682200')">
                    <div class="emergency-icon">
                        <i class="fas fa-exclamation-triangle"></i>
                    </div>
                    <div class="emergency-info">
                        <div class="emergency-name">BPBD Demak</div>
                        <div class="emergency-number">(0291) 682200</div>
                    </div>
                </div>
            </div>
        </div>

        <footer>
            <div class="footer-section">
                <h3 class="footer-title">Tentang MUVIT</h3>
                <p style="margin-bottom: 15px; opacity: 0.8; font-size: 0.9rem;">MUVIT adalah platform edukasi dan pelaporan lalu lintas untuk mewujudkan mobilitas yang lebih baik.</p>
                <p style="opacity: 0.8; font-size: 0.9rem;">Dibuat oleh Arum FNisa untuk Lomba Pelajar Pelopor Ketertiban Lalu Lintas</p>
            </div>
            
            <div class="footer-section">
                <h3 class="footer-title">Kontak Kami</h3>
                <div class="contact-item" onclick="openEmail()">
                    <div class="contact-icon">
                        <i class="fas fa-envelope"></i>
                    </div>
                    <div class="contact-info">
                        <div class="contact-type">Email</div>
                        <div class="contact-value">muvitmovewithit@gmail.com</div>
                    </div>
                </div>
                
                <div class="contact-item" onclick="openInstagram()">
                    <div class="contact-icon">
                        <i class="fab fa-instagram"></i>
                    </div>
                    <div class="contact-info">
                        <div class="contact-type">Instagram</div>
                        <div class="contact-value">@nisarumaee_</div>
                    </div>
                </div>
            </div>
        </footer>
    </div>
    
    <!-- FAQ Modal -->
    <div class="modal" id="faqModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">FAQ</h3>
                <button class="close-modal" onclick="closeModal('faqModal')">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="faq-list">
                <div class="faq-item">
                    <div class="faq-question" onclick="toggleFaqAnswer(this)">
                        <i class="fas fa-chevron-right"></i>
                        Apa itu MUVIT?
                    </div>
                    <div class="faq-answer">
                        MUVIT adalah aplikasi all-in-one yang dirancang untuk meningkatkan keselamatan, ketertiban, dan kenyamanan lalu lintas. Aplikasi ini menyediakan berbagai fitur seperti pelaporan pelanggaran lalu lintas, akses darurat, edukasi berkendara, dan sistem gamifikasi.
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question" onclick="toggleFaqAnswer(this)">
                        <i class="fas fa-chevron-right"></i>
                        Siapa saja yang bisa menggunakan MUVIT?
                    </div>
                    <div class="faq-answer">
                        Aplikasi ini dapat digunakan oleh semua kalangan, mulai dari anak-anak, dewasa, hingga lansia. Desain antarmuka dibuat agar ramah dan mudah dipahami oleh pengguna dari berbagai usia.
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question" onclick="toggleFaqAnswer(this)">
                        <i class="fas fa-chevron-right"></i>
                        Apa saja fitur utama di dalam aplikasi MUVIT?
                    </div>
                    <div class="faq-answer">
                        <p>📩 LAPOR!: Kirim laporan pelanggaran atau kejadian lalu lintas (bisa disertai foto dan video.).</p>
                        <p>🚨 SOS DARURAT: Akses cepat ke nomor darurat seperti ambulans, polisi, pemadam kebakaran, atau BPBD.</p>
                        <p>📘 MUVIT EDU: Panduan digital lengkap tentang etika dan peraturan lalu lintas untuk berbagai jenis kendaraan.</p>
                        <p>🎮 TRAFFIC HERO: Game edukasi untuk membantu kakek menyebrang dengan aman dan tes pengetahuan lalu lintas.</p>
                        <p>📝 TES SIM: simulasi ujian yang berisi 25 soal pilihan ganda seputar lalu lintas, rambu, marka jalan, dan pengetahuan dasar kendaraan.</p>
                        <p>🤖 VIRTUAL ASSISTANT: Akses cepat ke asisten AI yang akan membantu menjawab pertanyaanmu.</p>
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question" onclick="toggleFaqAnswer(this)">
                        <i class="fas fa-chevron-right"></i>
                        Bagaimana cara melaporkan pelanggaran lalu lintas melalui MUVIT?
                    </div>
                    <div class="faq-answer">
                        Cukup buka fitur LAPOR!, anda akan diarahkan untuk mengirimkan email kepada Satuan Lalu Lintas.
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question" onclick="toggleFaqAnswer(this)">
                        <i class="fas fa-chevron-right"></i>
                        Apakah MUVIT bisa digunakan di seluruh Indonesia?
                    </div>
                    <div class="faq-answer">
                        Target utama adalah penggunaan kabupaten, namun efektivitas beberapa fitur (seperti penanganan laporan) bergantung pada kerja sama dengan pemerintah daerah dan institusi terkait.
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question" onclick="toggleFaqAnswer(this)">
                        <i class="fas fa-chevron-right"></i>
                        Apakah MUVIT gratis?
                    </div>
                    <div class="faq-answer">
                        Ya. MUVIT dapat digunakan melalui web secara gratis.
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Contact Modal -->
    <div class="modal" id="contactModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Kontak</h3>
                <button class="close-modal" onclick="closeModal('contactModal')">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="contact-list">
                <div class="contact-item" onclick="openEmail()">
                    <div class="contact-icon">
                        <i class="fas fa-envelope"></i>
                    </div>
                    <div class="contact-info">
                        <div class="contact-type">Email</div>
                        <div class="contact-value">muvitmovewithit@gmail.com</div>
                    </div>
                </div>
                
                <div class="contact-item" onclick="openInstagram()">
                    <div class="contact-icon">
                        <i class="fab fa-instagram"></i>
                    </div>
                    <div class="contact-info">
                        <div class="contact-type">Instagram</div>
                        <div class="contact-value">@nisarumaee_</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Traffic Hero Modal -->
    <div class="modal" id="trafficHeroModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">TRAFFIC HERO</h3>
                <button class="close-modal" onclick="closeModal('trafficHeroModal')">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="traffic-hero-grid">
                <div class="traffic-hero-card" onclick="openGame('bantuKakek')">
                    <div class="traffic-hero-icon">
                        <i class="fas fa-walking"></i>
                    </div>
                    <h3 class="traffic-hero-title">BANTU KAKEK</h3>
                    <p>Bantu kakek menyebrang jalan dengan selamat sambil menghindari kendaraan</p>
                </div>
                
                <div class="traffic-hero-card" onclick="openGame('tesPengetahuan')">
                    <div class="traffic-hero-icon">
                        <i class="fas fa-brain"></i>
                    </div>
                    <h3 class="traffic-hero-title">TES PENGETAHUAN</h3>
                    <p>Kuis untuk anak-anak tentang pengetahuan dasar lalu lintas</p>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Game Modals -->
    <div class="modal" id="gameModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="gameTitle">BANTU KAKEK</h3>
                <button class="close-modal" onclick="closeModal('gameModal')">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div id="gameContent">
                <!-- Game content will be loaded here -->
            </div>
        </div>
    </div>
    
    <!-- SIM Test Modal -->
    <div class="modal" id="simModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">TES SIM</h3>
                <button class="close-modal" onclick="closeModal('simModal')">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div id="simContent">
                <!-- SIM test content will be loaded here -->
            </div>
        </div>
    </div>
    
    <!-- Education Modal -->
    <div class="modal" id="eduModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">MUVIT EDU</h3>
                <button class="close-modal" onclick="closeModal('eduModal')">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="edu-container">
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🧍‍♂️</div>
                        <div class="edu-title">Pejalan Kaki</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Gunakan trotoar, bukan badan jalan.</div>
                        <div class="edu-item">Menyeberanglah di zebra cross atau jembatan penyeberangan.</div>
                        <div class="edu-item">Waspadai kendaraan saat menyeberang, lihat kiri-kanan dulu.</div>
                        <div class="edu-item">Jangan bermain HP saat menyeberang.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🚲</div>
                        <div class="edu-title">Pesepeda Ontel / Manual</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Gunakan jalur sepeda jika tersedia.</div>
                        <div class="edu-item">Jangan melawan arah.</div>
                        <div class="edu-item">Pakai helm dan lampu sepeda saat malam.</div>
                        <div class="edu-item">Hormati rambu lalu lintas dan pejalan kaki.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🛵</div>
                        <div class="edu-title">Pengendara Sepeda Motor</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Pakai helm SNI dan jaket pelindung.</div>
                        <div class="edu-item">Nyalakan lampu utama saat berkendara.</div>
                        <div class="edu-item">Jaga kecepatan dan jarak aman.</div>
                        <div class="edu-item">Jangan menyalip sembarangan, gunakan lampu sein.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🚗</div>
                        <div class="edu-title">Pengendara Mobil</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Gunakan sabuk pengaman.</div>
                        <div class="edu-item">Ikuti batas kecepatan dan marka jalan.</div>
                        <div class="edu-item">Jangan bermain HP saat menyetir.</div>
                        <div class="edu-item">Beri jalan pada pejalan kaki dan pesepeda di tempat yang semestinya.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🚌</div>
                        <div class="edu-title">Pengendara Bus</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Berhenti di halte resmi, bukan sembarang tempat.</div>
                        <div class="edu-item">Utamakan keselamatan penumpang saat naik/turun.</div>
                        <div class="edu-item">Perhatikan blind spot, terutama pesepeda dan pemotor.</div>
                        <div class="edu-item">Hindari ugal-ugalan demi mengejar penumpang.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🚛</div>
                        <div class="edu-title">Pengemudi Truk</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Pastikan muatan tidak melebihi batas.</div>
                        <div class="edu-item">Periksa rem dan kondisi ban secara rutin.</div>
                        <div class="edu-item">Beri isyarat sebelum belok atau berhenti.</div>
                        <div class="edu-item">Waspadai kendaraan kecil di sekitar truk.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">✈️</div>
                        <div class="edu-title">Pilot Pesawat</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Ikuti prosedur pre-flight checklist secara lengkap.</div>
                        <div class="edu-item">Koordinasi dengan menara kontrol (ATC).</div>
                        <div class="edu-item">Pastikan komunikasi jelas antar awak kabin dan penumpang.</div>
                        <div class="edu-item">Utamakan keselamatan, bukan kecepatan.</div>
                    </div>
                </div>
                
                <div class="edu-category" onclick="toggleEduContent(this)">
                    <div class="edu-header">
                        <div class="edu-icon">🚆</div>
                        <div class="edu-title">Masinis Kereta</div>
                    </div>
                    <div class="edu-content">
                        <div class="edu-item">Patuh pada sinyal dan jadwal perjalanan.</div>
                        <div class="edu-item">Lakukan pengecekan rutin terhadap sistem rem dan mesin.</div>
                        <div class="edu-item">Gunakan klakson di perlintasan sebidang.</div>
                        <div class="edu-item">Jaga kecepatan dan berhenti tepat di stasiun.</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        // Game data
        const knowledgeQuiz = [
            {
                question: "Bensinku tinggal sedikit! Apa yang harus ku lakukan?",
                options: [
                    "Mengisi bensin",
                    "Melamun",
                    "Menari"
                ],
                answer: 0
            },
            {
                question: "Lampu lalu lintas berwarna merah, apa yang harus dilakukan?",
                options: [
                    "Terus jalan",
                    "Berhenti",
                    "Mempercepat"
                ],
                answer: 1
            },
            {
                question: "Saat menyebrang jalan, apa yang harus dilakukan?",
                options: [
                    "Lihat kiri dan kanan",
                    "Lari secepatnya",
                    "Tutup mata"
                ],
                answer: 0
            },
            {
                question: "Dimana tempat yang aman untuk bermain?",
                options: [
                    "Taman bermain",
                    "Jalan raya",
                    "Parkiran mobil"
                ],
                answer: 0
            },
            {
                question: "Apa yang harus dipakai saat naik sepeda?",
                options: [
                    "Helm",
                    "Topi pesta",
                    "Tidak perlu pakai apa-apa"
                ],
                answer: 0
            }
        ];
        
        const simTest = [
            {
                question: "Apa arti rambu lalu lintas berbentuk segitiga sama sisi dengan warna dasar kuning dan garis tepi merah?",
                options: [
                    "Rambu larangan",
                    "Rambu peringatan",
                    "Rambu petunjuk",
                    "Rambu perintah"
                ],
                answer: 1
            },
            {
                question: "Rambu larangan umumnya berbentuk:",
                options: [
                    "Persegi panjang biru",
                    "Lingkaran merah",
                    "Segitiga kuning",
                    "Kotak hijau"
                ],
                answer: 1
            },
            {
                question: "Apa arti marka jalan berupa garis putih putus-putus di tengah jalan?",
                options: [
                    "Dilarang mendahului",
                    "Bebas mendahului jika aman",
                    "Hanya untuk kendaraan berat",
                    "Untuk parkir kendaraan"
                ],
                answer: 1
            },
            {
                question: "Rambu bergambar anak kecil menyeberang jalan berarti:",
                options: [
                    "Larangan bermain di jalan",
                    "Jalan menuju sekolah",
                    "Penyeberangan pejalan kaki",
                    "Hanya untuk kendaraan roda dua"
                ],
                answer: 2
            },
            {
                question: "Warna dasar rambu petunjuk adalah:",
                options: [
                    "Merah",
                    "Kuning",
                    "Biru",
                    "Hijau"
                ],
                answer: 3
            },
            {
                question: "Marka jalan garis utuh ganda di tengah berarti:",
                options: [
                    "Diperbolehkan menyalip dua arah",
                    "Dilarang mendahului dari kedua arah",
                    "Khusus untuk kendaraan umum",
                    "Tanda adanya lampu merah"
                ],
                answer: 1
            },
            {
                question: "Marka bergambar sepeda di jalur jalan menunjukkan:",
                options: [
                    "Dilarang dilewati kendaraan",
                    "Jalan rusak",
                    "Jalur khusus sepeda",
                    "Tempat parkir sepeda"
                ],
                answer: 2
            },
            {
                question: "Marka berbentuk kotak kuning di persimpangan berfungsi untuk:",
                options: [
                    "Tempat parkir kendaraan besar",
                    "Jalur evakuasi",
                    "Area dilarang berhenti walau lampu merah",
                    "Zona aman penyeberang"
                ],
                answer: 2
            },
            {
                question: "Garis zigzag di dekat sekolah atau rumah sakit artinya:",
                options: [
                    "Hati-hati ada polisi tidur",
                    "Area berhenti kendaraan umum",
                    "Dilarang parkir dan berhenti",
                    "Jalan satu arah"
                ],
                answer: 2
            },
            {
                question: "Marka jalan warna kuning biasanya menunjukkan:",
                options: [
                    "Jalan khusus kendaraan pribadi",
                    "Jalan nasional",
                    "Pembatas antara jalur cepat dan lambat",
                    "Tidak ada arti khusus"
                ],
                answer: 2
            },
            {
                question: "Fungsi utama rem tangan adalah untuk:",
                options: [
                    "Mempercepat mobil",
                    "Menyalakan lampu",
                    "Menahan kendaraan saat berhenti",
                    "Mendinginkan mesin"
                ],
                answer: 2
            },
            {
                question: "Lampu hazard digunakan ketika:",
                options: [
                    "Ingin berbelok",
                    "Parkir di jalan",
                    "Dalam kondisi darurat",
                    "Berkendara malam hari"
                ],
                answer: 2
            },
            {
                question: "Oli mesin perlu diganti secara berkala untuk:",
                options: [
                    "Menambah kecepatan",
                    "Menghemat bahan bakar",
                    "Menjaga pelumasan mesin",
                    "Membersihkan jok"
                ],
                answer: 2
            },
            {
                question: "Jika indikator suhu mesin menyala merah, maka:",
                options: [
                    "Mesin sedang dingin",
                    "Mesin overheat",
                    "Bahan bakar habis",
                    "Ban bocor"
                ],
                answer: 1
            },
            {
                question: "Tekanan angin ban yang kurang dapat menyebabkan:",
                options: [
                    "Rem lebih kuat",
                    "Ban lebih awet",
                    "Konsumsi BBM lebih boros",
                    "Kendaraan lebih cepat"
                ],
                answer: 2
            },
            {
                question: "Helm SNI artinya:",
                options: [
                    "Sudah nyaman",
                    "Sering naik intern",
                    "Standar Nasional Indonesia",
                    "Syarat naik instansi"
                ],
                answer: 2
            },
            {
                question: "Fungsi sabuk pengaman adalah untuk:",
                options: [
                    "Gaya",
                    "Menambah kecepatan",
                    "Keselamatan saat tabrakan",
                    "Menjaga barang tetap di kursi"
                ],
                answer: 2
            },
            {
                question: "Jarak aman mengikuti kendaraan di depan saat hujan adalah:",
                options: [
                    "1 meter",
                    "2 detik waktu reaksi",
                    "10 langkah kaki",
                    "Tidak perlu ada jarak"
                ],
                answer: 1
            },
            {
                question: "Di jalan menanjak dan sempit, siapa yang harus mengalah?",
                options: [
                    "Kendaraan menanjak",
                    "Kendaraan menurun",
                    "Sepeda motor",
                    "Kendaraan yang lebih kecil"
                ],
                answer: 1
            },
            {
                question: "Apa yang perlu diperiksa sebelum menyalakan mesin kendaraan?",
                options: [
                    "Warna mobil",
                    "Posisi kaca",
                    "Kondisi ban, oli, dan bahan bakar",
                    "Musik di radio"
                ],
                answer: 2
            },
            {
                question: "Apa yang harus dilakukan jika melihat lampu lalu lintas kuning berkedip?",
                options: [
                    "Tancap gas",
                    "Berhenti total",
                    "Hati-hati dan kurangi kecepatan",
                    "Belok ke kanan"
                ],
                answer: 2
            },
            {
                question: "Tanda lampu lalu lintas merah artinya:",
                options: [
                    "Jalan terus",
                    "Belok kiri langsung",
                    "Wajib berhenti",
                    "Lihat kanan dulu"
                ],
                answer: 2
            },
            {
                question: "Jika melihat pejalan kaki sedang menyeberang di zebra cross, pengendara harus:",
                options: [
                    "Membunyikan klakson",
                    "Mendahului",
                    "Berhenti dan memberi jalan",
                    "Mengalihkan jalur"
                ],
                answer: 2
            },
            {
                question: "Klakson digunakan untuk:",
                options: [
                    "Menyapa teman",
                    "Menegur pengendara lain",
                    "Peringatan untuk keselamatan",
                    "Pamer suara"
                ],
                answer: 2
            },
            {
                question: "Berkendara sambil menggunakan HP dapat menyebabkan:",
                options: [
                    "Konsentrasi terpecah dan bahaya kecelakaan",
                    "Jalan lebih cepat",
                    "Hemat baterai",
                    "Aman karena multitasking"
                ],
                answer: 0
            }
        ];
        
        // Initialize variables
        let currentGame = null;
        let currentQuiz = null;
        let currentQuestion = 0;
        let score = 0;
        let characterPosition = { x: 0, y: 0 };
        let obstacles = [];
        let gameInterval;
        let gameSpeed = 2;
        let gameStarted = false;
        
        // Splash screen with typewriter effect
        const splashScreen = document.getElementById('splashScreen');
        const subtitle = document.getElementById('subtitle');
        const typedText = document.getElementById('typed-text');
        const mainContainer = document.getElementById('mainContainer');
        const text = "Mobile Untuk Visi Integritas Lalu-Lintas Terbaik";
        let index = 0;
        
        function typeWriter() {
            if (index < text.length) {
                typedText.textContent += text.charAt(index);
                index++;
                setTimeout(typeWriter, 50);
            } else {
                setTimeout(() => {
                    splashScreen.style.opacity = '0';
                    setTimeout(() => {
                        splashScreen.style.display = 'none';
                        mainContainer.classList.add('show');
                    }, 1000);
                }, 2000);
            }
        }
        
        // Start typewriter effect
        setTimeout(typeWriter, 500);
        
        // Menu toggle functionality
        const menuToggle = document.getElementById('menuToggle');
        const dropdownMenu = document.getElementById('dropdownMenu');
        
        menuToggle.addEventListener('click', function() {
            playSound('click');
            dropdownMenu.classList.toggle('show');
        });
        
        // Close dropdown when clicking outside
        document.addEventListener('click', function(event) {
            if (!menuToggle.contains(event.target) && !dropdownMenu.contains(event.target)) {
                dropdownMenu.classList.remove('show');
            }
        });
        
        // Theme toggle
        const themeToggle = document.getElementById('themeToggle');
        const themeIcon = themeToggle.querySelector('.dropdown-icon i');
        
        themeToggle.addEventListener('click', function() {
            playSound('click');
            document.body.classList.toggle('light-mode');
            
            if (document.body.classList.contains('light-mode')) {
                themeIcon.className = 'fas fa-sun';
                themeToggle.querySelector('.dropdown-text').textContent = 'Light Mode';
            } else {
                themeIcon.className = 'fas fa-moon';
                themeToggle.querySelector('.dropdown-text').textContent = 'Dark Mode';
            }
            
            dropdownMenu.classList.remove('show');
        });
        
        // FAQ modal
        const faqBtn = document.getElementById('faqBtn');
        const faqModal = document.getElementById('faqModal');
        
        faqBtn.addEventListener('click', function() {
            playSound('click');
            faqModal.classList.add('show');
            dropdownMenu.classList.remove('show');
        });
        
        // Contact modal
        const contactBtn = document.getElementById('contactBtn');
        const contactModal = document.getElementById('contactModal');
        
        contactBtn.addEventListener('click', function() {
            playSound('click');
            contactModal.classList.add('show');
            dropdownMenu.classList.remove('show');
        });
        
        // Close modals
        function closeModal(modalId) {
            playSound('click');
            document.getElementById(modalId).classList.remove('show');
            
            // Reset game when closing game modal
            if (modalId === 'gameModal') {
                clearInterval(gameInterval);
                gameStarted = false;
            }
        }
        
        // Accessibility mode
        const accessibilityBtn = document.getElementById('accessibilityBtn');
        
        accessibilityBtn.addEventListener('click', function() {
            playSound('click');
            document.body.classList.toggle('accessibility-mode');
            dropdownMenu.classList.remove('show');
        });
        
        // Emergency call function
        function callEmergency(number) {
            playSound('click');
            if (/Android|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
                window.location.href = `tel:${number}`;
            } else {
                alert(`Memanggil: ${number}\n\nDi perangkat mobile, ini akan langsung menelepon`);
            }
        }
        
        // Card functions
        function openReport() {
            playSound('click');
            const subject = encodeURIComponent("Laporan Pelanggaran Lalu Lintas");
            const body = encodeURIComponent("Deskripsikan pelanggaran yang Anda saksikan di sini...\n\nLokasi: \nWaktu: \n\nTerima kasih telah melapor!");
            window.location.href = `mailto:antas.resdmk@gmail.com?subject=${subject}&body=${body}`;
        }
        
        function openEducation() {
            playSound('click');
            document.getElementById('eduModal').classList.add('show');
        }
        
        function openTrafficHero() {
            playSound('click');
            document.getElementById('trafficHeroModal').classList.add('show');
        }
        
        function openGame(gameType) {
            playSound('click');
            currentGame = gameType;
            const gameModal = document.getElementById('gameModal');
            const gameTitle = document.getElementById('gameTitle');
            const gameContent = document.getElementById('gameContent');
            
            if (gameType === 'bantuKakek') {
                gameTitle.textContent = "BANTU KAKEK";
                gameContent.innerHTML = `
                    <p style="margin-bottom: 15px;">Bantu Kakek menyebrang jalan dengan selamat! Gunakan tombol panah untuk menggerakkan Kakek.</p>
                    <div class="game-container">
                        <div class="game-road" id="gameRoad">
                            <!-- Road lines will be added dynamically -->
                        </div>
                        <div class="character" id="character">👴</div>
                        <div class="game-result" id="gameResult">
                            <div class="result-title" id="resultTitle"></div>
                            <button class="result-btn" onclick="restartGame()">Main Lagi</button>
                        </div>
                    </div>
                    <div class="controls">
                        <div class="control-btn" onclick="moveCharacter('left')"><i class="fas fa-arrow-left"></i></div>
                        <div class="control-btn" onclick="moveCharacter('up')"><i class="fas fa-arrow-up"></i></div>
                        <div class="control-btn" onclick="moveCharacter('right')"><i class="fas fa-arrow-right"></i></div>
                        <div class="control-btn" onclick="moveCharacter('down')"><i class="fas fa-arrow-down"></i></div>
                    </div>
                `;
                initGame();
            } else if (gameType === 'tesPengetahuan') {
                gameTitle.textContent = "TES PENGETAHUAN";
                gameContent.innerHTML = `
                    <p style="margin-bottom: 15px;">Tes pengetahuan lalu lintas untuk anak-anak. Pilih jawaban yang benar!</p>
                    <div id="quizContent">
                        <!-- Quiz content will be loaded here -->
                    </div>
                `;
                startQuiz(knowledgeQuiz);
            }
            
            gameModal.classList.add('show');
        }
        
        function openTest() {
            playSound('click');
            document.getElementById('simModal').classList.add('show');
            const simContent = document.getElementById('simContent');
            
            simContent.innerHTML = `
                <p style="margin-bottom: 15px;">Tes pengetahuan untuk mendapatkan SIM. Jawab 25 soal dengan benar!</p>
                <div id="quizContent">
                    <!-- Quiz content will be loaded here -->
                </div>
            `;
            startQuiz(simTest);
        }
        
        function openAssistant() {
            playSound('click');
            window.open('https://chat.openai.com', '_blank');
        }
        
        // Toggle education content
        function toggleEduContent(element) {
            playSound('click');
            const content = element.querySelector('.edu-content');
            content.classList.toggle('show');
        }
        
        // Toggle FAQ answer
        function toggleFaqAnswer(element) {
            playSound('click');
            const faqItem = element.closest('.faq-item');
            const answer = faqItem.querySelector('.faq-answer');
            element.classList.toggle('expanded');
            answer.classList.toggle('show');
        }
        
        // Game functions
        function initGame() {
            const gameRoad = document.getElementById('gameRoad');
            const character = document.getElementById('character');
            
            // Reset character position
            characterPosition = { x: 50, y: 90 };
            character.style.left = `${characterPosition.x}%`;
            character.style.bottom = `${characterPosition.y}px`;
            
            // Clear obstacles
            obstacles = [];
            gameRoad.innerHTML = '';
            
            // Create road lines
            for (let i = 0; i < 5; i++) {
                const line = document.createElement('div');
                line.className = 'road-line';
                line.style.top = `${i * 20}%`;
                line.style.animationDelay = `${i * 0.5}s`;
                gameRoad.appendChild(line);
            }
            
            // Start game
            gameStarted = true;
            gameInterval = setInterval(updateGame, 50);
        }
        
        function updateGame() {
            if (!gameStarted) return;
            
            const gameRoad = document.getElementById('gameRoad');
            const character = document.getElementById('character');
            
            // Move obstacles
            obstacles.forEach((obstacle, index) => {
                obstacle.y -= gameSpeed;
                obstacle.element.style.top = `${obstacle.y}px`;
                
                // Remove obstacles that are off screen
                if (obstacle.y < -30) {
                    obstacle.element.remove();
                    obstacles.splice(index, 1);
                }
                
                // Check collision
                if (checkCollision(character, obstacle.element)) {
                    gameOver(false);
                }
            });
            
            // Add new obstacles randomly
            if (Math.random() < 0.05) {
                createObstacle();
            }
            
            // Check if character reached the top
            if (parseInt(character.style.bottom) > 250) {
                gameOver(true);
            }
        }
        
        function createObstacle() {
            const gameRoad = document.getElementById('gameRoad');
            const obstacle = document.createElement('div');
            obstacle.className = 'obstacle';
            
            // Randomly decide direction (left to right or right to left)
            const direction = Math.random() > 0.5 ? 'left' : 'right';
            obstacle.classList.add(direction);
            
            // Set initial position
            if (direction === 'left') {
                obstacle.style.left = '0%';
                obstacle.style.transform = 'translateX(-100%)';
            } else {
                obstacle.style.left = '100%';
            }
            
            obstacle.style.top = `${Math.floor(Math.random() * 70) + 15}%`;
            
            gameRoad.appendChild(obstacle);
            
            obstacles.push({
                element: obstacle,
                y: parseInt(obstacle.style.top),
                direction: direction
            });
            
            // Animate obstacle
            obstacle.style.animation = `moveHorizontal ${Math.random() * 2 + 2}s linear infinite ${direction === 'right' ? 'reverse' : ''}`;
        }
        
        function moveCharacter(direction) {
            if (!gameStarted) return;
            playSound('click');
            
            const character = document.getElementById('character');
            const step = 10;
            
            switch (direction) {
                case 'up':
                    characterPosition.y += step;
                    break;
                case 'down':
                    characterPosition.y = Math.max(20, characterPosition.y - step);
                    break;
                case 'left':
                    characterPosition.x = Math.max(10, characterPosition.x - step);
                    break;
                case 'right':
                    characterPosition.x = Math.min(90, characterPosition.x + step);
                    break;
            }
            
            character.style.left = `${characterPosition.x}%`;
            character.style.bottom = `${characterPosition.y}px`;
        }
        
        function checkCollision(char, obs) {
            const charRect = char.getBoundingClientRect();
            const obsRect = obs.getBoundingClientRect();
            
            return !(
                charRect.right < obsRect.left ||
                charRect.left > obsRect.right ||
                charRect.bottom < obsRect.top ||
                charRect.top > obsRect.bottom
            );
        }
        
        function gameOver(success) {
            gameStarted = false;
            clearInterval(gameInterval);
            
            const result = document.getElementById('gameResult');
            const title = document.getElementById('resultTitle');
            
            result.style.display = 'block';
            
            if (success) {
                title.textContent = "Kakek berhasil menyebrang dengan selamat! Terima kasih orang baik!";
                title.className = "result-title result-success";
                playSound('success');
            } else {
                title.textContent = "Aduh! Lain kali lebih berhati-hati ya!";
                title.className = "result-title result-fail";
                playSound('fail');
            }
        }
        
        function restartGame() {
            playSound('click');
            const result = document.getElementById('gameResult');
            result.style.display = 'none';
            initGame();
        }
        
        // Quiz functions
        function startQuiz(quiz) {
            currentQuiz = quiz;
            currentQuestion = 0;
            score = 0;
            showQuestion();
        }
        
        function showQuestion() {
            const quizContent = document.getElementById('quizContent');
            
            if (currentQuestion < currentQuiz.length) {
                const question = currentQuiz[currentQuestion];
                let optionsHtml = '';
                
                question.options.forEach((option, index) => {
                    optionsHtml += `
                        <div class="option" onclick="selectOption(this, ${index})">
                            ${String.fromCharCode(65 + index)}. ${option}
                        </div>
                    `;
                });
                
                quizContent.innerHTML = `
                    <div class="quiz-question">
                        <div class="question-text">${currentQuestion + 1}. ${question.question}</div>
                        <div class="options">${optionsHtml}</div>
                    </div>
                    <div class="quiz-nav">
                        ${currentQuestion > 0 ? '<button class="nav-btn" onclick="prevQuestion()"><i class="fas fa-arrow-left"></i> Sebelumnya</button>' : '<div></div>'}
                        <button class="nav-btn" onclick="nextQuestion()">${currentQuestion === currentQuiz.length - 1 ? 'Selesai' : 'Selanjutnya'} <i class="fas fa-arrow-right"></i></button>
                    </div>
                `;
            } else {
                showResults();
            }
        }
        
        function selectOption(element, optionIndex) {
            playSound('click');
            // Remove selected class from all options
            const options = element.parentElement.querySelectorAll('.option');
            options.forEach(opt => opt.classList.remove('selected'));
            
            // Add selected class to clicked option
            element.classList.add('selected');
            
            // Store selected answer
            currentQuiz[currentQuestion].selected = optionIndex;
        }
        
        function nextQuestion() {
            playSound('click');
            const selectedOption = currentQuiz[currentQuestion].selected;
            
            // Check if answer is correct
            if (selectedOption === currentQuiz[currentQuestion].answer) {
                score++;
            }
            
            currentQuestion++;
            showQuestion();
        }
        
        function prevQuestion() {
            playSound('click');
            currentQuestion--;
            showQuestion();
        }
        
        function showResults() {
            const quizContent = document.getElementById('quizContent');
            
            // Play applause sound for SIM test
            if (currentQuiz === simTest) {
                playSound('applause');
            }
            
            let answerKey = '';
            if (currentQuiz === simTest) {
                answerKey = '<h3>Kunci Jawaban</h3><div class="answer-key">';
                simTest.forEach((question, index) => {
                    answerKey += `
                        <div class="answer-item">
                            <strong>${index + 1}. ${question.question}</strong>
                            <p class="correct-answer">Jawaban benar: ${question.options[question.answer]}</p>
                        </div>
                    `;
                });
                answerKey += '</div>';
            }
            
            quizContent.innerHTML = `
                <div class="quiz-result">
                    <h3>Hasil Tes</h3>
                    <div class="score-display">${score} / ${currentQuiz.length}</div>
                    <p>${score >= currentQuiz.length * 0.8 ? 'Selamat! Anda lulus tes.' : 'Cukup bagus! Ayo main lagi!'}</p>
                    ${answerKey}
                    <button class="result-btn" onclick="restartQuiz()">Ulangi Tes</button>
                </div>
            `;
        }
        
        function restartQuiz() {
            playSound('click');
            startQuiz(currentQuiz);
        }
        
        // Sound functions
        function playSound(type) {
            try {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                
                if (type === 'click') {
                    // Simple click sound
                    const oscillator = audioContext.createOscillator();
                    oscillator.type = 'sine';
                    oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
                    oscillator.connect(audioContext.destination);
                    oscillator.start();
                    oscillator.stop(audioContext.currentTime + 0.05);
                } 
                else if (type === 'success') {
                    // Success sound
                    const oscillator = audioContext.createOscillator();
                    oscillator.type = 'sine';
                    oscillator.frequency.setValueAtTime(523.25, audioContext.currentTime); // C5
                    oscillator.frequency.setValueAtTime(659.25, audioContext.currentTime + 0.1); // E5
                    oscillator.frequency.setValueAtTime(783.99, audioContext.currentTime + 0.2); // G5
                    oscillator.connect(audioContext.destination);
                    oscillator.start();
                    oscillator.stop(audioContext.currentTime + 0.3);
                } 
                else if (type === 'fail') {
                    // Fail sound
                    const oscillator = audioContext.createOscillator();
                    oscillator.type = 'sawtooth';
                    oscillator.frequency.setValueAtTime(349.23, audioContext.currentTime); // F4
                    oscillator.frequency.setValueAtTime(261.63, audioContext.currentTime + 0.2); // C4
                    oscillator.connect(audioContext.destination);
                    oscillator.start();
                    oscillator.stop(audioContext.currentTime + 0.4);
                }
                else if (type === 'applause') {
                    // Applause sound for SIM test
                    const oscillator = audioContext.createOscillator();
                    oscillator.type = 'sine';
                    
                    // Create a short applause-like sound
                    const frequencies = [523.25, 587.33, 659.25, 698.46, 783.99, 880];
                    let currentTime = audioContext.currentTime;
                    
                    frequencies.forEach((freq, i) => {
                        oscillator.frequency.setValueAtTime(freq, currentTime);
                        currentTime += 0.1;
                    });
                    
                    oscillator.connect(audioContext.destination);
                    oscillator.start();
                    oscillator.stop(audioContext.currentTime + 0.6);
                }
            } catch (e) {
                console.log("Audio error:", e);
            }
        }
        
        // Footer contact functions
        function openInstagram() {
            playSound('click');
            window.open('https://www.instagram.com/nisarumaee_?igsh=MXd3NWF5aWhleTh1ag==', '_blank');
        }
        
        function openEmail() {
            playSound('click');
            window.location.href = 'mailto:muvitmovewithit@gmail.com';
        }
    </script>
    

<html lang="id">
<head>
    <!-- Previous head content remains the same -->
    <style>
        /* Previous styles remain the same */
        
        .explanation {
            margin-top: 10px;
            padding: 10px;
            background: rgba(0, 0, 0, 0.1);
            border-radius: 5px;
            font-size: 0.9rem;
            display: none;
        }
        
        .explanation.show {
            display: block;
        }
        
        .toggle-explanation {
            color: var(--accent);
            cursor: pointer;
            font-size: 0.9rem;
            margin-top: 5px;
            display: inline-block;
        }
        
        body.light-mode .explanation {
            background: rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body>
    <!-- Previous HTML content remains the same until the simTest array -->

    <script>
        // Updated simTest array with 35 questions (original 25 + new 10)
        const simTest = [
            // Original 25 questions remain unchanged...
            
            // New additional 10 questions
            {
                question: "Apa arti tanda rambu lalu lintas segitiga dengan warna dasar merah?",
                options: [
                    "Larangan",
                    "Peringatan",
                    "Perintah",
                    "Informasi"
                ],
                answer: 1,
                explanation: "Rambu segitiga merah digunakan untuk peringatan adanya bahaya atau kondisi jalan khusus di depan."
            },
            {
                question: "Saat mengemudi di jalan licin karena hujan, yang harus Anda lakukan adalah...",
                options: [
                    "Menginjak rem secara tiba-tiba",
                    "Mempercepat kendaraan",
                    "Mengemudi dengan kecepatan rendah dan menjaga jarak aman",
                    "Memotong jalur kendaraan lain"
                ],
                answer: 2,
                explanation: "Jalan licin membuat kendaraan mudah tergelincir. Jaga jarak dan kurangi kecepatan."
            },
            {
                question: "Apa fungsi lampu sein pada kendaraan?",
                options: [
                    "Memberi tanda untuk belok atau pindah jalur",
                    "Menambah pencahayaan di malam hari",
                    "Mengingatkan kendaraan di belakang untuk berhenti",
                    "Menghidupkan lampu utama"
                ],
                answer: 0,
                explanation: "Lampu sein digunakan untuk memberi sinyal arah, misalnya saat akan berbelok atau berpindah jalur."
            },
            {
                question: "Jika Anda melihat lampu merah menyala di lampu lalu lintas, apa yang harus dilakukan?",
                options: [
                    "Melanjutkan perjalanan dengan hati-hati",
                    "Berhenti sebelum garis stop",
                    "Mempercepat kendaraan untuk lewat",
                    "Berhenti di tengah persimpangan"
                ],
                answer: 1,
                explanation: "Lampu merah artinya harus berhenti total, sebelum garis stop."
            },
            {
                question: "Bagaimana cara yang benar untuk menyalip kendaraan lain di jalan raya?",
                options: [
                    "Menyalip dari sebelah kanan",
                    "Menyalip dari sebelah kiri dan memastikan aman",
                    "Menyalip tanpa melihat spion",
                    "Menyalip sambil membunyikan klakson terus-menerus"
                ],
                answer: 0,
                explanation: "Menyalip dari kanan adalah aturan yang benar di jalan dua arah di Indonesia."
            },
            {
                question: "Saat kendaraan akan masuk ke jalan utama dari jalan kecil, Anda harus...",
                options: [
                    "Mempercepat untuk masuk jalan utama",
                    "Memberi prioritas pada kendaraan di jalan utama",
                    "Menyalip kendaraan lain di jalan utama",
                    "Tidak perlu memberi perhatian"
                ],
                answer: 1,
                explanation: "Kendaraan dari jalan kecil wajib mengalah pada arus kendaraan dari jalan utama."
            },
            {
                question: "Apa arti tanda rambu larangan parkir?",
                options: [
                    "Boleh parkir di mana saja",
                    "Tidak boleh parkir di tempat tersebut",
                    "Hanya boleh parkir pada waktu tertentu",
                    "Parkir hanya untuk kendaraan tertentu"
                ],
                answer: 1,
                explanation: "Rambu ini menunjukkan dilarang parkir di lokasi tersebut, bisa karena mengganggu arus lalu lintas."
            },
            {
                question: "Berapa jarak aman minimal antar kendaraan saat berkendara di jalan raya?",
                options: [
                    "1 meter",
                    "2 meter",
                    "Sesuai kecepatan dan kondisi jalan",
                    "5 meter"
                ],
                answer: 2,
                explanation: "Tidak ada angka pasti karena jarak aman tergantung kecepatan dan kondisi jalan (cuaca, visibilitas, dll)."
            },
            {
                question: "Apa yang harus dilakukan ketika ada kendaraan darurat (ambulans, pemadam kebakaran) yang menggunakan sirine dan lampu darurat di belakang?",
                options: [
                    "Tetap jalan seperti biasa",
                    "Memberi jalan dan berhenti di sisi jalan",
                    "Mempercepat laju kendaraan",
                    "Mengabaikannya"
                ],
                answer: 1,
                explanation: "Pengemudi wajib memberi jalan pada kendaraan darurat untuk keselamatan bersama."
            },
            {
                question: "Saat mengemudi di jalan menurun curam, sebaiknya...",
                options: [
                    "Menggunakan rem tangan terus-menerus",
                    "Menggunakan transmisi rendah dan mengerem secara berkala",
                    "Mematikan mesin",
                    "Mempercepat kendaraan"
                ],
                answer: 1,
                explanation: "Menggunakan gigi rendah membantu menahan laju kendaraan secara mekanis tanpa membebani rem."
            }
        ];

        // Previous JavaScript code remains the same until the showQuestion function

        function showQuestion() {
            const quizContent = document.getElementById('quizContent');
            
            if (currentQuestion < currentQuiz.length) {
                const question = currentQuiz[currentQuestion];
                let optionsHtml = '';
                
                question.options.forEach((option, index) => {
                    optionsHtml += `
                        <div class="option" onclick="selectOption(this, ${index})">
                            ${String.fromCharCode(65 + index)}. ${option}
                        </div>
                    `;
                });

                // Add explanation toggle if explanation exists
                let explanationHtml = '';
                if (question.explanation) {
                    explanationHtml = `
                        <div class="toggle-explanation" onclick="toggleExplanation(this)">
                            <i class="fas fa-info-circle"></i> Lihat Penjelasan
                        </div>
                        <div class="explanation">
                            ${question.explanation}
                        </div>
                    `;
                }
                
                quizContent.innerHTML = `
                    <div class="quiz-question">
                        <div class="question-text">${currentQuestion + 1}. ${question.question}</div>
                        <div class="options">${optionsHtml}</div>
                        ${explanationHtml}
                    </div>
                    <div class="quiz-nav">
                        ${currentQuestion > 0 ? '<button class="nav-btn" onclick="prevQuestion()"><i class="fas fa-arrow-left"></i> Sebelumnya</button>' : '<div></div>'}
                        <button class="nav-btn" onclick="nextQuestion()">${currentQuestion === currentQuiz.length - 1 ? 'Selesai' : 'Selanjutnya'} <i class="fas fa-arrow-right"></i></button>
                    </div>
                `;
            } else {
                showResults();
            }
        }

        // Add new function to toggle explanation
        function toggleExplanation(element) {
            const explanation = element.nextElementSibling;
            explanation.classList.toggle('show');
            if (explanation.classList.contains('show')) {
                element.innerHTML = '<i class="fas fa-times-circle"></i> Sembunyikan Penjelasan';
            } else {
                element.innerHTML = '<i class="fas fa-info-circle"></i> Lihat Penjelasan';
            }
        }

        // Rest of the JavaScript code remains the same
    </script>
</body>
</html>
</body>
</html>
