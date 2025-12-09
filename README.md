<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link
        href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@400;700&family=Raleway:wght@300;400;500&family=Great+Vibes&display=swap"
        rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/TextPlugin.min.js"></script>
    <style>
        /* Responsive Updates */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --pink: #ff5c8d;
            --purple: #c770ff;
            --gold: #ffd166;
            --light-pink: #ffb8d1;
            --dark: #3a0ca3;
            --light: #fff0f5;
        }

        body {
            font-family: 'Raleway', sans-serif;
            background: linear-gradient(135deg, #3a0ca3 0%, #4361ee 30%, #ff5c8d 70%, #ffb8d1 100%);
            color: white;
            line-height: 1.6;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }

        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background:
                radial-gradient(circle at 20% 80%, rgba(255, 92, 141, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(199, 112, 255, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(255, 209, 102, 0.1) 0%, transparent 50%);
            z-index: -1;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header Section */
        .header {
            text-align: center;
            padding: 40px 0 60px;
            position: relative;
        }

        .anniversary-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            background: linear-gradient(45deg, var(--pink), var(--purple));
            color: white;
            padding: 12px 25px;
            border-radius: 50px;
            font-weight: bold;
            font-size: 1.2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            z-index: 10;
            transform: rotate(5deg);
        }

        .main-title {
            font-family: 'Dancing Script', cursive;
            font-size: 5rem;
            color: var(--gold);
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(255, 209, 102, 0.5);
        }

        .subtitle {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            color: var(--light);
            margin-bottom: 15px;
            font-weight: 300;
        }

        .urdu-title {
            font-family: 'Great Vibes', cursive;
            font-size: 3rem;
            color: var(--light-pink);
            margin: 20px 0;
            letter-spacing: 2px;
        }

        .date-timeline {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            margin: 40px 0;
            flex-wrap: wrap;
        }

        .date-box {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 20px 30px;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: center;
            min-width: 200px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .date-box:hover {
            transform: translateY(-10px);
        }

        .date-year {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--gold);
            margin-bottom: 5px;
        }

        .date-text {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .heart-divider {
            font-size: 2.5rem;
            color: var(--pink);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.2);
            }
        }

        /* Love Words Section */
        .love-words-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin: 50px 0;
            padding: 30px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .love-word {
            background: linear-gradient(45deg, var(--pink), var(--purple));
            padding: 15px 25px;
            border-radius: 50px;
            font-size: 1.5rem;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            transform: translateY(50px);
            opacity: 0;
        }

        /* Gallery Section */
        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 3rem;
            text-align: center;
            margin: 60px 0 40px;
            color: var(--light);
            position: relative;
        }

        .section-title::after {
            content: "";
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 150px;
            height: 3px;
            background: linear-gradient(to right, var(--pink), var(--gold));
            border-radius: 2px;
        }

        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }

        .photo-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.15);
            transform: translateY(100px);
            opacity: 0;
            transition: transform 0.4s ease, box-shadow 0.4s ease;
            cursor: pointer;
        }

        .photo-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
        }

        .photo-frame {
            height: 300px;
            overflow: hidden;
            position: relative;
        }

        .photo-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.7s ease;
        }

        .photo-card:hover .photo-frame img {
            transform: scale(1.1);
        }

        .photo-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            background: linear-gradient(to top, rgba(58, 12, 163, 0.9), transparent);
            padding: 20px;
            color: white;
        }

        .photo-number {
            position: absolute;
            top: 20px;
            left: 20px;
            background: var(--gold);
            color: var(--dark);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        .photo-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.6rem;
            margin-bottom: 5px;
            color: var(--gold);
        }

        .photo-caption {
            font-size: 1rem;
            opacity: 0.9;
        }

        /* Roman Urdu Quotes Section */
        .quotes-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin: 60px 0;
        }

        .quote-card {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            transform: translateX(-100px);
            opacity: 0;
        }

        .quote-card:nth-child(even) {
            transform: translateX(100px);
        }

        .quote-text {
            font-family: 'Great Vibes', cursive;
            font-size: 1.8rem;
            line-height: 1.8;
            color: white;
            text-align: center;
            margin-bottom: 20px;
        }

        .quote-translation {
            font-style: italic;
            text-align: center;
            color: var(--light);
            opacity: 0.8;
            font-size: 1.1rem;
            border-top: 1px dashed rgba(255, 255, 255, 0.3);
            padding-top: 15px;
        }

        /* Message Section */
        .message-box {
            background: linear-gradient(135deg, rgba(255, 92, 141, 0.2), rgba(199, 112, 255, 0.2));
            backdrop-filter: blur(10px);
            border-radius: 25px;
            padding: 50px;
            margin: 60px 0;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
            transform: scale(0.9);
            opacity: 0;
        }

        .message-box::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(to right, var(--pink), var(--gold), var(--purple));
        }

        .message-title {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            color: var(--gold);
            margin-bottom: 30px;
            text-align: center;
        }

        .message-content {
            font-size: 1.2rem;
            line-height: 1.8;
            margin-bottom: 30px;
            text-align: center;
        }

        .signature {
            font-family: 'Dancing Script', cursive;
            font-size: 3rem;
            color: var(--pink);
            text-align: center;
            margin-top: 30px;
        }

        /* Floating Elements */
        .floating-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .heart {
            position: absolute;
            color: var(--pink);
            opacity: 0;
            font-size: 24px;
            animation: floatUp 15s linear infinite;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }

            10% {
                opacity: 0.7;
            }

            90% {
                opacity: 0.7;
            }

            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 40px 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            margin-top: 60px;
        }

        .footer-text {
            font-size: 1.1rem;
            opacity: 0.8;
            margin-bottom: 10px;
        }

        .footer-heart {
            color: var(--pink);
            font-size: 1.5rem;
            animation: heartbeat 1.5s infinite;
        }

        @keyframes heartbeat {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.2);
            }
        }

        /* Edit Button */
        .edit-btn {
            display: block;
            margin: 40px auto;
            padding: 15px 40px;
            background: linear-gradient(to right, var(--pink), var(--purple));
            color: white;
            border: none;
            border-radius: 50px;
            font-family: 'Raleway', sans-serif;
            font-size: 1.2rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
        }

        .edit-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }
