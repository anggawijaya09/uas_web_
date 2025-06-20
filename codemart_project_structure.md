# 📦 CodeMart - Complete Project Files

## 📁 Struktur Folder
```
codemart/
├── index.html
├── README.md
├── package.json
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── script.js
│   └── images/
│       └── .gitkeep
└── docs/
    └── API.md
```

---

## 📄 index.html
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CodeMart - Minimarket Modern</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo">🛒 CodeMart</div>
            <ul class="nav-links">
                <li><a href="#home">Beranda</a></li>
                <li><a href="#products">Produk</a></li>
                <li><a href="#about">Tentang</a></li>
                <li><a href="#contact">Kontak</a></li>
            </ul>
            <div class="cart-icon" onclick="toggleCart()">
                🛍️
                <span class="cart-count" id="cartCount">0</span>
            </div>
        </nav>
    </header>

    <div class="overlay" id="overlay" onclick="toggleCart()"></div>

    <main class="main-container">
        <section class="hero">
            <h1>Selamat Datang di CodeMart</h1>
            <p>Minimarket modern dengan teknologi terdepan untuk kebutuhan sehari-hari Anda</p>
        </section>

        <section class="search-section">
            <div class="search-container">
                <input type="text" class="search-box" placeholder="Cari produk..." id="searchInput">
            </div>
            
            <div class="category-filter">
                <button class="category-btn active" onclick="filterCategory('all')">Semua</button>
                <button class="category-btn" onclick="filterCategory('makanan')">🍎 Makanan</button>
                <button class="category-btn" onclick="filterCategory('minuman')">🥤 Minuman</button>
                <button class="category-btn" onclick="filterCategory('snack')">🍿 Snack</button>
                <button class="category-btn" onclick="filterCategory('kebutuhan')">🧴 Kebutuhan</button>
                <button class="category-btn" onclick="filterCategory('elektronik')">📱 Elektronik</button>
            </div>
        </section>

        <section class="products-grid" id="productsGrid">
            <!-- Products will be populated by JavaScript -->
        </section>

        <section class="stats-section">
            <div class="stat-card">
                <div class="stat-number" id="totalProducts">0</div>
                <div>Total Produk</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="totalCategories">5</div>
                <div>Kategori</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">24/7</div>
                <div>Buka Setiap Hari</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">⭐ 4.8</div>
                <div>Rating Pelanggan</div>
            </div>
        </section>
    </main>

    <div class="cart-sidebar" id="cartSidebar">
        <div class="cart-header">
            <h2>🛍️ Keranjang Belanja</h2>
            <button class="close-cart" onclick="toggleCart()">✕</button>
        </div>
        <div id="cartItems">
            <p style="text-align: center; color: #666; margin-top: 2rem;">Keranjang kosong</p>
        </div>
        <div class="cart-total">
            <h3>Total: Rp <span id="cartTotal">0</span></h3>
            <button class="checkout-btn" onclick="checkout()">Checkout Sekarang</button>
        </div>
    </div>

    <script src="assets/js/script.js"></script>
