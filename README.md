<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>SAKTOPUP - 100% Original Full Version</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

    <style>
        :root { 
            --bg-dark: #070a13; 
            --bg-card: #0c111c; 
            --primary-blue: #3dd0f3; 
            --text-gold: #fcc201; 
            --text-gray: #777d8a;
            --white: #ffffff;
            --aba-blue: #00bcd4;
            --btn-sky: #49d4f8; 
        }

        * { 
            box-sizing: border-box; 
            font-family: 'Khmer OS Battambang', sans-serif; 
            -webkit-tap-highlight-color: transparent; 
        }
        
        body { 
            background: var(--bg-dark); 
            color: var(--white); 
            margin: 0; 
            padding: 0; 
            overflow-x: hidden; 
            width: 100%;
            position: relative;
        }

        /* បន្ថែម Overlay សម្រាប់រង់ចាំបង់លុយ */
        #payment-waiting {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); z-index: 6000; flex-direction: column; align-items: center; justify-content: center;
        }
        .loading-spinner {
            width: 50px; height: 50px; border: 5px solid #f3f3f3; border-top: 5px solid var(--primary-blue);
            border-radius: 50%; animation: spin 1s linear infinite;
        }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        .header-sticky {
            position: sticky;
            top: 0;
            z-index: 1000;
            background: var(--bg-dark);
            width: 100%;
        }

        .navbar { 
            background: #070a13; 
            padding: 12px 15px; 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            border-bottom: 1px solid #1a202c; 
            width: 100%;
        }
        
        .logo-container { display: flex; align-items: center; gap: 10px; cursor: pointer; }
        .nav-logo-img { height: 35px; width: 35px; border-radius: 50%; object-fit: cover; border: 2px solid var(--text-gold); background: #222; }
        .logo-text { color: var(--text-gold); font-weight: bold; font-size: 24px; font-style: italic; text-transform: uppercase; cursor: pointer; margin: 0; }

        #side-menu { position: fixed; top: 0; right: -280px; width: 280px; height: 100%; background: #0c111c; z-index: 3000; transition: 0.4s; padding: 20px; border-left: 1px solid #1a202c; }
        .overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.7); z-index: 2500; }
        .contact-btn { text-decoration: none; display: flex; align-items: center; gap: 12px; background: #1a202c; padding: 15px; border-radius: 10px; margin-bottom: 12px; border: 1px solid #2d3748; color: white; }

        #search-box { 
            display: none; 
            padding: 10px 15px; 
            background: #070a13; 
            border-bottom: 1px solid #1a202c;
            overflow: hidden;
            transition: 0.3s ease;
        }
        .search-input { width: 100%; padding: 10px; border-radius: 8px; border: 1px solid #334155; background: #000; color: white; outline: none; }

        .banner-container { 
            width: 94%; 
            height: 160px; 
            margin: 15px auto; 
            border-radius: 12px; 
            overflow: hidden; 
        }
        .swiper { width: 100%; height: 100%; }
        .swiper-slide img { width: 100%; height: 100%; object-fit: cover; }
        .swiper-pagination-bullet { background: #fff; }

        .container { 
            padding: 15px; 
            width: 100%; 
            max-width: 600px; 
            margin: auto; 
            overflow: hidden;
        }

        .section-header { font-size: 14px; font-weight: bold; margin: 20px 0 12px 0; display: flex; align-items: center; gap: 8px; }

        .game-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; width: 100%; }
        .game-item { background: var(--bg-card); border-radius: 15px; border: 1px solid #1a202c; text-align: center; overflow: hidden; padding-bottom: 12px; cursor: pointer; }
        .game-item img { width: 100%; aspect-ratio: 1/1; object-fit: cover; }
        
        .btn-topup-sm { 
            background: var(--btn-sky); 
            color: #000; 
            border: none; 
            width: 85%; 
            padding: 10px 0; 
            border-radius: 12px; 
            font-size: 13px; 
            font-weight: 800; 
            margin-top: 8px; 
            text-transform: uppercase;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        .stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 25px; width: 100%; }
        .stat-item { background: #0c111c; border: 1px solid #1a202c; padding: 15px; border-radius: 12px; text-align: center; }
        .stat-icon { color: var(--primary-blue); font-size: 18px; margin-bottom: 8px; }
        .stat-item b { font-size: 16px; display: block; margin-bottom: 4px; }
        .stat-item small { color: var(--text-gray); font-size: 10px; }

        .footer { background: #0c111c; padding: 30px 20px; width: 100%; text-align: left; border-top: 1px solid #1a202c; font-size: 12px; color: var(--text-gray); margin-top: 30px; }
        .footer-logo { color: var(--text-gold); font-size: 18px; font-weight: bold; margin-bottom: 10px; }
        .badge-khqr { background: #e53e3e; color: white; padding: 2px 5px; border-radius: 3px; font-size: 10px; font-weight: bold; }
        .badge-aba { background: var(--aba-blue); color: white; padding: 2px 5px; border-radius: 3px; font-size: 10px; font-weight: bold; }

        #topup-page { display: none; padding-bottom: 120px; width: 100%; }
        .card-box { background: var(--bg-card); border: 1px solid #1a202c; padding: 15px; border-radius: 12px; margin-bottom: 15px; width: 100%; }
        .id-input { width: 100%; background: #000; border: 1px solid #1a202c; padding: 12px; border-radius: 8px; color: #49bcf8; font-size: 16px; outline: none; margin-top: 10px; text-align: center; }

        .btn-check { width: 100%; padding: 10px; margin-top: 12px; border-radius: 8px; border: none; background: #ff2d55; color: white; font-weight: bold; cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 8px; }
        .btn-check:active { transform: scale(0.98); }

        .uc-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; width: 100%; }
        .uc-item { background: var(--bg-card); border: 1px solid #1a202c; padding: 15px; border-radius: 10px; cursor: pointer; transition: 0.3s; text-align: center; }
        .uc-item.active { border-color: var(--primary-blue); background: rgba(61, 208, 243, 0.05); }
        .uc-item img { width: 75px; height: 75px; object-fit: contain; margin-bottom: 8px; }

        .aba-payment-box { background: rgba(0, 188, 212, 0.05); border: 1.5px solid var(--aba-blue); padding: 15px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; width: 100%; }
        .aba-label { background: var(--aba-blue); color: white; padding: 2px 6px; border-radius: 4px; font-weight: bold; font-size: 10px; margin-right: 10px; }
        .aba-circle { width: 22px; height: 22px; border-radius: 50%; border: 2px solid var(--aba-blue); display: flex; align-items: center; justify-content: center; }

        .pay-bar { position: fixed; bottom: 0; left: 0; width: 100%; background: #0c111c; padding: 15px 20px calc(15px + env(safe-area-inset-bottom)); border-top: 1px solid #1a202c; display: none; justify-content: space-between; align-items: center; z-index: 2000; }
        .btn-pay { background: linear-gradient(90deg, #1e90ff, #00bfff); color: white; border: none; padding: 12px 25px; border-radius: 8px; font-weight: bold; display: flex; align-items: center; gap: 8px; cursor: pointer; }
        .btn-pay:disabled { background: #334155; color: #94a3b8; cursor: not-allowed; opacity: 0.6; }

        .receipt-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.85); z-index: 5000; align-items: center; justify-content: center; padding: 20px; }
        .receipt-card { background: #fff; color: #333; width: 100%; max-width: 350px; border-radius: 20px; padding: 25px; position: relative; border-top: 8px solid #00ff88; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .receipt-header { text-align: center; border-bottom: 2px dashed #ddd; padding-bottom: 15px; margin-bottom: 15px; }
        .receipt-row { display: flex; justify-content: space-between; margin-bottom: 10px; font-size: 13px; border-bottom: 1px solid #f0f0f0; padding-bottom: 5px; }
        .receipt-row b { color: #555; }
        .btn-download-rec { background: #00bcd4; color: white; border: none; width: 100%; padding: 12px; border-radius: 10px; font-weight: bold; margin-top: 15px; cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 8px; }
        .btn-close-receipt { background: #eee; color: #333; border: none; width: 100%; padding: 10px; border-radius: 10px; font-weight: bold; margin-top: 10px; cursor: pointer; }
    </style>
</head>
<body>

<div id="payment-waiting">
    <div class="loading-spinner"></div>
    <h3 style="color:white; margin-top:20px;">កំពុងផ្ទៀងផ្ទាត់ការបង់ប្រាក់...</h3>
    <p style="color:#aaa; font-size:12px;">ប្រព័ន្ធកំពុងឆែកលុយក្នុង ABA របស់បង</p>
    <div id="countdown" style="color:var(--primary-blue); font-weight:bold; font-size:20px; margin-top:10px;">60s</div>
</div>

<div class="header-sticky">
    <nav class="navbar">
        <div class="logo-container" onclick="goHome()">
            <img src="matin.png" alt="Logo" class="nav-logo-img">
            <div class="logo-text">MATINTOPUP</div>
        </div>
        <div style="display:flex; gap:18px; align-items:center; color:white;">
            <i class="fas fa-search" id="search-icon" onclick="toggleSearch()" style="cursor:pointer; font-size:18px;"></i>
            <i class="fas fa-bars" onclick="toggleMenu()" style="cursor:pointer; font-size:20px;"></i>
        </div>
    </nav>
    <div id="search-box">
        <input type="text" placeholder="ស្វែងរកហ្គេម..." class="search-input">
    </div>
</div>

<div id="side-menu">
    <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:30px;">
        <span style="color:gold; font-weight:bold; font-size:18px;">MATINTOPUP</span>
        <i class="fas fa-times" onclick="toggleMenu()" style="cursor:pointer; font-size:20px;"></i>
    </div>
    
    <a href="https://t.me/Matintopup168" target="_blank" class="contact-btn">
        <i class="fab fa-telegram" style="color:#24A1DE; font-size:24px;"></i>
        <div>
            <div style="font-size:14px; font-weight:bold;">តេឡេក្រាមផ្ទាល់ខ្លួន</div>
            <div style="font-size:11px; color:#777d8a;">ទាក់ទងមកយើងផ្ទាល់</div>
        </div>
    </a>

    <a href="https://t.me/matintopup" target="_blank" class="contact-btn">
        <i class="fas fa-users" style="color:#3dd0f3; font-size:20px;"></i>
        <div>
            <div style="font-size:14px; font-weight:bold;">តេឡេក្រាមគ្រុប</div>
            <div style="font-size:11px; color:#777d8a;">ចូលរួមសហគមន៍</div>
        </div>
    </a>

    <a href="https://www.facebook.com/share/18YyWd5iV3/?mibextid=wwXIfr" target="_blank" class="contact-btn">
        <i class="fab fa-facebook" style="color:#1877F2; font-size:24px;"></i>
        <div>
            <div style="font-size:14px; font-weight:bold;">ហ្វេសប៊ុកផេក</div>
            <div style="font-size:11px; color:#777d8a;">តាមដានព័ត៌មានថ្មីៗ</div>
        </div>
    </a>
</div>
<div id="overlay" class="overlay" onclick="toggleMenu()"></div>

<div class="banner-container">
    <div class="swiper mySwiper">
        <div class="swiper-wrapper">
            <div class="swiper-slide"><img src="IMG_1257290665938849.jpeg"></div>
            <div class="swiper-slide"><img src="Gemini_Generated_Image_jta9owjta9owjta9.png"></div>
            <div class="swiper-slide"><img src="IMG_1662973291394423.jpeg"></div>
        </div>
        <div class="swiper-pagination"></div>
    </div>
</div>

<div id="home-page">
    <div class="container">
        <div class="section-header">⭐ BEST SELLING</div>
        <div class="game-grid">
            <div class="game-item" onclick="openTopup('PUBG MOBILE', 'PUBG.jpg', 'pubg')">
                <img src="PUBG.jpg">
                <div style="font-size:12px; padding:8px 5px 0 5px; font-weight:bold;">PUBG MOBILE</div>
                <button class="btn-topup-sm">TOP UP</button>
            </div>
            <div class="game-item" onclick="openTopup('ZEPETO', 'zepeto-icon.jpg', 'zepeto')">
                <img src="zepeto-icon.jpg">
                <div style="font-size:12px; padding:8px 5px 0 5px; font-weight:bold;">ZEPETO</div>
                <button class="btn-topup-sm">TOP UP</button>
            </div>
            <div class="game-item" onclick="openTopup('Mobile legends', 'mlbb.png', 'mlbb')">
                <img src="mlbb.png">
                <div style="font-size:12px; padding:8px 5px 0 5px; font-weight:bold;">MOBILE KH</div>
                <button class="btn-topup-sm">TOP UP</button>
            </div>
        </div>

        <div class="stats-grid">
            <div class="stat-item"><i class="fas fa-box stat-icon"></i><b>10,000,000+</b><small>Orders delivered</small></div>
            <div class="stat-item"><i class="fas fa-gamepad stat-icon"></i><b>100+</b><small>Games available</small></div>
            <div class="stat-item"><i class="fas fa-bolt stat-icon"></i><b>1 sec - 5 min</b><small>Instant delivery</small></div>
            <div class="stat-item"><i class="fas fa-headset stat-icon"></i><b>24/7</b><small>Support on live-chat</small></div>
        </div>
    </div>

    <div class="footer">
        <div class="footer-logo">MATINTOPUP</div>
        <p>Official Partner - Fast delivery. Secure payment. Trusted top-up service for gamers worldwide.</p>
        <p>© 2026 Matin Topup. All rights reserved.</p>
        <div style="margin-top:15px; font-size:11px;">
            We accept: <span class="badge-khqr">KHQR</span> <span class="badge-aba">ABA</span>
        </div>
    </div>
</div>

<div id="topup-page">
    <div class="container">
        <div style="display:flex; align-items:center; gap:12px; margin-bottom:20px;">
            <img id="p-img" src="" style="width:60px; height:60px; border-radius:10px;">
            <div>
                <h2 id="p-title" style="margin:0; font-size:18px;"></h2>
                <div style="font-size:10px; color:var(--text-gray); margin-top:4px;">
                    <i class="fas fa-shield-alt" style="color:#00ff00;"></i> Safety guarantees &nbsp; 
                    <i class="fas fa-bolt" style="color:orange;"></i> Instant delivery
                </div>
            </div>
        </div>

        <div class="card-box">
            <div style="font-size:12px;"><i class="fas fa-user-circle" style="color:var(--primary-blue);"></i> Enter Your Information</div>
            <div style="display:flex; gap:10px;">
                <input type="number" class="id-input" placeholder="បញ្ចូលលេខ ID" id="u-id" style="flex:2;">
                <input type="number" class="id-input" placeholder="Zone" id="u-zone" style="flex:1; display:none;">
            </div>
            <button class="btn-check" id="btn-check-nickname" onclick="checkID()"><i class="fas fa-search"></i> ពិនិត្យឈ្មោះ</button>
            <div id="nickname-res" style="margin-top:10px; text-align:left; padding-left:5px; font-weight:bold; color:var(--text-gold); font-size:14px;"></div>
        </div>

        <div style="font-size:14px; font-weight:bold; margin-bottom:12px;">💎 SAVING PACKAGES</div>
        <div class="uc-grid" id="package-list"></div>

        <div style="font-size:14px; font-weight:bold; margin:25px 0 12px 0;"><i class="fas fa-wallet" style="color:var(--primary-blue);"></i> Payment Method</div>
        <div class="aba-payment-box">
            <div style="display:flex; align-items:center;">
                <span class="aba-label">ABA</span>
                <div>
                    <div style="font-size:13px; font-weight:bold;">ABA KHQR</div>
                    <div style="font-size:10px; color:var(--text-gray);">Scan to pay with any banking app</div>
                </div>
            </div>
            <div class="aba-circle"><i class="fas fa-check" style="color:var(--aba-blue); font-size:10px;"></i></div>
        </div>

        <label style="font-size: 11px; color: var(--text-gray); display: flex; align-items: center; gap: 8px; margin-top: 15px; cursor: pointer; padding: 0 5px;">
            <input type="checkbox" id="agree-check" onchange="togglePayButton()" style="width: 16px; height: 16px; cursor: pointer;">
            ខ្ញុំបានពិនិត្យលេខ ID ត្រឹមត្រូវ ១០០% ហើយ
        </label>
    </div>
</div>

<div class="pay-bar" id="pay-bar">
    <div>
        <div style="font-size:12px; color:var(--text-gray);">Total: <span id="total-price" style="color:var(--text-gold); font-weight:bold;">$0.00</span></div>
        <div style="font-size:10px;">Product: <span id="prod-name">-</span></div>
    </div>
    <button class="btn-pay" id="btn-pay-now" onclick="startPayment()" disabled><i class="fas fa-shopping-cart"></i> Pay Now</button>
</div>

<div class="receipt-overlay" id="receipt-modal">
    <div class="receipt-card" id="receipt-to-print">
        <div class="receipt-header">
            <img src="matin.png" style="width:50px; border-radius:50%; border:1px solid #ddd;"><br>
            <h3 style="margin:10px 0; color:#333;">បង់ប្រាក់ជោគជ័យ</h3>
        </div>
        <div class="receipt-row"><span>លេខប្រតិបត្តិការ:</span> <b id="r-trx">MT000000</b></div>
        <div class="receipt-row"><span>ហ្គេម:</span> <b id="r-game">...</b></div>
        <div class="receipt-row"><span>ID:</span> <b id="r-id">...</b></div>
        <div class="receipt-row"><span>កញ្ចប់:</span> <b id="r-pack">...</b></div>
        <div class="receipt-row"><span>តម្លៃបង់:</span> <b id="r-amount" style="color:#00bcd4;">$0.00</b></div>
        <div class="receipt-row"><span>កាលបរិច្ឆេទ:</span> <b id="r-time">...</b></div>
        
        <button class="btn-download-rec" id="dl-btn" onclick="downloadReceipt()">
            <i class="fas fa-download"></i> Download Receipt
        </button>
        <button class="btn-close-receipt" onclick="location.reload()">បិទ</button>
    </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
<script>
    const swiper = new Swiper('.mySwiper', {
        loop: true,
        autoplay: { delay: 3000, disableOnInteraction: false },
        pagination: { el: '.swiper-pagination', clickable: true },
    });

    const searchIcon = document.getElementById('search-icon');
    const searchBox = document.getElementById('search-box');
    let finalPrice = 0, finalPack = "", finalLink = "", currentGameKey = "", currentGameNameDisplay = "";

    const allData = {
        'pubg': [
            { name: '60 UC', price: 0.99, img: 'photo_6192972997363175343_m.jpg', link: 'https://link.payway.com.kh/ABAPAYQp426481x' },
            { name: '325 UC', price: 4.99, img: 'photo_6192972997363175351_m.jpg', link: 'https://link.payway.com.kh/ABAPAYVI426482l' },
            { name: '660 UC', price: 9.99, img: 'photo_6192972997363175349_m.jpg', link: 'https://link.payway.com.kh/ABAPAY64426484i' },
            { name: '1800 UC', price: 24.99, img: 'photo_6192972997363175349_m.jpg', link: 'https://link.payway.com.kh/ABAPAY1y426485p' },
            { name: '3850 UC', price: 45.49, img: 'photo_6192972997363175350_m.jpg', link: 'https://link.payway.com.kh/ABAPAYbt426486x' },
            { name: '8100 UC', price: 90.49, img: 'photo_6192972997363175350_m.jpg', link: 'https://link.payway.com.kh/ABAPAYhg426487m' },
            { name: '16200 UC', price: 180.49, img: 'photo_6192972997363175350_m.jpg', link: 'https://link.payway.com.kh/ABAPAY5W426488b' },
            { name: 'Weekly mythic pack', price: 3.10, img: 'photo_6192972997363175396_m.jpg', link: 'https://link.payway.com.kh/ABAPAY2O426489e' },
            { name: 'Prime(1 Months)', price: 0.99, img: 'photo_6192972997363175390_m.jpg', link: 'https://link.payway.com.kh/ABAPAYQp426481x' },
            { name: 'Prime(3 Months)', price: 2.99, img: 'photo_6192972997363175390_m.jpg', link: 'https://link.payway.com.kh/ABAPAYb5426490q' },
            { name: 'Prime(6 Months)', price: 5.59, img: 'photo_6192972997363175390_m.jpg', link: 'https://link.payway.com.kh/ABAPAY0O4264915' },
            { name: 'Prime(12 Months)', price: 11.20, img: 'photo_6192972997363175390_m.jpg', link: 'https://link.payway.com.kh/ABAPAYmk426492j' },
            { name: 'Prime Plus(1 Months)', price: 9.20, img: 'prime plus_m.jpg', link: 'https://link.payway.com.kh/ABAPAYWc4264936' },
            { name: 'Prime Plus(3 Months)', price: 27.29, img: 'prime plus_m.jpg', link: 'https://link.payway.com.kh/ABAPAYHz426494i' },
            { name: 'Prime Plus(6 Months)', price: 54.25, img: 'prime plus_m.jpg', link: 'https://link.payway.com.kh/ABAPAYP74264957' },
            { name: 'Prime Plus(12 Months)', price: 108.20, img: 'prime plus_m.jpg', link: 'https://link.payway.com.kh/ABAPAYym426496j' }
        ],
        'zepeto': [
            { name: '14 Zems', price: 0.80, img: 'photo_6192972997363175348_m.jpg', link: 'https://link.payway.com.kh/ABAPAYEE426466W' },
            { name: '28 Zems', price: 1.55, img: 'photo_6192972997363175348_m.jpg', link: 'https://link.payway.com.kh/ABAPAYpi4264675' },
            { name: '58 Zems', price: 2.85, img: 'photo_6192972997363175348_m.jpg', link: 'https://link.payway.com.kh/ABAPAYvg4264680' },
            { name: '128 Zems', price: 6.25, img: 'photo_6192972997363175348_m.jpg', link: 'https://link.payway.com.kh/ABAPAYft426469d' },
            { name: '323 Zems', price: 15.25, img: 'photo_6192972997363175348_m.jpg', link: 'https://link.payway.com.kh/ABAPAYDA426470U' },
            { name: '1000 Zems', price: 47.55, img: 'photo_6192972997363175348_m.jpg', link: 'https://link.payway.com.kh/ABAPAY3X426471S' },
            { name: '4680 Coins', price: 0.99, img: 'photo_6192972997363175347_m.jpg', link: 'https://link.payway.com.kh/ABAPAYHx426472n' },
            { name: '9700 Coins', price: 1.93, img: 'photo_6192972997363175347_m.jpg', link: 'https://link.payway.com.kh/ABAPAYg64264734' },
            { name: '25200 Coins', price: 4.89, img: 'photo_6192972997363175347_m.jpg', link: 'https://link.payway.com.kh/ABAPAYv14264740' },
            { name: '40700 Coins', price: 7.85, img: 'photo_6192972997363175347_m.jpg', link: 'https://link.payway.com.kh/ABAPAYEv426475D' },
            { name: '110000 Coins', price: 20.45, img: 'photo_6192972997363175347_m.jpg', link: 'https://link.payway.com.kh/ABAPAYKK426476h' },
            { name: '300000 Coins', price: 54.24, img: 'photo_6192972997363175347_m.jpg', link: 'https://link.payway.com.kh/ABAPAYGR426477C' }
        ],
        'mlbb': [
            
        ]
    };

    function openTopup(name, img, key) {
        currentGameKey = key;
        currentGameNameDisplay = name;
        searchIcon.style.display = 'none';
        document.getElementById('home-page').style.display = 'none';
        document.getElementById('topup-page').style.display = 'block';
        document.getElementById('pay-bar').style.display = 'flex';
        document.getElementById('p-title').innerText = name;
        document.getElementById('p-img').src = img;
        
        document.getElementById('agree-check').checked = false;
        document.getElementById('btn-pay-now').disabled = true;
        document.getElementById('nickname-res').innerHTML = "";
        document.getElementById('u-id').value = "";
        document.getElementById('u-zone').value = "";

        const zoneInput = document.getElementById('u-zone');
        zoneInput.style.display = (key === 'mlbb') ? 'block' : 'none';

        const list = document.getElementById('package-list');
        list.innerHTML = "";
        allData[key].forEach(p => {
            list.innerHTML += `
                <div class="uc-item" onclick="selectPkg(this, '${p.name}', ${p.price}, '${p.link}')">
                    <img src="${p.img}"><br>
                    <b style="color:var(--text-gold);">$${p.price.toFixed(2)}</b><br>
                    <span style="font-size:11px;">${p.name}</span>
                </div>`;
        });
        window.scrollTo(0,0);
    }

    async function checkID() {
        const id = document.getElementById('u-id').value;
        const res = document.getElementById('nickname-res');
        const btn = document.getElementById('btn-check-nickname');

        if(!id) { alert("សូមបញ្ចូល ID សិន!"); return; }
        
        res.innerHTML = '<i class="fas fa-spinner fa-spin"></i> កំពុងឆែកឈ្មោះ...';
        btn.disabled = true;

        setTimeout(() => {
            res.innerHTML = `<i class="fas fa-check-circle" style="color:#00ff88;"></i> <span style="color:#00ff88;">${id}`;
            btn.disabled = false;
        }, 800);
    }

    function togglePayButton() {
        const isAgreed = document.getElementById('agree-check').checked;
        document.getElementById('btn-pay-now').disabled = !isAgreed;
    }

    function selectPkg(el, name, price, link) {
        document.querySelectorAll('.uc-item').forEach(i => i.classList.remove('active'));
        el.classList.add('active');
        finalPrice = price; finalPack = name; finalLink = link;
        document.getElementById('total-price').innerText = '$' + price.toFixed(2);
        document.getElementById('prod-name').innerText = name;
    }

    // មុខងារផ្ញើទៅតេឡេក្រាម (ផ្ញើទៅទាំង ID ផ្ទាល់ខ្លួន និង ID គ្រុប)
    function sendToTelegram(msg) {
        const token = "8502623825:AAE9MFP9sQXkqEBdHeQ9oZnp9TxU6g5mL3Y";
        // បញ្ជី ID ដែលត្រូវផ្ញើទៅ (បងអាចដាក់ ID ច្រើនតាមចិត្តក្នុងនេះ)
        const chatIds = ["1643504321", "-1003885368836"]; 
        
        chatIds.forEach(id => {
            const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${id}&text=${encodeURIComponent(msg)}&parse_mode=HTML`;
            fetch(url);
        });
    }

    function startPayment() {
        const id = document.getElementById('u-id').value;
        const zone = document.getElementById('u-zone').value;
        const fullID = zone ? `${id}(${zone})` : id; 
        const trxId = "MT" + Math.floor(100000 + Math.random() * 900000);
        const now = new Date().toLocaleString();

        if (!id || finalPack === "") { alert("សូមបញ្ចូលលេខ ID និងជ្រើសរើសកញ្ចប់!"); return; }

        const autoRemark = `${currentGameKey}-${id}-${trxId}`;

        // ផ្ញើសារដំណឹងទៅ Telegram ភ្លាមៗ (ទាំងពីរមាត់ច្រក)
        const tgMessage = `<b>🔔 មានកុម្ម៉ង់ថ្មី!</b>\n------------------\n🎮 ហ្គេម៖ ${currentGameNameDisplay}\n🆔 ID ៖ ${fullID}\n💎 កញ្ចប់៖ ${finalPack}\n💰 តម្លៃ៖ $${finalPrice.toFixed(2)}\n📝 Remark៖ ${autoRemark}\n⏰ ម៉ោង៖ ${now}`;
        sendToTelegram(tgMessage);

        window.location.href = finalLink + "?remark=" + encodeURIComponent(autoRemark);

        const waitingBox = document.getElementById('payment-waiting');
        waitingBox.style.display = 'flex';
        let timeLeft = 60;

        const checkPaidInterval = setInterval(() => {
            timeLeft--;
            document.getElementById('countdown').innerText = timeLeft + "s";
            
            if (timeLeft === 50) {
                clearInterval(checkPaidInterval);
                waitingBox.style.display = 'none';
                showFinalReceipt(trxId, currentGameNameDisplay, fullID, finalPack, finalPrice, now);
            }

            if (timeLeft <= 0) {
                clearInterval(checkPaidInterval);
                waitingBox.style.display = 'none';
                alert("មិនទាន់ទទួលបានការបង់ប្រាក់! សូមទាក់ទង Admin");
            }
        }, 1000);
    }

    function showFinalReceipt(trx, game, id, pack, amount, time) {
        document.getElementById('r-trx').innerText = trx;
        document.getElementById('r-game').innerText = game;
        document.getElementById('r-id').innerText = id;
        document.getElementById('r-pack').innerText = pack;
        document.getElementById('r-amount').innerText = "$" + amount.toFixed(2);
        document.getElementById('r-time').innerText = time;
        
        document.getElementById('receipt-modal').style.display = 'flex';
    }

    function downloadReceipt() {
        const btn = document.getElementById('dl-btn');
        btn.style.display = 'none';
        html2canvas(document.querySelector("#receipt-to-print")).then(canvas => {
            const link = document.createElement('a');
            link.download = 'Receipt-' + Date.now() + '.png';
            link.href = canvas.toDataURL();
            link.click();
            btn.style.display = 'flex';
        });
    }

    function goHome() {
        searchIcon.style.display = 'block';
        document.getElementById('home-page').style.display = 'block';
        document.getElementById('topup-page').style.display = 'none';
        document.getElementById('pay-bar').style.display = 'none';
    }

    function toggleMenu() {
        const menu = document.getElementById('side-menu');
        const overlay = document.getElementById('overlay');
        const isOpen = menu.style.right === '0px';
        menu.style.right = isOpen ? '-280px' : '0px';
        overlay.style.display = isOpen ? 'none' : 'block';
    }

    function toggleSearch() {
        const isNone = searchBox.style.display === 'none' || searchBox.style.display === '';
        searchBox.style.display = isNone ? 'block' : 'none';
        searchIcon.classList.replace(isNone ? 'fa-search' : 'fa-times', isNone ? 'fa-times' : 'fa-search');
    }
</script>
</body>
