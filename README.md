<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Matin Store - 1000 Products System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root { --main: #0088cc; --orange: #ff9900; --red: #d9534f; --telegram: #24A1DE; --green: #28a745; }
        * { box-sizing: border-box; }
        body { font-family: 'Khmer OS Battambang', sans-serif; background: #f4f7f6; margin: 0; padding-bottom: 90px; }
        
        .header { background: linear-gradient(135deg, var(--main), #005f91); color: white; text-align: center; padding: 12px; position: sticky; top: 0; z-index: 1000; }
        .container { padding: 10px; max-width: 100%; margin: auto; }
        
        /* ប្លង់បង្ហាញផលិតផល */
        .product-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; }
        .product-card { background: white; border-radius: 12px; padding: 10px; text-align: center; box-shadow: 0 2px 8px rgba(0,0,0,0.05); border: 1px solid #eee; display: flex; flex-direction: column; justify-content: space-between; }
        .product-img { width: 100%; aspect-ratio: 1/1; object-fit: cover; border-radius: 8px; margin-bottom: 8px; background: #f9f9f9; }
        .product-card h4 { margin: 5px 0; font-size: 12px; height: 35px; overflow: hidden; color: #333; line-height: 1.4; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; }
        .product-card .price { color: var(--red); font-weight: bold; font-size: 15px; margin-bottom: 8px; display: block; }
        .btn-add { background: var(--orange); color: white; border: none; padding: 8px; border-radius: 20px; width: 100%; font-weight: bold; font-size: 11px; cursor: pointer; }

        /* ប៊ូតុងប្តូរទំព័រ */
        .pagination { display: flex; justify-content: center; align-items: center; gap: 8px; margin: 25px 0; flex-wrap: wrap; padding: 0 10px; }
        .page-btn { padding: 8px 14px; border: 1px solid var(--main); background: white; color: var(--main); border-radius: 6px; cursor: pointer; font-weight: bold; font-size: 14px; transition: 0.3s; }
        .page-btn.active { background: var(--main); color: white; border-color: var(--main); }

        .floating-controls { position: fixed; bottom: 20px; right: 15px; display: flex; flex-direction: column; gap: 10px; z-index: 2000; }
        .float-btn { width: 55px; height: 55px; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; box-shadow: 0 5px 15px rgba(0,0,0,0.2); cursor: pointer; text-decoration: none; }
        .bg-telegram { background: var(--telegram); }
        .bg-cart { background: var(--main); position: relative; }
        .badge { position: absolute; top: 0; right: 0; background: var(--red); color: white; font-size: 10px; width: 20px; height: 20px; border-radius: 50%; display: flex; align-items: center; justify-content: center; border: 2px solid white; }

        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); z-index: 3000; align-items: flex-end; justify-content: center; }
        .modal-content { background: white; width: 100%; max-width: 500px; border-radius: 20px 20px 0 0; padding: 20px; box-sizing: border-box; max-height: 85vh; overflow-y: auto; }
        .cart-item { display: flex; justify-content: space-between; align-items: center; padding: 10px 0; border-bottom: 1px solid #eee; }
        .order-form input, .order-form textarea { width: 100%; padding: 12px; margin-bottom: 10px; border-radius: 8px; border: 1px solid #ddd; outline: none; font-family: inherit; }

        #qrModal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 4000; align-items: center; justify-content: center; padding: 15px; }
        .qr-box { background: white; padding: 20px; border-radius: 20px; width: 100%; max-width: 320px; text-align: center; }
        .qr-img { width: 100%; max-width: 230px; border-radius: 10px; border: 2px solid var(--main); margin: 10px 0; cursor: pointer; }
        .btn-aba-open { display: block; background: #005f91; color: white; text-decoration: none; padding: 15px; border-radius: 10px; font-weight: bold; margin-bottom: 15px; font-size: 15px; text-align: center; border: none; width: 100%; cursor: pointer; }
        .delivery-info { color: #555; font-size: 13px; margin: 10px 0; padding: 8px; border-top: 1px dashed #ccc; display: flex; justify-content: space-between; }
    </style>
</head>
<body>

<div class="header"><h3>🏪 Matin Store</h3></div>

<div class="container">
    <div class="product-grid" id="productGrid"></div>
    <div class="pagination" id="pagination"></div>
</div>

<div class="floating-controls">
    <a href="https://t.me/CHEASOKCHAMREUN1111" target="_blank" class="float-btn bg-telegram"><i class="fab fa-telegram-plane" style="font-size: 25px;"></i></a>
    <div class="float-btn bg-cart" onclick="openCart()">
        <i class="fas fa-shopping-cart" style="font-size: 20px;"></i>
        <div class="badge" id="cartBadge">0</div>
    </div>
</div>

<div class="modal" id="cartModal">
    <div class="modal-content">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:15px;">
            <h3 style="margin:0;">🛒 កន្ត្រកអីវ៉ាន់</h3>
            <span onclick="closeCart()" style="font-size:30px; cursor:pointer; color:#999;">&times;</span>
        </div>
        <div id="cartItems"></div>
        <div class="delivery-info">
            <span>🛵 ថ្លៃដឹកជញ្ជូន (Delivery):</span>
            <span style="font-weight: bold;">$2.00</span>
        </div>
        <div style="display:flex; justify-content:space-between; font-weight:bold; margin:10px 0; font-size:18px;">
            <span>សរុបទាំងអស់:</span> <span id="totalTxt" style="color:var(--red);">$0.00</span>
        </div>
        <div class="order-form">
            <input type="text" id="custName" placeholder="👤 ឈ្មោះរបស់អ្នក">
            <input type="number" id="custPhone" placeholder="📞 លេខទូរសព្ទ">
            <textarea id="custAddress" placeholder="📍 ទីតាំងដឹកជញ្ជូន"></textarea>
            <button onclick="submitOrder()" style="width:100%; padding:15px; background:var(--green); color:white; border:none; border-radius:10px; font-weight:bold; font-size:16px;">✅ បញ្ជាទិញឥឡូវនេះ</button>
        </div>
    </div>
</div>

<div id="qrModal">
    <div class="qr-box">
        <h3 style="margin:0; font-size: 16px;">សូមចុចប៊ូតុងខាងក្រោមដើម្បីបង់ប្រាក់</h3>
        <h2 style="color:var(--red); margin: 10px 0;">$ <span id="payAmount">0.00</span></h2>
        <img src="IMG_20260317_155742_134~2.jpg" class="qr-img" onclick="openABALink()">
        <button onclick="openABALink()" class="btn-aba-open"><i class="fas fa-university"></i> បើកកម្មវិធី ABA</button>
        <button onclick="sendPaymentNoti()" style="background:var(--green); color:white; border:none; padding:12px; width:100%; border-radius:10px; font-weight:bold; cursor:pointer;">ខ្ញុំបានបង់ប្រាក់រួចរាល់</button>
    </div>
</div>

<script>
    // ==========================================
    // ផ្នែក Copy & Paste ផលិតផលនៅត្រង់នេះ
    // ==========================================
    const allProducts = [
        // ទំព័រទី ១ (ផលិតផល ១-១០)
        { id: 1, name: "អាវយឺតបុរស ម៉ូតថ្មី ០១", price: "10.00", img: "IMG_20260317_032745_060.jpg" },
        { id: 2, name: "ផលិតផលលេខ ០២", price: "12.50", img: "https://via.placeholder.com/150" },
        { id: 3, name: "ផលិតផលលេខ ០៣", price: "15.00", img: "https://via.placeholder.com/150" },
        { id: 4, name: "ផលិតផលលេខ ០៤", price: "8.00", img: "https://via.placeholder.com/150" },
        { id: 5, name: "ផលិតផលលេខ ០៥", price: "20.00", img: "https://via.placeholder.com/150" },
        { id: 6, name: "ផលិតផលលេខ ០៦", price: "11.00", img: "https://via.placeholder.com/150" },
        { id: 7, name: "ផលិតផលលេខ ០៧", price: "9.50", img: "https://via.placeholder.com/150" },
        { id: 8, name: "ផលិតផលលេខ ០៨", price: "13.00", img: "https://via.placeholder.com/150" },
        { id: 9, name: "ផលិតផលលេខ ០៩", price: "18.00", img: "https://via.placeholder.com/150" },
        { id: 10, name: "ផលិតផលលេខ ១០", price: "5.00", img: "https://via.placeholder.com/150" },

        // ទំព័រទី ២ (ផលិតផល ១១-២០) - ចម្លងជួរខាងលើមកដាក់ចុះមកក្រោមបន្តទៀត
        { id: 11, name: "ផលិតផលលេខ ១១", price: "12.00", img: "https://via.placeholder.com/150" },
        { id: 12, name: "ផលិតផលលេខ ១២", price: "14.00", img: "https://via.placeholder.com/150" },
        { id: 13, name: "ផលិតផលលេខ ១៣", price: "16.00", img: "https://via.placeholder.com/150" },
        { id: 11, name: "ផលិតផលលេខ ១១", price: "12.00", img: "https://via.placeholder.com/150" },
        { id: 12, name: "ផលិតផលលេខ ១២", price: "14.00", img: "https://via.placeholder.com/150" },
        { id: 13, name: "ផលិតផលលេខ ១៣", price: "16.00", img: "https://via.placeholder.com/150" },
        // អ្នកអាចចម្លងដាក់ចុះក្រោមរហូតដល់ id: 1000...
    ];
    // ==========================================

    let cart = [];
    let curPage = 1;
    const limit = 10; // ១ ទំព័រ បង្ហាញ ១០ ផលិតផល
    const deliveryFee = 2.00; // ថ្លៃដឹក $2
    const bot_token = "8502623825:AAE9MFP9sQXkqEBdHeQ9oZnp9TxU6g5mL3Y";
    const chat_id = "1643504321";
    let currentTotal = 0;

    function renderProducts(page) {
        curPage = page;
        const grid = document.getElementById('productGrid');
        const start = (page - 1) * limit;
        const itemsToDisplay = allProducts.slice(start, start + limit);
        grid.innerHTML = itemsToDisplay.map(p => `
            <div class="product-card">
                <img src="${p.img}" class="product-img">
                <h4>${p.name}</h4>
                <span class="price">$${p.price}</span>
                <button class="btn-add" onclick="addToCart(${p.id})">+ ដាក់កន្ត្រក</button>
            </div>
        `).join('');
        renderPager();
        window.scrollTo({top: 0, behavior: 'smooth'});
    }

    function renderPager() {
        const pager = document.getElementById('pagination');
        const totalPages = Math.ceil(allProducts.length / limit);
        pager.innerHTML = "";
        if (totalPages <= 1) return;
        for (let i = 1; i <= totalPages; i++) {
            pager.innerHTML += `<button class="page-btn ${i === curPage ? 'active' : ''}" onclick="renderProducts(${i})">${i}</button>`;
        }
    }

    function addToCart(id) {
        const item = allProducts.find(x => x.id === id);
        cart.push({...item, cartUid: Date.now() + Math.random()});
        document.getElementById('cartBadge').innerText = cart.length;
    }

    function openCart() {
        if(cart.length === 0) return alert("កន្ត្រកទំនេរ!");
        updateCartUI();
        document.getElementById('cartModal').style.display = 'flex';
    }

    function closeCart() { document.getElementById('cartModal').style.display = 'none'; }

    function updateCartUI() {
        const list = document.getElementById('cartItems');
        let subTotal = 0;
        list.innerHTML = cart.map(p => {
            subTotal += parseFloat(p.price);
            return `<div class="cart-item">
                <div style="text-align:left;">
                    <div style="font-size:13px; font-weight:bold;">${p.name}</div>
                    <div style="color:var(--red); font-size:12px;">$${p.price}</div>
                </div>
                <i class="fas fa-trash-alt" style="color:red; cursor:pointer;" onclick="removeItem(${p.cartUid})"></i>
            </div>`;
        }).join('');
        let finalTotal = subTotal + deliveryFee;
        document.getElementById('totalTxt').innerText = `$${finalTotal.toFixed(2)}`;
        currentTotal = finalTotal.toFixed(2);
    }

    function removeItem(uid) {
        cart = cart.filter(p => p.cartUid !== uid);
        document.getElementById('cartBadge').innerText = cart.length;
        if (cart.length === 0) closeCart(); else updateCartUI();
    }

    function submitOrder() {
        const name = document.getElementById('custName').value;
        const phone = document.getElementById('custPhone').value;
        const addr = document.getElementById('custAddress').value;
        if (!name || !phone || !addr) return alert("សូមបំពេញព័ត៌មានឱ្យគ្រប់!");
        const productList = cart.map((p, i) => `${i+1}. ${p.name} ($${p.price})`).join('%0A');
        const msg = `📦 *កុម្ម៉ង់ថ្មី*%0A👤 ឈ្មោះ: ${name}%0A📞 លេខ: ${phone}%0A📍 ទីតាំង: ${addr}%0A🛒 *ទំនិញ៖*%0A${productList}%0A🛵 ដឹកជញ្ជូន: $${deliveryFee.toFixed(2)}%0A💰 *សរុប៖ $${currentTotal}*`;
        fetch(`https://api.telegram.org/bot${bot_token}/sendMessage?chat_id=${chat_id}&text=${msg}&parse_mode=Markdown`);
        document.getElementById('payAmount').innerText = currentTotal;
        closeCart();
        document.getElementById('qrModal').style.display = 'flex';
    }

    function openABALink() {
        window.location.href = `https://pay.ababank.com/oRF8/du83nu9t`;
    }

    function sendPaymentNoti() {
        const payMsg = `💰 សរុប: $${currentTotal}%0A🏧 ស្ថានភាព: ភ្ញៀវចុចបង់រួចរាល់`;
        fetch(`https://api.telegram.org/bot${bot_token}/sendMessage?chat_id=${chat_id}&text=${payMsg}&parse_mode=Markdown`)
        .then(() => { alert("អរគុណ! យើងនឹងពិនិត្យមើលការបង់ប្រាក់របស់អ្នក។"); location.reload(); });
    }

    renderProducts(1);
</script>
</body>
</html>