</body>
</html>
```

---

## 🎨 assets/css/style.css
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
}

.header {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    padding: 1rem 2rem;
    position: sticky;
    top: 0;
    z-index: 100;
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
}

.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
}

.logo {
    font-size: 2rem;
    font-weight: bold;
    color: white;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}

.nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
}

.nav-links a {
    color: white;
    text-decoration: none;
    font-weight: 500;
    transition: all 0.3s ease;
    padding: 0.5rem 1rem;
    border-radius: 20px;
}

.nav-links a:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-2px);
}

.cart-icon {
    position: relative;
    background: #ff6b6b;
    color: white;
    padding: 0.8rem;
    border-radius: 50%;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(255, 107, 107, 0.4);
}

.cart-icon:hover {
    transform: scale(1.1);
    box-shadow: 0 6px 20px rgba(255, 107, 107, 0.6);
}

.cart-count {
    position: absolute;
    top: -8px;
    right: -8px;
    background: #4ecdc4;
    color: white;
    border-radius: 50%;
    width: 20px;
    height: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.8rem;
    font-weight: bold;
}

.main-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
}

.hero {
    text-align: center;
    color: white;
    margin-bottom: 3rem;
}

.hero h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}

.hero p {
    font-size: 1.2rem;
    opacity: 0.9;
}

.search-section {
    margin-bottom: 3rem;
}

.search-container {
    display: flex;
    gap: 1rem;
    margin-bottom: 2rem;
}

.search-box {
    flex: 1;
    padding: 1rem;
    border: none;
    border-radius: 25px;
    font-size: 1rem;
    background: rgba(255, 255, 255, 0.9);
    backdrop-filter: blur(5px);
}

.search-box:focus {
    outline: none;
    box-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
}

.category-filter {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    justify-content: center;
}

.category-btn {
    padding: 0.7rem 1.5rem;
    border: none;
    border-radius: 20px;
    background: rgba(255, 255, 255, 0.2);
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    font-weight: 500;
}

.category-btn:hover, .category-btn.active {
    background: #4ecdc4;
    transform: translateY(-2px);
    box-shadow: 0 4px 15px rgba(78, 205, 196, 0.4);
}

.products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
}

.product-card {
    background: rgba(255, 255, 255, 0.95);
    border-radius: 20px;
    padding: 1.5rem;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
}

.product-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
}

.product-image {
    width: 100%;
    height: 200px;
    background: linear-gradient(45deg, #ff9a9e, #fecfef);
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    margin-bottom: 1rem;
    position: relative;
    overflow: hidden;
}

.product-image::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: linear-gradient(45deg, transparent, rgba(255,255,255,0.3), transparent);
    transform: rotate(45deg);
    animation: shimmer 3s infinite;
}

@keyframes shimmer {
    0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
    100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
}

.product-title {
    font-size: 1.3rem;
    font-weight: bold;
    color: #333;
    margin-bottom: 0.5rem;
}

.product-category {
    color: #666;
    font-size: 0.9rem;
    margin-bottom: 1rem;
    background: #f0f0f0;
    padding: 0.3rem 0.8rem;
    border-radius: 15px;
    display: inline-block;
}

.product-price {
    font-size: 1.5rem;
    font-weight: bold;
    color: #4ecdc4;
    margin-bottom: 1rem;
}

.product-actions {
    display: flex;
    gap: 1rem;
    align-items: center;
}

.quantity-control {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    background: #f0f0f0;
    border-radius: 20px;
    padding: 0.3rem;
}

.qty-btn {
    width: 30px;
    height: 30px;
    border: none;
    border-radius: 50%;
    background: #4ecdc4;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
}

.qty-btn:hover {
    background: #45b7aa;
    transform: scale(1.1);
}

.qty-display {
    min-width: 30px;
    text-align: center;
    font-weight: bold;
}

.add-to-cart {
    flex: 1;
    padding: 0.8rem;
    border: none;
    border-radius: 25px;
    background: linear-gradient(45deg, #ff6b6b, #ffa726);
    color: white;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease;
}

.add-to-cart:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(255, 107, 107, 0.4);
}

.cart-sidebar {
    position: fixed;
    right: -400px;
    top: 0;
    width: 400px;
    height: 100vh;
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(10px);
    transition: right 0.3s ease;
    z-index: 1000;
    padding: 2rem;
    overflow-y: auto;
    box-shadow: -5px 0 20px rgba(0, 0, 0, 0.1);
}

.cart-sidebar.open {
    right: 0;
}

.cart-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
    padding-bottom: 1rem;
    border-bottom: 2px solid #eee;
}

.close-cart {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    color: #666;
}

.cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background: #f9f9f9;
    border-radius: 10px;
    margin-bottom: 1rem;
}

.cart-total {
    margin-top: 2rem;
    padding-top: 2rem;
    border-top: 2px solid #eee;
}

.checkout-btn {
    width: 100%;
    padding: 1rem;
    background: linear-gradient(45deg, #4ecdc4, #44a08d);
    color: white;
    border: none;
    border-radius: 25px;
    font-size: 1.1rem;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease;
    margin-top: 1rem;
}

.checkout-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(78, 205, 196, 0.4);
}

.stats-section {
    margin-top: 4rem;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
}

.stat-card {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 2rem;
    text-align: center;
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.2);
}

.stat-number {
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
    color: #4ecdc4;
}

.overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 999;
    display: none;
}

.overlay.show {
    display: block;
}

@media (max-width: 768px) {
    .nav-links {
        display: none;
    }
    
    .hero h1 {
        font-size: 2rem;
    }
    
    .search-container {
        flex-direction: column;
    }
    
    .cart-sidebar {
        width: 100%;
        right: -100%;
    }
}
```