@media (max-width: 1100px) {
    .main-title {
        font-size: 4rem;
    }

    .urdu-title {
        font-size: 2.5rem;
    }
    
    .section-title {
        font-size: 2.8rem;
    }
}

@media (max-width: 768px) {
    .main-title {
        font-size: 3.5rem;
    }

    .subtitle {
        font-size: 1.8rem;
    }

    .urdu-title {
        font-size: 2.5rem;
    }
    
    .section-title {
        font-size: 2.5rem;
        margin: 40px 0 30px;
    }
    
    .date-timeline {
        gap: 15px;
        margin: 30px 0;
    }

    .date-box {
        min-width: 160px;
        padding: 20px 25px;
    }

    .date-year {
        font-size: 2.2rem;
    }
    
    .date-text {
        font-size: 1.3rem;
    }
    
    .heart-divider {
        font-size: 3rem;
    }

    .gallery-container {
        grid-template-columns: 1fr;
        gap: 25px;
        margin-bottom: 40px;
    }
    
    .photo-frame {
        height: 350px;
    }
    
    .photo-title {
        font-size: 1.8rem;
    }
    
    .photo-caption {
        font-size: 1.1rem;
    }
    
    .love-word {
        font-size: 1.5rem;
        padding: 15px 25px;
    }
    
    .quote-text {
        font-size: 2rem;
    }
    
    .quote-translation {
        font-size: 1.3rem;
    }
    
    .message-box {
        padding: 40px;
        margin: 40px 0;
    }
    
    .message-title {
        font-size: 2.2rem;
    }
    
    .message-content {
        font-size: 1.3rem;
    }
    
    .signature {
        font-size: 2.5rem;
    }
    
    .edit-btn {
        font-size: 1.3rem;
        padding: 18px 45px;
    }
    
    .footer-text {
        font-size: 1.2rem;
    }
}

