<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aroha café — Káva, co dává smysl ☕</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Lora:wght@400;600&family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --cream: #FFF8F0;
            --coffee-dark: #3E2723;
            --coffee-medium: #6D4C41;
            --coffee-light: #A1887F;
            --sage: #8B9D83;
            --sage-dark: #6B7D63;
            --terracotta: #C77D58;
            --warm-white: #FDFBF7;
            --shadow: rgba(62, 39, 35, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Quicksand', sans-serif;
            color: var(--coffee-dark);
            background: var(--cream);
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        /* Typography */
        h1, h2, h3 {
            font-family: 'Lora', serif;
            font-weight: 600;
            line-height: 1.2;
        }
        
        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 248, 240, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            box-shadow: 0 2px 20px var(--shadow);
            animation: slideDown 0.6s ease;
        }
        
        @keyframes slideDown {
            from {
                transform: translateY(-100%);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        
        nav .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        nav .logo {
            font-family: 'Lora', serif;
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--coffee-dark);
            text-decoration: none;
            letter-spacing: -0.5px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }
        
        nav ul li a {
            color: var(--coffee-medium);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }
        
        nav ul li a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--sage);
            transition: width 0.3s ease;
        }
        
        nav ul li a:hover {
            color: var(--sage-dark);
        }
        
        nav ul li a:hover::after {
            width: 100%;
        }
        
        /* Mobile Menu */
        .menu-toggle {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            padding: 5px;
        }
        
        .menu-toggle span {
            width: 25px;
            height: 3px;
            background: var(--coffee-dark);
            border-radius: 2px;
            transition: all 0.3s ease;
        }
        
        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, var(--cream) 0%, var(--warm-white) 100%);
            position: relative;
            overflow: hidden;
            padding-top: 80px;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(139, 157, 131, 0.15) 0%, transparent 70%);
            border-radius: 50%;
            animation: float 20s ease-in-out infinite;
        }
        
        .hero::after {
            content: '';
            position: absolute;
            bottom: -30%;
            left: -10%;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(199, 125, 88, 0.1) 0%, transparent 70%);
            border-radius: 50%;
            animation: float 15s ease-in-out infinite reverse;
        }
        
        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(30px, -30px) rotate(120deg); }
            66% { transform: translate(-20px, 20px) rotate(240deg); }
        }
        
        .hero-content {
            text-align: center;
            max-width: 700px;
            padding: 2rem;
            position: relative;
            z-index: 1;
            animation: fadeInUp 1s ease;
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .hero h1 {
            font-size: clamp(3rem, 8vw, 5rem);
            margin-bottom: 1rem;
            color: var(--coffee-dark);
            animation: fadeInUp 1s ease 0.2s both;
        }
        
        .hero .tagline {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            color: var(--coffee-medium);
            margin-bottom: 2rem;
            font-weight: 300;
            animation: fadeInUp 1s ease 0.4s both;
        }
        
        .cta-button {
            display: inline-block;
            padding: 1rem 2.5rem;
            background: var(--sage);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(139, 157, 131, 0.3);
            animation: fadeInUp 1s ease 0.6s both;
        }
        
        .cta-button:hover {
            background: var(--sage-dark);
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(139, 157, 131, 0.4);
        }
        
        /* Section Styles */
        section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        section h2 {
            font-size: clamp(2rem, 5vw, 3rem);
            margin-bottom: 2rem;
            color: var(--coffee-dark);
            text-align: center;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }
        
        section h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background: var(--terracotta);
            border-radius: 2px;
        }
        
        /* About Section */
        #o-nas {
            background: var(--warm-white);
        }
        
        .about-content {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
            font-size: 1.1rem;
            line-height: 1.8;
            color: var(--coffee-medium);
        }
        
        .about-content p {
            margin-bottom: 1.5rem;
        }
        
        /* Menu Section */
        #nabidka {
            background: var(--cream);
        }
        
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }
        
        .menu-card {
            background: white;
            padding: 2.5rem 2rem;
            border-radius: 20px;
            box-shadow: 0 4px 20px var(--shadow);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .menu-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--sage), var(--terracotta));
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.4s ease;
        }
        
        .menu-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 30px rgba(62, 39, 35, 0.15);
        }
        
        .menu-card:hover::before {
            transform: scaleX(1);
        }
        
        .menu-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--coffee-dark);
        }
        
        .menu-card ul {
            list-style: none;
            color: var(--coffee-medium);
        }
        
        .menu-card ul li {
            padding: 0.5rem 0;
            padding-left: 1.5rem;
            position: relative;
        }
        
        .menu-card ul li::before {
            content: '✦';
            position: absolute;
            left: 0;
            color: var(--sage);
        }
        
        /* Opening Hours */
        #oteviraci-doba {
            background: var(--warm-white);
        }
        
        .hours-container {
            max-width: 600px;
            margin: 3rem auto 0;
            background: white;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 4px 20px var(--shadow);
        }
        
        .hours-row {
            display: flex;
            justify-content: space-between;
            padding: 1rem 0;
            border-bottom: 1px solid rgba(139, 157, 131, 0.2);
            font-size: 1.1rem;
        }
        
        .hours-row:last-child {
            border-bottom: none;
        }
        
        .day {
            font-weight: 600;
            color: var(--coffee-dark);
        }
        
        .time {
            color: var(--coffee-medium);
        }
        
        .closed {
            color: var(--coffee-light);
            font-style: italic;
        }
        
        .weekend-note {
            margin-top: 2rem;
            padding: 1.5rem;
            background: rgba(199, 125, 88, 0.1);
            border-radius: 10px;
            text-align: center;
            color: var(--coffee-medium);
            border-left: 4px solid var(--terracotta);
        }
        
        /* Contact Section */
        #kontakt {
            background: var(--cream);
        }
        
        .contact-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            margin-top: 3rem;
        }
        
        .contact-info {
            background: white;
            padding: 2.5rem;
            border-radius: 20px;
            box-shadow: 0 4px 20px var(--shadow);
        }
        
        .contact-item {
            margin-bottom: 2rem;
        }
        
        .contact-item:last-child {
            margin-bottom: 0;
        }
        
        .contact-label {
            font-weight: 600;
            color: var(--sage-dark);
            margin-bottom: 0.5rem;
            display: block;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .contact-value {
            color: var(--coffee-dark);
            font-size: 1.1rem;
        }
        
        .contact-value a {
            color: var(--coffee-dark);
            text-decoration: none;
            transition: color 0.3s ease;
        }
        
        .contact-value a:hover {
            color: var(--sage);
        }
        
        .social-link {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.8rem 1.5rem;
            background: var(--sage);
            color: white !important;
            text-decoration: none;
            border-radius: 50px;
            transition: all 0.3s ease;
            margin-top: 1rem;
        }
        
        .social-link:hover {
            background: var(--sage-dark);
            transform: translateX(5px);
        }
        
        .map-container {
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 4px 20px var(--shadow);
            height: 100%;
            min-height: 400px;
        }
        
        .map-container iframe {
            width: 100%;
            height: 100%;
            min-height: 400px;
            border: none;
        }
        
        /* Footer */
        footer {
            background: var(--coffee-dark);
            color: var(--cream);
            padding: 3rem 2rem 2rem;
            text-align: center;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .footer-logo {
            font-family: 'Lora', serif;
            font-size: 2rem;
            font-weight: 600;
            margin-bottom: 1rem;
        }
        
        .footer-contact {
            margin: 2rem 0;
            font-size: 0.95rem;
            opacity: 0.9;
        }
        
        .footer-contact p {
            margin: 0.5rem 0;
        }
        
        .footer-socials {
            margin: 2rem 0;
        }
        
        .footer-social-icon {
            display: inline-flex;
            width: 45px;
            height: 45px;
            align-items: center;
            justify-content: center;
            background: rgba(255, 248, 240, 0.1);
            border-radius: 50%;
            color: var(--cream);
            text-decoration: none;
            margin: 0 0.5rem;
            transition: all 0.3s ease;
            font-size: 1.2rem;
        }
        
        .footer-social-icon:hover {
            background: var(--sage);
            transform: translateY(-3px);
        }
        
        .footer-bottom {
            margin-top: 2rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 248, 240, 0.2);
            font-size: 0.9rem;
            opacity: 0.7;
        }
        
        /* Smooth Scroll */
        html {
            scroll-behavior: smooth;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            nav ul {
                position: fixed;
                top: 70px;
                left: -100%;
                width: 100%;
                background: rgba(255, 248, 240, 0.98);
                backdrop-filter: blur(10px);
                flex-direction: column;
                padding: 2rem;
                box-shadow: 0 4px 20px var(--shadow);
                transition: left 0.3s ease;
                gap: 1rem;
            }
            
            nav ul.active {
                left: 0;
            }
            
            .menu-toggle {
                display: flex;
            }
            
            .menu-toggle.active span:nth-child(1) {
                transform: rotate(45deg) translate(5px, 5px);
            }
            
            .menu-toggle.active span:nth-child(2) {
                opacity: 0;
            }
            
            .menu-toggle.active span:nth-child(3) {
                transform: rotate(-45deg) translate(7px, -6px);
            }
            
            section {
                padding: 4rem 1.5rem;
            }
            
            .contact-grid {
                grid-template-columns: 1fr;
            }
            
            .hours-container {
                padding: 2rem 1.5rem;
            }
            
            .menu-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Scroll Reveal Animation */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }
        
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="container">
            <a href="#" class="logo">Aroha café</a>
            <div class="menu-toggle" id="menuToggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
            <ul id="navMenu">
                <li><a href="#o-nas">O nás</a></li>
                <li><a href="#nabidka">Nabídka</a></li>
                <li><a href="#oteviraci-doba">Otevírací doba</a></li>
                <li><a href="#kontakt">Kontakt</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1>Aroha café</h1>
            <p class="tagline">Káva, co dává smysl ☕</p>
            <a href="#kontakt" class="cta-button">Najít nás</a>
        </div>
    </section>

    <!-- About Section -->
    <section id="o-nas" class="reveal">
        <h2>O nás</h2>
        <div class="about-content">
            <p>
                Vítejte v Aroha café – místě, kde se potkává kvalita s pohodou. 
                Jsme malá kavárna v srdci Brna, kde si můžete vychutnat skvěle 
                připravenou kávu v přátelské a uvolněné atmosféře.
            </p>
            <p>
                Věříme, že dobrá káva není jen nápoj, ale zážitek. Proto si 
                zakládáme na kvalitních surovinách, pečlivé přípravě a osobním 
                přístupu ke každému návštěvníkovi. U nás nejste číslo – jste náš host.
            </p>
            <p>
                Přijďte se zastavit, odpočinout si a nabrat energii do dalšího dne. 
                Těšíme se na vás!
            </p>
        </div>
    </section>

    <!-- Menu Section -->
    <section id="nabidka" class="reveal">
        <h2>Nabídka</h2>
        <div class="menu-grid">
            <div class="menu-card">
                <h3>Káva</h3>
                <ul>
                    <li>Espresso</li>
                    <li>Cappuccino</li>
                    <li>Latte</li>
                    <li>Flat White</li>
                    <li>Americano</li>
                    <li>Filtrovaná káva</li>
                </ul>
            </div>
            
            <div class="menu-card">
                <h3>Dezerty</h3>
                <ul>
                    <li>Domácí koláče</li>
                    <li>Croissanty</li>
                    <li>Muffiny</li>
                    <li>Cheesecake</li>
                    <li>Brownies</li>
                </ul>
            </div>
            
            <div class="menu-card">
                <h3>Další občerstvení</h3>
                <ul>
                    <li>Čaje</li>
                    <li>Fresh džusy</li>
                    <li>Limonády</li>
                    <li>Sendviče</li>
                    <li>Bagety</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Opening Hours -->
    <section id="oteviraci-doba" class="reveal">
        <h2>Otevírací doba</h2>
        <div class="hours-container">
            <div class="hours-row">
                <span class="day">Pondělí</span>
                <span class="time">9:00 – 14:00</span>
            </div>
            <div class="hours-row">
                <span class="day">Úterý</span>
                <span class="time">9:00 – 14:00</span>
            </div>
            <div class="hours-row">
                <span class="day">Středa</span>
                <span class="time">9:00 – 14:00</span>
            </div>
            <div class="hours-row">
                <span class="day">Čtvrtek</span>
                <span class="time">9:00 – 14:00</span>
            </div>
            <div class="hours-row">
                <span class="day">Pátek</span>
                <span class="time">9:00 – 14:00</span>
            </div>
            <div class="hours-row">
                <span class="day">Sobota</span>
                <span class="time closed">Zavřeno</span>
            </div>
            <div class="hours-row">
                <span class="day">Neděle</span>
                <span class="time closed">Zavřeno</span>
            </div>
            
            <div class="weekend-note">
                ℹ️ O víkendech máme zavřeno. Těšíme se na vás ve všední dny!
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="kontakt" class="reveal">
        <h2>Kontakt</h2>
        <div class="contact-grid">
            <div class="contact-info">
                <div class="contact-item">
                    <span class="contact-label">Adresa</span>
                    <div class="contact-value">
                        Křenová 183/57<br>
                        602 00 Brno – Trnitá<br>
                        Česko
                    </div>
                </div>
                
                <div class="contact-item">
                    <span class="contact-label">Telefon</span>
                    <div class="contact-value">
                        <a href="tel:+420603815911">+420 603 815 911</a>
                    </div>
                </div>
                
                <div class="contact-item">
                    <span class="contact-label">Email</span>
                    <div class="contact-value">
                        <a href="mailto:arohacafe@seznam.cz">arohacafe@seznam.cz</a>
                    </div>
                </div>
                
                <div class="contact-item">
                    <span class="contact-label">Sociální sítě</span>
                    <a href="https://www.facebook.com/Arohabistrocafe" target="_blank" class="social-link">
                        <span>📘</span>
                        <span>Navštivte nás na Facebooku</span>
                    </a>
                </div>
                
                <div class="contact-item">
                    <span class="contact-label">Hodnocení</span>
                    <div class="contact-value">
                        ⭐⭐⭐⭐⭐ 5,0 / 5 (5 recenzí)
                    </div>
                </div>
            </div>
            
            <div class="map-container">
                <iframe 
                    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2607.4158267867586!2d16.600894!3d49.195833!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x471294679ca5c4c1%3A0x8e8f3e3e3e3e3e3e!2zS8WZZW7DtnbDoSAxODMvNTcsIDYwMiAwMCBCcm5vLVRybml0w6E!5e0!3m2!1scs!2scz!4v1234567890"
                    allowfullscreen="" 
                    loading="lazy" 
                    referrerpolicy="no-referrer-when-downgrade">
                </iframe>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-logo">Aroha café</div>
            
            <div class="footer-contact">
                <p>Křenová 183/57, 602 00 Brno – Trnitá</p>
                <p>+420 603 815 911 • arohacafe@seznam.cz</p>
            </div>
            
            <div class="footer-socials">
                <a href="https://www.facebook.com/Arohabistrocafe" target="_blank" class="footer-social-icon" aria-label="Facebook">
                    📘
                </a>
            </div>
            
            <div class="footer-bottom">
                <p>&copy; 2026 Aroha café. Káva, co dává smysl.</p>
            </div>
        </div>
    </footer>

    <script>
        // Mobile menu toggle
        const menuToggle = document.getElementById('menuToggle');
        const navMenu = document.getElementById('navMenu');
        
        menuToggle.addEventListener('click', () => {
            menuToggle.classList.toggle('active');
            navMenu.classList.toggle('active');
        });
        
        // Close menu when clicking on a link
        document.querySelectorAll('nav ul li a').forEach(link => {
            link.addEventListener('click', () => {
                menuToggle.classList.remove('active');
                navMenu.classList.remove('active');
            });
        });
        
        // Scroll reveal animation
        const reveals = document.querySelectorAll('.reveal');
        
        const revealOnScroll = () => {
            const windowHeight = window.innerHeight;
            
            reveals.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const revealPoint = 100;
                
                if (elementTop < windowHeight - revealPoint) {
                    element.classList.add('active');
                }
            });
        };
        
        window.addEventListener('scroll', revealOnScroll);
        revealOnScroll(); // Initial check
    </script>
</body>
</html>