---

## ⚡ assets/js/script.js
```javascript
// Sample products data
const products = [
    {id: 1, name: "Nasi Bento Premium", category: "makanan", price: 25000, emoji: "🍱"},
    {id: 2, name: "Air Mineral 600ml", category: "minuman", price: 3000, emoji: "💧"},
    {id: 3, name: "Keripik Kentang", category: "snack", price: 8000, emoji: "🍟"},
    {id: 4, name: "Shampo Anti Ketombe", category: "kebutuhan", price: 15000, emoji: "🧴"},
    {id: 5, name: "Power Bank 10000mAh", category: "elektronik", price: 150000, emoji: "🔋"},
    {id: 6, name: "Roti Tawar Gandum", category: "makanan", price: 12000, emoji: "🍞"},
    {id: 7, name: "Kopi Susu Dingin", category: "minuman", price: 8000, emoji: "☕"},
    {id: 8, name: "Coklat Batang", category: "snack", price: 5000, emoji: "🍫"},
    {id: 9, name: "Sabun Mandi Cair", category: "kebutuhan", price: 18000, emoji: "🧼"},
    {id: 10, name: "Earphone Bluetooth", category: "elektronik", price: 85000, emoji: "🎧"},
    {id: 11, name: "Sushi Roll Set", category: "makanan", price: 35000, emoji: "🍣"},
    {id: 12, name: "Jus Jeruk Fresh", category: "minuman", price: 12000, emoji: "🧃"},
    {id: 13, name: "Biskuit Coklat Chip", category: "snack", price: 7000, emoji: "🍪"},
    {id: 14, name: "Pasta Gigi Fluoride", category: "kebutuhan", price: 11000, emoji: "🦷"},
    {id: 15, name: "Kabel Charger USB-C", category: "elektronik", price: 25000, emoji: "🔌"},
    {id: 16, name: "Sandwich Ayam", category: "makanan", price: 18000, emoji: "🥪"},
    {id: 17, name: "Teh Botol Sosro", category: "minuman", price: 4000, emoji: "🍵"},
    {id: 18, name: "Kerupuk Udang", category: "snack", price: 6000, emoji: "🦐"},
];

let cart = [];
let quantities = {};

// Initialize quantities
products.forEach(product => {
    quantities[product.id] = 1;
});

function renderProducts(productsToRender = products) {
    const grid = document.getElementById('productsGrid');
    grid.innerHTML = '';

    productsToRender.forEach(product => {
        const productCard = document.createElement('div');
        productCard.className = 'product-card';
        productCard.innerHTML = `
            <div class="product-image">${product.emoji}</div>
            <h3 class="product-title">${product.name}</h3>
            <span class="product-category">${product.category.charAt(0).toUpperCase() + product.category.slice(1)}</span>
            <div class="product-price">Rp ${product.price.toLocaleString()}</div>
            <div class="product-actions">
                <div class="quantity-control">
                    <button class="qty-btn" onclick="changeQuantity(${product.id}, -1)">-</button>
                    <span class="qty-display" id="qty-${product.id}">${quantities[product.id]}</span>
                    <button class="qty-btn" onclick="changeQuantity(${product.id}, 1)">+</button>
                </div>
                <button class="add-to-cart" onclick="addToCart(${product.id})">Tambah ke Keranjang</button>
            </div>
        `;
        grid.appendChild(productCard);
    });

    document.getElementById('totalProducts').textContent = productsToRender.length;
}

function changeQuantity(productId, change) {
    quantities[productId] = Math.max(1, quantities[productId] + change);
    document.getElementById(`qty-${productId}`).textContent = quantities[productId];
}

function addToCart(productId) {
    const product = products.find(p => p.id === productId);
    const quantity = quantities[productId];
    
    const existingItem = cart.find(item => item.id === productId);
    if (existingItem) {
        existingItem.quantity += quantity;
    } else {
        cart.push({ ...product, quantity });
    }

    updateCartUI();
    
    // Animation feedback
    const button = event.target;
    button.style.transform = 'scale(0.95)';
    button.textContent = '✓ Ditambahkan!';
    setTimeout(() => {
        button.style.transform = 'scale(1)';
        button.textContent = 'Tambah ke Keranjang';
    }, 1000);
}

function updateCartUI() {
    const cartCount = document.getElementById('cartCount');
    const cartItems = document.getElementById('cartItems');
    const cartTotal = document.getElementById('cartTotal');

    cartCount.textContent = cart.reduce((sum, item) => sum + item.quantity, 0);

    if (cart.length === 0) {
        cartItems.innerHTML = '<p style="text-align: center; color: #666; margin-top: 2rem;">Keranjang kosong</p>';
        cartTotal.textContent = '0';
        return;
    }

    cartItems.innerHTML = cart.map(item => `
        <div class="cart-item">
            <div>
                <div style="font-weight: bold;">${item.name}</div>
                <div style="color: #666; font-size: 0.9rem;">${item.quantity} x Rp ${item.price.toLocaleString()}</div>
            </div>
            <div style="display: flex; align-items: center; gap: 1rem;">
                <div style="font-weight: bold;">Rp ${(item.price * item.quantity).toLocaleString()}</div>
                <button onclick="removeFromCart(${item.id})" style="background: #ff6b6b; color: white; border: none; border-radius: 50%; width: 25px; height: 25px; cursor: pointer;">×</button>
            </div>
        </div>
    `).join('');

    const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
    cartTotal.textContent = total.toLocaleString();
}

function removeFromCart(productId) {
    cart = cart.filter(item => item.id !== productId);
    updateCartUI();
}

function toggleCart() {
    const sidebar = document.getElementById('cartSidebar');
    const overlay = document.getElementById('overlay');
    
    if (sidebar.classList.contains('open')) {
        sidebar.classList.remove('open');
        overlay.classList.remove('show');
    } else {
        sidebar.classList.add('open');
        overlay.classList.add('show');
    }
}

function checkout() {
    if (cart.length === 0) {
        alert('Keranjang kosong! Silakan tambahkan produk terlebih dahulu.');
        return;
    }

    const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
    const itemList = cart.map(item => `${item.name} (${item.quantity}x)`).join(', ');
    
    alert(`Terima kasih atas pembelian Anda!\n\nItem: ${itemList}\nTotal: Rp ${total.toLocaleString()}\n\nPesanan akan diproses segera.`);
    
    cart = [];
    updateCartUI();
    toggleCart();
}

function filterCategory(category) {
    // Update active button
    document.querySelectorAll('.category-btn').forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    // Filter products
    const filteredProducts = category === 'all' ? products : products.filter(p => p.category === category);
    renderProducts(filteredProducts);
}

function searchProducts() {
    const query = document.getElementById('searchInput').value.toLowerCase();
    const filteredProducts = products.filter(p => 
        p.name.toLowerCase().includes(query) || 
        p.category.toLowerCase().includes(query)
    );
    renderProducts(filteredProducts);
}

// Event listeners
document.getElementById('searchInput').addEventListener('input', searchProducts);

// Initialize the app
document.addEventListener('DOMContentLoaded', function() {
    renderProducts();
    updateCartUI();
});
```

