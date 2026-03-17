<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ហាងអনឡាញទំនើប</title>
    <style>
        body { font-family: 'Khmer OS Battambang', sans-serif; background: #f4f4f4; margin: 0; padding-bottom: 280px; }
        .header { background: #0088cc; color: white; text-align: center; padding: 15px; position: sticky; top: 0; z-index: 100; }
        .container { max-width: 600px; margin: auto; padding: 10px; }
        .product-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; }
        .product-card { background: white; border-radius: 8px; padding: 10px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.1); border: 1px solid #ddd; }
        .product-card img { width: 100%; height: 140px; object-fit: cover; border-radius: 5px; }
        .product-card h4 { margin: 8px 0 5px; font-size: 13px; height: 35px; overflow: hidden; color: #333; }
        .product-card .price { color: #d9534f; font-weight: bold; margin-bottom: 8px; display: block; }
        .btn-group { display: flex; gap: 4px; }
        .btn-add { background: #ff9900; color: white; border: none; padding: 8px; border-radius: 4px; flex: 1; cursor: pointer; font-size: 11px; font-weight: bold; }
        .btn-buy { background: #0088cc; color: white; border: none; padding: 8px; border-radius: 4px; flex: 1; cursor: pointer; font-size: 11px; font-weight: bold; }
        .pagination { display: flex; justify-content: center; overflow-x: auto; gap: 8px; padding: 20px 0; }
        .pagination button { padding: 8px 14px; border: 1px solid #0088cc; background: white; color: #0088cc; cursor: pointer; border-radius: 5px; min-width: 40px; }
        .pagination button.active { background: #0088cc; color: white; }
        .order-panel { position: fixed; bottom: 0; left: 0; right: 0; background: white; padding: 15px; box-shadow: 0 -5px 15px rgba(0,0,0,0.2); z-index: 1000; max-width: 600px; margin: auto; border-radius: 15px 15px 0 0; }
        .summary { display: flex; justify-content: space-between; margin-bottom: 10px; font-weight: bold; color: #333; }
        .total-price { color: #d9534f; font-size: 18px; }
        .input-box { display: flex; flex-direction: column; gap: 8px; }
        input, textarea { width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; box-sizing: border-box; font-family: inherit; }
        .btn-submit { background: #28a745; color: white; border: none; padding: 12px; border-radius: 6px; font-size: 16px; font-weight: bold; cursor: pointer; }
        #paymentModal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 2000; justify-content: center; align-items: center; }
        .modal-content { background: white; padding: 20px; border-radius: 15px; text-align: center; max-width: 300px; width: 90%; }
        .qr-img { width: 100%; border-radius: 10px; margin-bottom: 15px; cursor: pointer; border: 2px solid #0088cc; }
        .btn-confirm { background: #28a745; color: white; border: none; padding: 12px; width: 100%; border-radius: 8px; font-weight: bold; cursor: pointer; }
    </style>
</head>
<body>

<div class="header"><h2>🏪 ហាងអនឡាញទំនើប</h2></div>

<div class="container">
    <div class="product-grid" id="productDisplay"></div>
    <div class="pagination" id="pagination"></div>
</div>

<div class="order-panel">
    <div class="summary">
        <span id="cartCount">🛒 អីវ៉ាន់: 0 មុខ</span>
        <span class="total-price" id="totalDisplay">សរុប: $0.00</span>
    </div>
    <div class="input-box">
        <input type="text" id="custName" placeholder="👤 ឈ្មោះរបស់អ្នក">
        <input type="text" id="phone" placeholder="📞 លេខទូរសព្ទ">
        <textarea id="address" rows="2" placeholder="📍 អាសយដ្ឋានដឹកជញ្ជូន..."></textarea>
        <button class="btn-submit" onclick="showPayment()">📤 បញ្ជាទិញឥឡូវនេះ</button>
    </div>
</div>

<div id="paymentModal">
    <div class="modal-content">
        <h3 style="color:#0088cc;">បង់ប្រាក់តាម ABA</h3>
        <p style="font-size: 11px; color: red;">ចុចលើរូប QR ដើម្បីបើក App ABA</p>
        <a id="aba link" href="https://pay.ababank.com/oRF8/quqnct3c" target="_blank">
            <img src="aba_mobile.jpg" class="qr-img" alt="Scan to Pay">
        </a>
        <button class="btn-confirm" onclick="confirmPayment()">✅ ខ្ញុំបានបង់ប្រាក់រួចរាល់</button>
        <button onclick="document.getElementById('paymentModal').style.display='none'" style="margin-top:10px; border:none; background:none; color:red; cursor:pointer;">បោះបង់</button>
    </div>
</div>

<script>
    // --- ១. កន្លែងបញ្ចូលអីវ៉ាន់ម្ដងមួយៗ ដូចកូដចាស់របស់អ្នក ---
    const allProducts = [
        { id: 1, name: "អាវយឺតដៃខ្លី ម៉ូតថ្មី", price: "5.50", img: "aba_mobile.jpg" },
        { id: 2, name: "ខោខូវប៊យ បុរស", price: "12.00", img: "IMG_20260317_032745_060.jpg" },
        { id: 3, name: "កាបូបស្ពាយ ពណ៌ខ្មៅ", price: "18.00", img: "aba_mobile.jpg" },
        { id: 4, name: "ស្បែកជើងប៉ាត់តា", price: "25.00", img: "IMG_20260317_032745_060.jpg" },
        { id: 5, name: "មួកប៉ារ៉េ Fashion", price: "4.50", img: "https://via.placeholder.com/200x150?text=Item+5" },
        { id: 6, name: "វ៉ែនតាការពារថ្ងៃ", price: "7.00", img: "https://via.placeholder.com/200x150?text=Item+6" },
        { id: 7, name: "នាឡិកាដៃ បុរស", price: "35.00", img: "https://via.placeholder.com/200x150?text=Item+7" },
        { id: 8, name: "ខ្សែក្រវាត់ ស្បែក", price: "9.00", img: "https://via.placeholder.com/200x150?text=Item+8" },
        { id: 9, name: "អាវធំ សម្រាប់បុរស", price: "45.00", img: "https://via.placeholder.com/200x150?text=Item+9" },
        { id: 10, name: "កាបូបលុយ ស្បែក", price: "10.00", img: "https://via.placeholder.com/200x150?text=Item+10" }
        // អ្នកអាចថែម id: 11, 12... បន្តបន្ទាប់រហូតដល់ ១០០ ទំព័រ
    ];

    let cart = [];
    const itemsPerPage = 10;
    let currentPage = 1;

    function renderProducts(page) {
        const start = (page - 1) * itemsPerPage;
        const currentItems = allProducts.slice(start, start + itemsPerPage);
        const grid = document.getElementById('productDisplay');
        grid.innerHTML = "";
        currentItems.forEach(item => {
            grid.innerHTML += `
                <div class="product-card">
                    <img src="${item.img}">
                    <h4>${item.name}</h4>
                    <span class="price">$${item.price}</span>
                    <div class="btn-group">
                        <button class="btn-add" onclick="addToCart('${item.name}', ${item.price})">Add</button>
                        <button class="btn-buy" onclick="buyNow('${item.name}', ${item.price})">Buy</button>
                    </div>
                </div>`;
        });
        renderPagination();
    }

    function renderPagination() {
        const totalPages = Math.ceil(allProducts.length / itemsPerPage) || 100; 
        const nav = document.getElementById('pagination');
        nav.innerHTML = "";
        let start = Math.max(1, currentPage - 1);
        let end = Math.min(totalPages, currentPage + 1);
        for (let i = start; i <= end; i++) {
            const btn = document.createElement('button');
            btn.innerText = i;
            if (i === currentPage) btn.className = "active";
            btn.onclick = () => { currentPage = i; renderProducts(i); window.scrollTo(0,0); };
            nav.appendChild(btn);
        }
    }

    function addToCart(name, price) { cart.push({ name, price }); updateSummary(); }
    function buyNow(name, price) { cart = [{ name, price }]; updateSummary(); document.getElementById('custName').focus(); }
    function updateSummary() {
        let total = cart.reduce((sum, item) => sum + parseFloat(item.price), 0);
        document.getElementById('cartCount').innerText = `🛒 អីវ៉ាន់: ${cart.length} មុខ`;
        document.getElementById('totalDisplay').innerText = `សរុប: $${total.toFixed(2)}`;
    }

    function showPayment() {
        if (cart.length === 0 || !document.getElementById('custName').value || !document.getElementById('phone').value || !document.getElementById('address').value) {
            alert("សូមបំពេញព័ត៌មាន និងរើសអីវ៉ាន់ឱ្យគ្រប់!"); return;
        }
        document.getElementById('paymentModal').style.display = 'flex';
    }

    function confirmPayment() {
        document.getElementById('paymentModal').style.display = 'none';
        sendToTelegram();
    }

    function sendToTelegram() {
        const token = "8502623825:AAE9MFP9sQXkqEBdHeQ9oZnp9TxU6g5mL3Y"; 
        const chat_id = "1643504321";
        const name = document.getElementById('custName').value;
        const phone = document.getElementById('phone').value;
        const address = document.getElementById('address').value;
        let itemsText = cart.map(i => `- ${i.name} ($${i.price})`).join('%0A');
        let totalVal = cart.reduce((sum, i) => sum + parseFloat(i.price), 0).toFixed(2);
        const message = `✅ *កុម្ម៉ង់ថ្មី (បានបង់ប្រាក់)*%0A%0A👤 *ឈ្មោះ:* ${name}%0A📞 *លេខទូរសព្ទ:* ${phone}%0A📍 *អាសយដ្ឋាន:* ${address}%0A📦 *អីវ៉ាន់:*%0A${itemsText}%0A💰 *សរុប:* $${totalVal}%0A✅ *ស្ថានភាព:* ភ្ញៀវបញ្ជាក់ថាបានបង់លុយរួច`;
        fetch(`https://api.telegram.org/bot${token}/sendMessage?chat_id=${chat_id}&text=${message}&parse_mode=Markdown`)
        .then(res => { if(res.ok) { alert("បញ្ជូនទៅ Telegram ជោគជ័យ! ✅"); cart = []; updateSummary(); } });
    }
    renderProducts(currentPage);
</script>
