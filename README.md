<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>SAKTOPUP - 100% Original Full Version</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
    <style>
        :root { 
            --bg-dark: #070a13; 
            --bg-card: #0c111c; 
            --primary-blue: #3dd0f3; 
            --text-gold: #fcc201; 
            --text-gray: #777d8a;
            --white: #ffffff;
            --aba-blue: #00bcd4;
        }

        * { box-sizing: border-box; font-family: 'Khmer OS Battambang', sans-serif; -webkit-tap-highlight-color: transparent; }
        body { background: var(--bg-dark); color: var(--white); margin: 0; padding: 0; overflow-x: hidden; }

        .header-sticky {
            position: sticky;
            top: 0;
            z-index: 1000;
            background: var(--bg-dark);
        }

        .navbar { background: #070a13; padding: 12px 15px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #1a202c; }
        .logo-text { color: var(--text-gold); font-weight: bold; font-size: 24px; font-style: italic; text-transform: uppercase; cursor: pointer; }

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

        /* --- Banner Slider ឱ្យនៅជាប់រហូត --- */
        .banner-container { width: 94%; height: 160px; margin: 15px auto; border-radius: 12px; overflow: hidden; }
        .swiper { width: 100%; height: 100%; }
        .swiper-slide img { width: 100%; height: 100%; object-fit: cover; }
        .swiper-pagination-bullet { background: #fff; }

        .container { padding: 15px; max-width: 600px; margin: auto; }
        .section-header { font-size: 14px; font-weight: bold; margin: 20px 0 12px 0; display: flex; align-items: center; gap: 8px; }

        .game-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
        .game-item { background: var(--bg-card); border-radius: 12px; border: 1px solid #1a202c; text-align: center; overflow: hidden; padding-bottom: 10px; cursor: pointer; }
        .game-item img { width: 100%; aspect-ratio: 1/1; object-fit: cover; }
        .btn-topup-sm { background: var(--primary-blue); color: #000; border: none; width: 85%; padding: 5px 0; border-radius: 5px; font-size: 10px; font-weight: bold; margin-top: 5px; }

        .stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 25px; }
        .stat-item { background: #0c111c; border: 1px solid #1a202c; padding: 15px; border-radius: 12px; text-align: center; }
        .stat-icon { color: var(--primary-blue); font-size: 18px; margin-bottom: 8px; }
        .stat-item b { font-size: 16px; display: block; margin-bottom: 4px; }
        .stat-item small { color: var(--text-gray); font-size: 10px; }

        .footer { background: #0c111c; padding: 30px 20px; text-align: left; border-top: 1px solid #1a202c; font-size: 12px; color: var(--text-gray); margin-top: 30px; }
        .footer-logo { color: var(--text-gold); font-size: 18px; font-weight: bold; margin-bottom: 10px; }
        .badge-khqr { background: #e53e3e; color: white; padding: 2px 5px; border-radius: 3px; font-size: 10px; font-weight: bold; }
        .badge-aba { background: var(--aba-blue); color: white; padding: 2px 5px; border-radius: 3px; font-size: 10px; font-weight: bold; }

        #topup-page { display: none; padding-bottom: 120px; }
        .card-box { background: var(--bg-card); border: 1px solid #1a202c; padding: 15px; border-radius: 12px; margin-bottom: 15px; }
        .id-input { width: 100%; background: #000; border: 1px solid #1a202c; padding: 12px; border-radius: 8px; color: #49bcf8; font-size: 16px; outline: none; margin-top: 10px; text-align: center; }

        .uc-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .uc-item { background: var(--bg-card); border: 1px solid #1a202c; padding: 15px; border-radius: 10px; cursor: pointer; transition: 0.3s; text-align: center; }
        .uc-item.active { border-color: var(--primary-blue); background: rgba(61, 208, 243, 0.05); }
        .uc-item img { width: 40px; height: 40px; object-fit: contain; margin-bottom: 8px; }

        .aba-payment-box { background: rgba(0, 188, 212, 0.05); border: 1.5px solid var(--aba-blue); padding: 15px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; }
        .aba-label { background: var(--aba-blue); color: white; padding: 2px 6px; border-radius: 4px; font-weight: bold; font-size: 10px; margin-right: 10px; }
        .aba-circle { width: 22px; height: 22px; border-radius: 50%; border: 2px solid var(--aba-blue); display: flex; align-items: center; justify-content: center; }

        .pay-bar { position: fixed; bottom: 0; left: 0; width: 100%; background: #0c111c; padding: 15px 20px; border-top: 1px solid #1a202c; display: none; justify-content: space-between; align-items: center; z-index: 2000; }
        .btn-pay { background: linear-gradient(90deg, #1e90ff, #00bfff); color: white; border: none; padding: 12px 25px; border-radius: 8px; font-weight: bold; display: flex; align-items: center; gap: 8px; cursor: pointer; }
    </style>
</head>
<body>

<div class="header-sticky">
    <nav class="navbar">
        <div class="logo-text" onclick="goHome()">MATINTOPUP</div>
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
    
    <a href="https://t.me/matintopup" target="_blank" class="contact-btn">
        <i class="fab fa-telegram" style="color:#24A1DE; font-size:24px;"></i>
        <div>
            <div style="font-size:14px; font-weight:bold;">តេឡេក្រាមផ្ទាល់ខ្លួន</div>
            <div style="font-size:11px; color:#777d8a;">ទាក់ទងមកយើងផ្ទាល់</div>
        </div>
    </a>

    <a href="https://t.me/Matintopup168" target="_blank" class="contact-btn">
        <i class="fas fa-users" style="color:#3dd0f3; font-size:20px;"></i>
        <div>
            <div style="font-size:14px; font-weight:bold;">តេឡេក្រាមគ្រុប</div>
            <div style="font-size:11px; color:#777d8a;">ចូលរួមសហគមន៍របស់យើង</div>
        </div>
    </a>
</div>
<div id="overlay" class="overlay" onclick="toggleMenu()"></div>

<div class="banner-container">
    <div class="swiper mySwiper">
        <div class="swiper-wrapper">
            <div class="swiper-slide"><img src="IMG_1257290665938849.jpeg"></div>
            <div class="swiper-slide"><img src="IMG_1507798854091986.jpeg"></div>
            <div class="swiper-slide"><img src="IMG_1662973291394423.jpeg"></div>
        </div>
        <div class="swiper-pagination"></div>
    </div>
</div>

<div id="home-page">
    <div class="container">
        <div class="section-header">⭐ BEST SELLING</div>
        <div class="game-grid">
            <div class="game-item" onclick="openTopup('PUBG MOBILE', 'PUBG.jpg')">
                <img src="PUBG.jpg">
                <div style="font-size:10px; padding:5px;">PUBG MOBILE</div>
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
            <input type="number" class="id-input" placeholder="បញ្ចូលលេខ ID នៅទីនេះ" id="u-id">
            <div id="check-container" style="display: none; color:#00ff00; font-size:12px; text-align:right; margin-top:8px; font-weight:bold;">
                ✅ <span id="id-label"></span>
            </div>
        </div>

        <div style="font-size:14px; font-weight:bold; margin-bottom:12px;">💎 SAVING PACKAGES</div>
        <div class="uc-grid">
            <div class="uc-item" onclick="selectUC(this, '60 UC', 0.99)">
                <img src="gggg.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$0.99</b><br>
                <span style="font-size:11px;">60 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, '325 UC', 4.49)">
                <img src="PUBG-Mobile-UC-Station.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$4.99</b><br>
                <span style="font-size:11px;">325 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, '660 UC', 9.99)">
                <img src="oss-a3a9e4a98044a39b4cbfe3626d7c375c-removebg-preview.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$9.99</b><br>
                <span style="font-size:11px;">660 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, '1800 UC', 24.99)">
                <img src="oss-a3a9e4a98044a39b4cbfe3626d7c375c-removebg-preview.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$24.99</b><br>
                <span style="font-size:11px;">1800 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, '3850 UC', 45.49)">
                <img src="oss-a3a9e4a98044a39b4cbfe3626d7c375c-removebg-preview.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$45.49</b><br>
                <span style="font-size:11px;">3850 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, '8100 UC', 90.49)">
                <img src="oss-70d65d0c5638c244117f34f2a8254cb6.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$90.49</b><br>
                <span style="font-size:11px;">8100 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, '16200 UC', 180.49)">
                <img src="oss-70d65d0c5638c244117f34f2a8254cb6.png" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$180.49</b><br>
                <span style="font-size:11px;">16200 UC</span>
            </div>
            <div class="uc-item" onclick="selectUC(this, 'Weekly Mythic Emblem Value Pack', 3.49)">
                <img src="images.jpeg" alt="UC">
                <br>
                <b style="color:var(--text-gold);">$3.49</b><br>
                <span style="font-size:11px;">Weekly Mythic Emblem Value Pack</span>
            </div>
        </div>

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
    </div>
</div>

<div class="pay-bar" id="pay-bar">
    <div>
        <div style="font-size:12px; color:var(--text-gray);">Total: <span id="total-price" style="color:var(--text-gold); font-weight:bold;">$0.00</span></div>
        <div style="font-size:10px;">Product: <span id="prod-name">-</span></div>
    </div>
    <button class="btn-pay" onclick="startPayment()"><i class="fas fa-shopping-cart"></i> Pay Now</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

<script>
    // Setup Swiper Slider
    const swiper = new Swiper('.mySwiper', {
        loop: true,
        autoplay: {
            delay: 3000,
            disableOnInteraction: false,
        },
        pagination: {
            el: '.swiper-pagination',
            clickable: true,
        },
    });

    const searchIcon = document.getElementById('search-icon');
    const searchBox = document.getElementById('search-box');

    // variable បន្ថែមសម្រាប់ផ្ទុកតម្លៃ
    let finalPrice = 0;
    let finalPack = "";

    function openTopup(name, img) {
        searchIcon.style.display = 'none';
        searchBox.style.display = 'none';
        document.getElementById('home-page').style.display = 'none';
        document.getElementById('topup-page').style.display = 'block';
        document.getElementById('pay-bar').style.display = 'flex';
        document.getElementById('p-title').innerText = name;
        document.getElementById('p-img').src = img;
        window.scrollTo(0,0);
    }

    function goHome() {
        searchIcon.style.display = 'block';
        document.getElementById('home-page').style.display = 'block';
        document.getElementById('topup-page').style.display = 'none';
        document.getElementById('pay-bar').style.display = 'none';
    }

    function selectUC(el, name, price) {
        document.querySelectorAll('.uc-item').forEach(i => i.classList.remove('active'));
        el.classList.add('active');
        finalPrice = price;
        finalPack = name;
        document.getElementById('total-price').innerText = '$' + price.toFixed(2);
        document.getElementById('prod-name').innerText = name;
    }

    // --- មុខងារបង់ប្រាក់ - រក្សាទម្រង់ដើមបង ១០០% តែបន្ថែមការផ្ញើទៅ Bot ---
    function startPayment() {
        const id = document.getElementById('u-id').value;
        if (!id || finalPack === "") { 
            alert("សូមបញ្ចូលលេខ ID និងជ្រើសរើសកញ្ចប់ UC ជាមុនសិន!"); 
            return; 
        }

        // --- កន្លែងប្តូរ Token និង Chat ID របស់បង ---
        const telegram_token = "8502623825:AAE9MFP9sQXkqEBdHeQ9oZnp9TxU6g5mL3Y"; 
        const chat_id = "1643504321";

        const message = `🔔 ការកុម្ម៉ង់ថ្មី!%0A🎮 ហ្គេម៖ ${document.getElementById('p-title').innerText}%0A🆔 ID ភ្ញៀវ៖ ${id}%0A💎 កញ្ចប់៖ ${finalPack}%0A💰 តម្លៃ៖ $${finalPrice.toFixed(2)}`;

        // ១. ផ្ញើទៅ Bot ជាមុន (ស្ងាត់ៗ)
        fetch(`https://api.telegram.org/bot${telegram_token}/sendMessage?chat_id=${chat_id}&text=${message}`)
        .then(() => {
            // ២. រួចហើយទើបលោតទៅ ABA តាមក្រោយភ្លាម
            window.location.href = "https://link.payway.com.kh/ABAPAYfN4261854"; 
        })
        .catch(() => {
            // បើមានបញ្ហាអ៊ីនធឺណិត ក៏ត្រូវឱ្យភ្ញៀវបន្តទៅ ABA ដែរ
            window.location.href = "https://link.payway.com.kh/ABAPAYfN4261854";
        });
    }

    function toggleMenu() {
        const menu = document.getElementById('side-menu');
        const overlay = document.getElementById('overlay');
        if (menu.style.right === '0px') {
            menu.style.right = '-280px';
            overlay.style.display = 'none';
        } else {
            menu.style.right = '0px';
            overlay.style.display = 'block';
        }
    }

    function toggleSearch() {
        if (searchBox.style.display === 'none' || searchBox.style.display === '') {
            searchBox.style.display = 'block';
            searchIcon.classList.replace('fa-search', 'fa-times');
        } else {
            searchBox.style.display = 'none';
            searchIcon.classList.replace('fa-times', 'fa-search');
        }
    }

    document.getElementById('u-id').addEventListener('input', function() {
        const checkContainer = document.getElementById('check-container');
        const idLabel = document.getElementById('id-label');
        if (this.value.length > 0) {
            checkContainer.style.display = 'block';
            idLabel.innerText = this.value;
        } else {
            checkContainer.style.display = 'none';
        }
    });
</script>
</body>
</html>