@media (max-width: 480px) {
    .container {
        padding: 15px;
    }
    
    .main-title {
        font-size: 2.8rem;
        margin-bottom: 15px;
    }

    .subtitle {
        font-size: 1.5rem;
    }

    .urdu-title {
        font-size: 2rem;
        margin: 15px 0;
    }
    
    .section-title {
        font-size: 2rem;
        margin: 30px 0 20px;
    }
    
    .date-timeline {
        flex-direction: column;
        gap: 20px;
    }
    
    .date-box {
        width: 100%;
        max-width: 280px;
        padding: 25px;
    }
    
    .date-year {
        font-size: 2.5rem;
    }
    
    .date-text {
        font-size: 1.5rem;
    }
    
    .heart-divider {
        font-size: 2.5rem;
        transform: rotate(90deg);
    }
    
    .photo-frame {
        height: 300px;
    }
    
    .photo-title {
        font-size: 1.6rem;
    }
    
    .photo-caption {
        font-size: 1rem;
    }
    
    .love-words-container {
        padding: 20px;
        gap: 15px;
    }
    
    .love-word {
        font-size: 1.3rem;
        padding: 12px 22px;
    }
    
    .quotes-container {
        gap: 20px;
    }
    
    .quote-card {
        padding: 25px;
    }
    
    .quote-text {
        font-size: 1.7rem;
    }
    
    .quote-translation {
        font-size: 1.1rem;
    }
    
    .message-box {
        padding: 30px 20px;
    }
    
    .message-title {
        font-size: 1.8rem;
    }
    
    .message-content {
        font-size: 1.1rem;
    }
    
    .signature {
        font-size: 2rem;
    }
    
    .edit-btn {
        font-size: 1.1rem;
        padding: 15px 35px;
    }
    
    .footer-text {
        font-size: 1rem;
    }
}

@media (max-width: 360px) {
    .main-title {
        font-size: 2.5rem;
    }
    
    .section-title {
        font-size: 1.8rem;
    }
    
    .photo-frame {
        height: 250px;
    }
    
    .love-word {
        font-size: 1.1rem;
        padding: 10px 18px;
    }
    
    .quote-text {
        font-size: 1.5rem;
    }
}

/* Make sure elements are easily clickable on mobile */
@media (hover: none) and (pointer: coarse) {
    .love-word,
    .photo-card,
    .quote-card,
    .edit-btn {
        min-height: 44px; /* Minimum touch target size */
    }
    
    .love-word,
    .edit-btn {
        padding: 15px 25px !important;
    }
}

/* Landscape orientation adjustments */
@media (max-height: 500px) and (orientation: landscape) {
    .header {
        padding: 20px 0 30px;
    }

    .main-title {
        font-size: 2.5rem;
        margin-bottom: 10px;
    }

    .photo-frame {
        height: 200px;
    }

    .message-box {
        padding: 20px;
        margin: 20px 0;
    }
}

/* Modal Styles */
.modal {
    display: none;
    position: fixed;
    z-index: 1000;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0, 0, 0, 0.9);
    backdrop-filter: blur(5px);
}

.modal-content {
    margin: auto;
    display: block;
    width: 80%;
    max-width: 700px;
    max-height: 80vh;
    object-fit: contain;
}

.close {
    position: absolute;
    top: 15px;
    right: 35px;
    color: #f1f1f1;
    font-size: 40px;
    font-weight: bold;
    transition: 0.3s;
    cursor: pointer;
}

.close:hover,
.close:focus {
    color: #bbb;
    text-decoration: none;
}

#caption {
    margin: auto;
    display: block;
    width: 80%;
    max-width: 700px;
    text-align: center;
    color: #ccc;
    padding: 10px 0;
    height: 150px;
}