---

## 📋 README.md
```markdown
# 🛒 CodeMart - Modern Minimarket Website

Sebuah website minimarket modern dengan teknologi terdepan dan user experience yang luar biasa.

## ✨ Features

- 🎨 **Modern UI/UX** - Glassmorphism design dengan animasi smooth
- 📱 **Responsive Design** - Bekerja sempurna di desktop dan mobile
- 🔍 **Search & Filter** - Cari produk dan filter berdasarkan kategori
- 🛍️ **Shopping Cart** - Keranjang belanja interaktif dengan sidebar
- 📊 **Real-time Stats** - Dashboard statistik real-time
- ⚡ **Fast Performance** - Loading cepat tanpa dependencies eksternal

## 🚀 Quick Start

1. Download semua file ke folder `codemart/`
2. Buka `index.html` di browser
3. Mulai berbelanja!

## 📁 Project Structure

```
codemart/
├── index.html          # Main HTML file
├── assets/
│   ├── css/
│   │   └── style.css   # All styles
│   └── js/
│       └── script.js   # JavaScript functionality
└── README.md           # This file
```

## 🛍️ Products Available

- **Makanan** (4 items): Nasi Bento, Roti, Sushi, Sandwich
- **Minuman** (4 items): Air Mineral, Kopi, Jus, Teh
- **Snack** (4 items): Keripik, Coklat, Biskuit, Kerupuk
- **Kebutuhan** (3 items): Shampo, Sabun, Pasta Gigi
- **Elektronik** (3 items): Power Bank, Earphone, Kabel

## 🔧 Customization

### Menambah Produk Baru
Edit file `assets/js/script.js` dan tambahkan objek baru ke array `products`:

```javascript
{
    id: 19, 
    name: "Nama Produk", 
    category: "kategori", 
    price: 10000, 
    emoji: "🎯"
}
```

### Mengubah Warna Tema
Edit variabel CSS di `assets/css/style.css`:

```css
:root {
    --primary-color: #4ecdc4;
    --secondary-color: #ff6b6b;
    --accent-color: #ffa726;
}
```

## 📱 Browser Support

- ✅ Chrome 60+
- ✅ Firefox 55+
- ✅ Safari 12+
- ✅ Edge 79+

## 📄 License

MIT License - Feel free to use and modify!

## 👨‍💻 Developer

Built with ❤️ for modern web experiences
```

