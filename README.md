<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>ហាងអនឡាញ - ១០ មុខក្នុងមួយទំព័រ</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        body { font-family: 'Khmer OS Battambang', sans-serif; background: #f4f7f6; margin: 0; padding-bottom: 90px; }
        .header { background: linear-gradient(135deg, #0088cc, #005f91); color: white; text-align: center; padding: 15px; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
        
        .container { padding: 12px; max-width: 600px; margin: auto; }
        /* កែសម្រួល Grid ឱ្យស្អាតសម្រាប់ ១០ មុខ */
        .product-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; }
        
        .product-card { background: white; border-radius: 15px; padding: 12px; text-align: center; box-shadow: 0 4px 6px rgba(0,0,0,0.05); border: 1px solid #eee; transition: 0.3s; }
        .product-img-placeholder { width: 100%; aspect-ratio: 1/1; background: #f8f9fa; border-radius: 10px; display: flex; align-items: center; justify-content: center; color: #ccc; font-size: 11px; margin-bottom: 8px; border: 1px dashed #ddd; }
        
        .product-card h4 { margin: 8px 0; font-size: 13px; height: 38px; overflow: hidden; color: #333; line-height: 1.5; }
        .product-card .price { color: #d9534f; font-weight: bold; font-size: 16px; display: block; margin-bottom: 10px; }
        .btn-add { background: #ff9900; color: white; border: none; padding: 10px; border-radius: 25px; width: 100%; font-weight: bold; font-size: 12px; cursor: pointer; transition: 0.2s; }
        .btn-add:active { transform: scale(0.95); background: #e68a00; }

        /* Pagination Style */
        .pagination { display: flex; justify-content: center; align-items: center; gap: 8px; margin: 30px 0; flex-wrap: wrap; }
        .page-btn { padding: 8px 14px; border: 1px solid #0088cc; background: white; color: #0088cc; border-radius: 8px; cursor: pointer; font-weight: bold; }
        .page-btn.active { background: #0088cc; color: white; box-shadow: 0 4px 8px rgba(0, 136, 204, 0.3); }

        /* Floating Controls */
        .floating-btns { position: fixed; bottom: 20px; right: 20px; display: flex; flex-direction: column; gap: 12px; z-index: 2000; }
        .btn-float { width: 58px; height: 58px; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; box-shadow: 0 5px 15px rgba(0,0,0,0.2); cursor: pointer; text-decoration: none; }
        .bg-blue { background: #0088cc; position: relative; }
        .bg-sky { background: #24A1DE; }
        .badge { position: absolute; top: -2px; right: -2px; background: #ff4d4d; color: white; font-size: 11px; width: 22px; height: 22px; border-radius: 50%; display: flex; align-items: center; justify-content: center; border: 2px solid white; font-weight: bold; }

        /* Modal Panels */
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); z-index: 3000; align-items: flex-end; justify-content: center; }
        .modal-content { background: white; width: 100%; max-width: 500px; border-radius: 25px 25px 0 0; padding: 20px; box-sizing: border-box; max-height: 85vh; overflow-y: auto; }
        .cart-item { display: flex; justify-content: space-between; padding: 12px 0; border-bottom: 1px solid #eee; align-items: center; }
        
        input, textarea { width: 100%; padding: 13px; border: 1px solid #ddd; border-radius: 12px; margin-bottom: 12px; box-sizing: border-box; font-size: 14px; background: #fcfcfc; }
        .btn-confirm { background: #28a745; color: white; border: none; padding: 16px; border-radius: 15px; font-size: 17px; font-weight: bold; width: 100%; cursor: pointer; }

        /* Payment QR Modal */
        #qrModal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 4000; align-items: center; justify-content: center; }
        .qr-box { background: white; padding: 25px; border-radius: 25px; text-align: center; width: 85%; max-width: 330px; }
        .qr-image { width: 100%; border-radius: 15px; margin: 15px 0; border: 4px solid #0088cc; cursor: pointer; }
    </style>
</head>
<body>

<div class="header"><h3>🏪 ហាងអនឡាញទំនើប</h3></div>

<div class="container">
    <div class="product-grid" id="productGrid"></div>
    <div class="pagination" id="pagination"></div>
</div>

<div class="floating-btns">
    <a href="https://t.me/Luck_17" class="btn-float bg-sky" target="_blank"><i class="fab fa-telegram-plane" style="font-size: 26px;"></i></a>
    <div class="btn-float bg-blue" onclick="openCart()">
        <i class="fas fa-shopping-cart" style="font-size: 22px;"></i>
        <div class="badge" id="cartBadge">0</div>
    </div>
</div>

<div class="modal" id="cartModal">
    <div class="modal-content">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:15px;">
            <h3 style="margin:0;">🛒 ទំនិញដែលបានរើស</h3>
            <span onclick="closeCart()" style="font-size:35px; cursor:pointer; color:#999;">&times;</span>
        </div>
        <div id="cartItems"></div>
        <div style="display:flex; justify-content:space-between; font-weight:bold; margin:20px 0; font-size:20px;">
            <span>សរុបរួម:</span> <span id="totalTxt" style="color:#d9534f;">$0.00</span>
        </div>
        <input type="text" id="name" placeholder="👤 ឈ្មោះរបស់អ្នក">
        <input type="number" id="phone" placeholder="📞 លេខទូរសព្ទ">
        <textarea id="addr" rows="2" placeholder="📍 អាសយដ្ឋានដឹកជញ្ជូន"></textarea>
        <button class="btn-confirm" onclick="submitOrder()">✅ បញ្ជាទិញ និងទៅកាន់កន្លែងបង់ប្រាក់</button>
    </div>
</div>

<div id="qrModal">
    <div class="qr-box">
        <h3 style="margin:0; color:#0088cc;">ABA បង់ប្រាក់រហ័ស</h3>
        <p style="font-size:26px; font-weight:bold; color:#d9534f; margin:10px 0;">$ <span id="payAmount">0.00</span></p>
        <p style="font-size:12px; color:#555;">👇 ចុចលើរូប QR ដើម្បីបើក App ABA ក្នុងទូរសព្ទ</p>
        
        <a id="bankLink" href="#" target="_blank">
            <img src="aba_mobile.jpg" class="qr-image" alt="QR Code">
        </a>
        
        <p style="font-size:11px; color:#888;">*សូមថតរូបវិក្កយបត្រទុកផ្ញើជូនម្ចាស់ហាង*</p>
        <button onclick="finishAll()" style="background:#28a745; color:white; border:none; padding:13px; width:100%; border-radius:12px; font-weight:bold; margin-top:10px; cursor:pointer;">រួចរាល់</button>
    </div>
</div>

<script>
    // បង្កើតទិន្នន័យផលិតផល ៦០០ មុខ
    const products = Array.from({ length: 600 }, (_, i) => ({
        id: i + 1,
        name: `ផលិតផល ម៉ូដថ្មី លេខ ${i + 1}`,
        price: (Math.random() * 25 + 5).toFixed(2)
    }));

    let cart = [];
    let curPage = 1;
    const itemsPerPage = 10; // កំណត់ ១០ មុខក្នុងមួយទំព័រ

    function renderProducts(page) {
        curPage = page;
        const grid = document.getElementById('productGrid');
        const start = (page - 1) * itemsPerPage;
        const items = products.slice(start, start + itemsPerPage);
        
        grid.innerHTML = items.map(p => `
            <div class="product-card">
                <div class="product-img-placeholder">រូបភាពទំនិញ</div>
                <h4>${p.name}</h4>
                <span class="price">$${p.price}</span>
                <button class="btn-add" onclick="add(${p.id})"><i class="fas fa-cart-plus"></i> បន្ថែម</button>
            </div>
        `).join('');
        renderPager();
        window.scrollTo({top: 0, behavior: 'smooth'});
    }

    function renderPager() {
        const pager = document.getElementById('pagination');
        pager.innerHTML = "";
        const totalPages = 60; // ៦០០ មុខ / ១០ ក្នុងមួយទំព័រ = ៦០ ទំព័រ
        
        let start = Math.max(1, curPage - 2);
        let end = Math.min(totalPages, curPage + 2);

        if (curPage > 1) pager.innerHTML += `<button class="page-btn" onclick="renderProducts(1)">ដំបូង</button>`;
        
        for(let i = start; i <= end; i++) {
            pager.innerHTML += `<button class="page-btn ${i === curPage ? 'active' : ''}" onclick="renderProducts(${i})">${i}</button>`;
        }
        
        if (curPage < totalPages) pager.innerHTML += `<button class="page-btn" onclick="renderProducts(${totalPages})">ចុងក្រោយ</button>`;
    }

    function add(id) {
        const p = products.find(x => x.id === id);
        cart.push({...p, uid: Date.now() + Math.random()});
        document.getElementById('cartBadge').innerText = cart.length;
    }

    function remove(uid) {
        cart = cart.filter(x => x.uid !== uid);
        document.getElementById('cartBadge').innerText = cart.length;
        updateCart();
        if(cart.length === 0) closeCart();
    }

    function openCart() {
        if(cart.length === 0) return alert("សូមជ្រើសរើសទំនិញជាមុនសិន!");
        updateCart();
        document.getElementById('cartModal').style.display = 'flex';
    }

    function closeCart() { document.getElementById('cartModal').style.display = 'none'; }

    function updateCart() {
        const list = document.getElementById('cartItems');
        let total = 0;
        list.innerHTML = cart.map(p => {
            total += parseFloat(p.price);
            return `<div class="cart-item">
                <div style="text-align:left;"><b>${p.name}</b><br><small style="color:#888;">$${p.price}</small></div>
                <i class="fas fa-trash-alt" onclick="remove(${p.uid})" style="color:#d9534f; cursor:pointer;"></i>
            </div>`;
        }).join('');
        document.getElementById('totalTxt').innerText = `$${total.toFixed(2)}`;
    }

    function submitOrder() {
        const name = document.getElementById('name').value;
        const phone = document.getElementById('phone').value;
        const addr = document.getElementById('addr').value;
        if(!name || !phone) return alert("សូមបំពេញឈ្មោះ និងលេខទូរសព្ទឱ្យបានត្រឹមត្រូវ!");

        const total = cart.reduce((s, x) => s + parseFloat(x.price), 0).toFixed(2);
        
        // ១. ផ្ញើទៅ Telegram Bot
        const token = "8502623825:AAE9MFP9sQXkqEBdHeQ9oZnp9TxU6g5mL3Y";
        const chat_id = "1643504321";
        const items = cart.map((p, i) => `${i+1}. ${p.name} ($${p.price})`).join('%0A');
        const msg = `✅ *ការកុម្ម៉ង់ថ្មី*%0A👤 ឈ្មោះ: ${name}%0A📞 លេខ: ${phone}%0A📍 ទីតាំង: ${addr}%0A📦 បញ្ជីអីវ៉ាន់:%0A${items}%0A💰 សរុប: $${total}%0A🏧 ស្ថានភាព: កំពុងរង់ចាំស្កេនបង់ប្រាក់...`;
        fetch(`https://api.telegram.org/bot${token}/sendMessage?chat_id=${chat_id}&text=${msg}&parse_mode=Markdown`);

        // ២. បង្ហាញផ្ទាំង QR
        document.getElementById('payAmount').innerText = total;
        document.getElementById('bankLink').href = `https://link.payway.com.kh/aba?id=oRF8/quqnct3c&amount=${total}`;
        document.getElementById('qrModal').style.display = 'flex';
    }

    function finishAll() {
        document.getElementById('qrModal').style.display = 'none';
        document.getElementById('cartModal').style.display = 'none';
        cart = []; document.getElementById('cartBadge').innerText = "0";
        alert("🎉 ការកុម្ម៉ង់របស់អ្នកទទួលបានជោគជ័យ! យើងនឹងទាក់ទងទៅវិញឆាប់ៗ។");
    }

    renderProducts(1);
</script>