.modal-content, #caption {
    animation-name: zoom;
    animation-duration: 0.6s;
}

@keyframes zoom {
    from {transform:scale(0)}
    to {transform:scale(1)}
}
    </style>
</head>
<body>
      <!-- Floating Hearts Background -->
    <div class="floating-hearts" id="floatingHearts"></div>

    <div class="container">
        <!-- Header Section -->
        <header class="header">
            <div class="anniversary-badge">
                <i class="fas fa-heart"></i> 4 Years Together <i class="fas fa-heart"></i>
            </div>

            <h1 class="main-title" id="mainTitle">Four Years of Love</h1>

            <div class="subtitle">From 10 December 2021 to 10 December 2025</div>

            <div class="urdu-title" id="urduTitle">4th Anniversary</div>

            <div class="date-timeline">
                <div class="date-box">
                    <div class="date-year">2021</div>
                    <div class="date-text">When We Met</div>
                </div>

                <div class="heart-divider">❤️</div>

                <div class="date-box">
                    <div class="date-year">2025</div>
                    <div class="date-text">4 Years Strong</div>
                </div>
            </div>
        </header>

        <!-- Love Words Section -->
        <h2 class="section-title">What I Call You</h2>

        <div class="love-words-container" id="loveWords">
            <!-- Love words will be added by JavaScript -->
        </div>

        <!-- Gallery Section -->
        <h2 class="section-title">Our Beautiful Journey</h2>

        <div class="gallery-container" id="gallery">
            <!-- Photo cards will be added by JavaScript -->
        </div>

        <!-- Roman Urdu Quotes Section -->
        <h2 class="section-title">My Feelings for You</h2>

        <div class="quotes-container" id="quotesContainer">
            <!-- Quotes will be added by JavaScript -->
        </div>

        <!-- Message Section -->
        <div class="message-box" id="messageBox">
            <h2 class="message-title">To My Everything</h2>

            <div class="message-content">
                <p>My dearest love, these past four years with you have been the most beautiful journey of my life. From
                    the moment we met on that cold December day in 2021, you've filled my world with warmth, laughter,
                    and unconditional love.</p>

                <p>Mny kabhi Socha hi nh tha k hum itna time sth guzarengy or inshallah agy bhi guzarengy....or isi trh
                    aik dusre se Pyr krty rhengy or zyada hr din ye Pyr brhta jyega or hum or yada qareeb ajyengy aik
                    dusre k...or inshallah isi trh aik din humara nikkah hojyega or Hume pta bhi nh lgega k kese guzr
                    gya wqt pr actually Hume pta lga h k kese mushkilo se guzr rha h wqt lkn koi nh humara ye intzr aik
                    din Hume aik dusre k qareeb krdega or koi duriya nh bs hum sth hongy......Meri SB se bari
                    Khushnseebi ye h k mere pss ap ho apka Pyr h apki loyalty h mere pss isse brh kr mere Liye or Kya hi
                    acha ho skta hai....isi trh bs hum aik dusre k sth rhy aik dusre ko Pyr kren or aik dusre ka sth den
                    achy or Bure wqt mai or bs Khush rhen aik dusre k sth🥺🥺🥺❤️❤️❤️❤️❤️🥺❤️❤️🥺🥺❤️❤️❤️🥺❤️ my
                    confidant, and my greatest supporter. Through all our adventures, quiet moments, challenges, and
                    celebrations, you've been my constant source of strength and happiness.</p>

                <p>These six pictures represent just a fraction of our beautiful memories, but each one holds a special
                    place in my heart. I can't wait to create countless more memories with you in the years to come.</p>

                <p>Thank you for being the amazing man that you are. Thank you for your patience, your kindness, and
                    your unwavering love. Here's to us, to our love, and to forever.</p>
            </div>

            <div class="signature">Always Yours</div>
        </div>

        <!-- Edit Button -->
       

        <!-- Footer -->
        <footer>
            <div class="footer-text">Made with <span class="footer-heart">❤️</span> for our 4th anniversary</div>
            <div class="footer-text">10 December 2021 - 10 December 2025</div>
            <div class="footer-text">A gift from me to you, meri jaan</div>
        </footer>
    </div>

    <!-- Image Modal -->
    <div id="imageModal" class="modal">
        <span class="close">&times;</span>
        <img class="modal-content" id="modalImage">
        <div id="caption"></div>
    </div>