---

## 📦 package.json
```json
{
  "name": "codemart",
  "version": "1.0.0",
  "description": "Modern minimarket website with advanced features",
  "main": "index.html",
  "scripts": {
    "start": "live-server --port=3000",
    "build": "echo 'No build process needed for vanilla HTML/CSS/JS'",
    "test": "echo 'Tests coming soon'"
  },
  "keywords": [
    "minimarket",
    "ecommerce",
    "javascript",
    "html5",
    "css3",
    "modern-ui"
  ],
  "author": "CodeMart Team",
  "license": "MIT",
  "devDependencies": {
    "live-server": "^1.2.2"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/yourusername/codemart.git"
  },
  "bugs": {
    "url": "https://github.com/yourusername/codemart/issues"
  },
  "homepage": "https://github.com/yourusername/codemart#readme"
}
```

---

## 📝 docs/API.md
```markdown
# CodeMart API Documentation

## Core Functions

### Products Management
- `renderProducts(array)` - Render produk ke grid
- `filterCategory(string)` - Filter produk berdasarkan kategori
- `searchProducts()` - Cari produk berdasarkan nama

### Cart Management
- `addToCart(productId)` - Tambah produk ke keranjang
- `removeFromCart(productId)` - Hapus produk dari keranjang
- `updateCartUI()` - Update tampilan keranjang
- `toggleCart()` - Buka/tutup