<script>
    // Roman Urdu quotes with translations (from girl's perspective)
    const romanUrduQuotes = [
        {
            quote: "Tum meri zindagi ka sabse khoobsurat hissa ho.",
            translation: "You are the most beautiful part of my life."
        },
        {
            quote: "Main tumhare bina apni zindagi ka soch bhi nahi sakti.",
            translation: "I can't even imagine my life without you."
        },
        {
            quote: "Har lamha tumhare saath guzara hua lamha zindagi ka sabse acha tohfa hai.",
            translation: "Every moment spent with you is life's best gift."
        },
        {
            quote: "Tum meri khushi ho, meri duniya ho, meri sab kuch ho.",
            translation: "You are my happiness, my world, my everything."
        },
        {
            quote: "Char saal ho gaye hain, par main ab bhi tumhe pehle din ki tarah chahti hoon.",
            translation: "It's been 4 years, but I still love you like the first day."
        },
        {
            quote: "Tumhari muskurahat meri duniya ki sabse keemti cheez hai.",
            translation: "Your smile is the most precious thing in my world."
        }
    ];

    // Love words/pet names (from girl to boyfriend)
    const loveWords = [
        "Meri Jaan", "Mera Shehzada", "Mera Bacha", "Mera Sher",
        "Mera Kaka", "Mera Pyaar", "Meri Zindagi", "Meri Duniya",
        "Mera Humsafar", "Mera Sab Kuch", "Meri Pehli Aur Aakhri Mohabbat",
        "Mera Dil", "Mera Sapna", "Meri Khushi"
    ];

    // Photo data - replace with your own images
    const photoData = [
        {
            id: 1,
            url: "IMG_1651.PNG",
            title: "My Happiness",
            caption: "The day my life changed forever - 10 Dec 2021 with you"
        },
        {
            id: 2,
            url: "IMG_3396.JPG",
            title: "Your Beautiful Smile",
            caption: "The smile that makes my heart skip a beat"
        },
        {
            id: 3,
            url: "in.jpg",
            title: "Our First Year",
            caption: "Celebrating one year of us together"
        },
        {
            id: 4,
            url: "ten.jpg",
            title: "Quiet Moments",
            caption: "The simple moments I cherish the most"
        },
        {
            id: 5,
            url: "IMG_2825.JPG",
            title: "My Everything",
            caption: "You are my past, present and future"
        },
        {
            id: 6,
            url: "one.jpg",
            title: "Forever to Come",
            caption: "So many more memories to make together"
        }
    ];

    // Create floating hearts
    function createFloatingHearts() {
        const heartsContainer = document.getElementById('floatingHearts');
        const colors = ['#ff5c8d', '#c770ff', '#ffd166', '#ffb8d1'];

        for (let i = 0; i < 30; i++) {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤';
            heart.style.left = `${Math.random() * 100}%`;
            heart.style.fontSize = `${Math.random() * 25 + 15}px`;
            heart.style.color = colors[Math.floor(Math.random() * colors.length)];
            heart.style.animationDelay = `${Math.random() * 10}s`;
            heart.style.animationDuration = `${Math.random() * 10 + 10}s`;
            heartsContainer.appendChild(heart);
        }
    }

    // Create love words
    function createLoveWords() {
        const container = document.getElementById('loveWords');

        loveWords.forEach((word, index) => {
            const wordElement = document.createElement('div');
            wordElement.className = 'love-word';
            wordElement.textContent = word;
            wordElement.style.animationDelay = `${index * 0.1}s`;
            container.appendChild(wordElement);
        });
    }

    // Create gallery with clickable images
    function createGallery() {
        const gallery = document.getElementById('gallery');

        photoData.forEach(photo => {
            const card = document.createElement('div');
            card.className = 'photo-card';
            card.innerHTML = `
                <div class="photo-frame">
                    <div class="photo-number">${photo.id}</div>
                    <img src="${photo.url}" alt="${photo.title}" data-id="${photo.id}" class="gallery-image">
                    <div class="photo-overlay">
                        <h3 class="photo-title">${photo.title}</h3>
                        <p class="photo-caption">${photo.caption}</p>
                    </div>
                </div>
            `;
            gallery.appendChild(card);
        });
    }

    // Create Roman Urdu quotes
    function createRomanUrduQuotes() {
        const container = document.getElementById('quotesContainer');

        romanUrduQuotes.forEach((quote, index) => {
            const quoteCard = document.createElement('div');
            quoteCard.className = 'quote-card';
            quoteCard.innerHTML = `
                <div class="quote-text">"${quote.quote}"</div>
                <div class="quote-translation">"${quote.translation}"</div>
            `;
            container.appendChild(quoteCard);
        });
    }

    // Image Lightbox Functionality
    function setupImageLightbox() {
        // Get modal elements
        const modal = document.getElementById('imageModal');
        const modalImg = document.getElementById('modalImage');
        const captionText = document.getElementById('caption');
        const closeBtn = document.querySelector('.close');
        let currentImageIndex = 0;

        // Function to open modal with specific image
        function openModal(imageIndex) {
            const photo = photoData[imageIndex];
            currentImageIndex = imageIndex;
            
            modal.style.display = "block";
            modalImg.src = photo.url;
            modalImg.alt = photo.title;
            captionText.innerHTML = `
                <h3 style="color: var(--gold); margin-bottom: 10px; font-size: 1.5rem;">${photo.title}</h3>
                <p style="font-size: 1.1rem; opacity: 0.9;">${photo.caption}</p>
            `;
            
            // Add zoom animation
            gsap.fromTo(modalImg, 
                { scale: 0.8, opacity: 0 },
                { scale: 1, opacity: 1, duration: 0.5, ease: "power3.out" }
            );
        }

        // Function to close modal
        function closeModal() {
            gsap.to(modal, {
                opacity: 0,
                duration: 0.3,
                onComplete: () => {
                    modal.style.display = "none";
                    modal.style.opacity = 1;
                }
            });
        }

        // Function to show next image
        function showNextImage() {
            currentImageIndex = (currentImageIndex + 1) % photoData.length;
            updateModalImage();
        }

        // Function to show previous image
        function showPrevImage() {
            currentImageIndex = (currentImageIndex - 1 + photoData.length) % photoData.length;
            updateModalImage();
        }

        // Function to update modal image with transition
        function updateModalImage() {
            const photo = photoData[currentImageIndex];
            
            // Fade out current image
            gsap.to(modalImg, {
                opacity: 0,
                duration: 0.2,
                onComplete: () => {
                    // Update image and caption
                    modalImg.src = photo.url;
                    modalImg.alt = photo.title;
                    captionText.innerHTML = `
                        <h3 style="color: var(--gold); margin-bottom: 10px; font-size: 1.5rem;">${photo.title}</h3>
                        <p style="font-size: 1.1rem; opacity: 0.9;">${photo.caption}</p>
                    `;
                    
                    // Fade in new image
                    gsap.to(modalImg, {
                        opacity: 1,
                        duration: 0.3
                    });
                }
            });
        }

        // Add click event to all photo cards
        document.querySelectorAll('.photo-card').forEach((card, index) => {
            card.addEventListener('click', function() {
                openModal(index);
            });
        });

        // Close modal when clicking the close button
        closeBtn.addEventListener('click', closeModal);

        // Close modal when clicking outside the image
        modal.addEventListener('click', function(event) {
            if (event.target === modal) {
                closeModal();
            }
        });

        // Keyboard navigation
        document.addEventListener('keydown', function(event) {
            if (modal.style.display === "block") {
                switch(event.key) {
                    case 'Escape':
                        closeModal();
                        break;
                    case 'ArrowRight':
                        showNextImage();
                        break;
                    case 'ArrowLeft':
                        showPrevImage();
                        break;
                }
            }
        });

        // Add navigation buttons to modal
        const prevButton = document.createElement('button');
        prevButton.innerHTML = '❮';
        prevButton.style.cssText = `
            position: absolute;
            top: 50%;
            left: 20px;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            font-size: 30px;
            padding: 15px;
            cursor: pointer;
            border-radius: 50%;
            transition: all 0.3s;
            z-index: 1001;
        `;

        const nextButton = document.createElement('button');
        nextButton.innerHTML = '❯';
        nextButton.style.cssText = `
            position: absolute;
            top: 50%;
            right: 20px;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            font-size: 30px;
            padding: 15px;
            cursor: pointer;
            border-radius: 50%;
            transition: all 0.3s;
            z-index: 1001;
        `;

        // Add hover effects
        prevButton.addEventListener('mouseenter', () => {
            prevButton.style.background = 'rgba(255, 92, 141, 0.8)';
            prevButton.style.transform = 'translateY(-50%) scale(1.1)';
        });
        prevButton.addEventListener('mouseleave', () => {
            prevButton.style.background = 'rgba(0, 0, 0, 0.5)';
            prevButton.style.transform = 'translateY(-50%) scale(1)';
        });

        nextButton.addEventListener('mouseenter', () => {
            nextButton.style.background = 'rgba(255, 92, 141, 0.8)';
            nextButton.style.transform = 'translateY(-50%) scale(1.1)';
        });
        nextButton.addEventListener('mouseleave', () => {
            nextButton.style.background = 'rgba(0, 0, 0, 0.5)';
            nextButton.style.transform = 'translateY(-50%) scale(1)';
        });

        // Add click events to navigation buttons
        prevButton.addEventListener('click', showPrevImage);
        nextButton.addEventListener('click', showNextImage);

        // Add buttons to modal
        modal.appendChild(prevButton);
        modal.appendChild(nextButton);

        // Add image counter
        const counter = document.createElement('div');
        counter.id = 'imageCounter';
        counter.style.cssText = `
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 14px;
            z-index: 1001;
        `;
        modal.appendChild(counter);

        // Function to update counter
        function updateCounter() {
            counter.textContent = `${currentImageIndex + 1} / ${photoData.length}`;
        }

        // Update counter when opening modal
        modal.addEventListener('click', updateCounter);
        
        // Update counter initially
        setTimeout(updateCounter, 100);

        // Add swipe support for mobile
        let touchStartX = 0;
        let touchEndX = 0;
        
        modal.addEventListener('touchstart', function(e) {
            touchStartX = e.changedTouches[0].screenX;
        });
        
        modal.addEventListener('touchend', function(e) {
            touchEndX = e.changedTouches[0].screenX;
            handleSwipe();
        });
        
        function handleSwipe() {
            const swipeThreshold = 50;
            const diff = touchStartX - touchEndX;
            
            if (Math.abs(diff) > swipeThreshold) {
                if (diff > 0) {
                    showNextImage();
                } else {
                    showPrevImage();
                }
            }
        }

        // Add zoom functionality for desktop (double click)
        let isZoomed = false;
        
        modalImg.addEventListener('dblclick', function() {
            if (!isZoomed) {
                // Zoom in
                this.style.transform = 'scale(1.5)';
                this.style.cursor = 'zoom-out';
                isZoomed = true;
            } else {
                // Zoom out
                this.style.transform = 'scale(1)';
                this.style.cursor = 'zoom-in';
                isZoomed = false;
            }
        });
    }

    // GSAP Animations
    function setupAnimations() {
        // Register GSAP plugins
        gsap.registerPlugin(ScrollTrigger, TextPlugin);

        // Main title animation
        gsap.from("#mainTitle", {
            duration: 2,
            y: -100,
            opacity: 0,
            ease: "elastic.out(1, 0.5)",
            delay: 0.5
        });

        // Urdu title animation
        gsap.from("#urduTitle", {
            duration: 2,
            y: 50,
            opacity: 0,
            ease: "power3.out",
            delay: 1
        });

        // Date boxes animation
        gsap.from(".date-box", {
            duration: 1.5,
            y: 50,
            opacity: 0,
            stagger: 0.3,
            ease: "power3.out",
            delay: 1.5
        });

        // Love words animation
        gsap.to(".love-word", {
            duration: 1,
            y: 0,
            opacity: 1,
            stagger: 0.1,
            ease: "power3.out",
            scrollTrigger: {
                trigger: "#loveWords",
                start: "top 80%",
                toggleActions: "play none none reverse"
            }
        });

        // Photo cards animation
        gsap.to(".photo-card", {
            duration: 1.2,
            y: 0,
            opacity: 1,
            stagger: 0.2,
            ease: "power3.out",
            scrollTrigger: {
                trigger: "#gallery",
                start: "top 70%",
                toggleActions: "play none none reverse"
            }
        });

        // Quote cards animation
        gsap.to(".quote-card", {
            duration: 1.2,
            x: 0,
            opacity: 1,
            stagger: 0.3,
            ease: "power3.out",
            scrollTrigger: {
                trigger: "#quotesContainer",
                start: "top 70%",
                toggleActions: "play none none reverse"
            }
        });

        // Message box animation
        gsap.to("#messageBox", {
            duration: 1.5,
            scale: 1,
            opacity: 1,
            ease: "elastic.out(1, 0.5)",
            scrollTrigger: {
                trigger: "#messageBox",
                start: "top 80%",
                toggleActions: "play none none reverse"
            }
        });

        // Continuous subtle animations
        gsap.to(".main-title", {
            duration: 3,
            y: "+=10",
            repeat: -1,
            yoyo: true,
            ease: "sine.inOut"
        });

        // Heart pulse animation
        gsap.to(".heart-divider", {
            duration: 2,
            scale: 1.3,
            repeat: -1,
            yoyo: true,
            ease: "sine.inOut"
        });
    }

    // Initialize everything when page loads
    document.addEventListener('DOMContentLoaded', function () {
        createFloatingHearts();
        createLoveWords();
        createGallery();
        createRomanUrduQuotes();
        setupAnimations();
        setupImageLightbox(); // Initialize image lightbox

        // Add click effect to love words
        document.querySelectorAll('.love-word').forEach(word => {
            word.addEventListener('click', function () {
                gsap.to(this, {
                    duration: 0.3,
                    scale: 1.3,
                    yoyo: true,
                    repeat: 1,
                    ease: "power2.inOut"
                });
            });
        });

        // Add hover effect to photo cards
        document.querySelectorAll('.photo-card').forEach(card => {
            card.addEventListener('mouseenter', function () {
                gsap.to(this, {
                    duration: 0.3,
                    scale: 1.02,
                    ease: "power2.out"
                });
            });

            card.addEventListener('mouseleave', function () {
                gsap.to(this, {
                    duration: 0.3,
                    scale: 1,
                    ease: "power2.out"
                });
            });
        });

        // Add special message on click of anniversary badge
        document.querySelector('.anniversary-badge').addEventListener('click', function () {
            gsap.to(this, {
                duration: 0.5,
                rotate: "+=360",
                scale: 1.2,
                yoyo: true,
                repeat: 1,
                ease: "power2.inOut"
            });

            setTimeout(() => {
                alert("Happy 4th Anniversary, meri jaan! \n\nEvery day with you is a blessing. I love you more than words can express. 💖");
            }, 300);
        });
    });
</script>


</body>
</html>
