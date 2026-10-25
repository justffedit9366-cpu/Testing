<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Buddy Sales | Fresh Finds, Best Prices</title>
  <style>
    :root {
      --primary: #10b981;
      --primary-dark: #059669;
      --secondary: #0f172a;
      --accent: #f59e0b;
      --bg: #f8fafc;
      --card-bg: #ffffff;
      --text: #1e293b;
      --muted: #64748b;
      --border: #e2e8f0;
      --shadow: 0 10px 25px -5px rgba(15, 23, 42, 0.08);
      --radius: 16px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      scroll-behavior: smooth;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.5;
      padding-bottom: 80px;
    }

    /* Sticky Header */
    header {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border);
      padding: 0.85rem 1.25rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .brand {
      display: flex;
      flex-direction: column;
    }

    .brand h1 {
      font-size: 1.4rem;
      font-weight: 800;
      color: var(--secondary);
      text-transform: capitalize;
      letter-spacing: -0.5px;
    }

    .brand h1 span {
      color: var(--primary);
    }

    .brand p {
      font-size: 0.78rem;
      color: var(--muted);
      text-transform: capitalize;
    }

    .cart-pill {
      background: var(--secondary);
      color: #fff;
      padding: 0.55rem 1rem;
      border-radius: 999px;
      text-decoration: none;
      font-size: 0.9rem;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      transition: transform 0.2s, background 0.2s;
    }

    .cart-pill:hover {
      background: var(--primary-dark);
      transform: translateY(-1px);
    }

    .cart-badge {
      background: var(--primary);
      color: #fff;
      font-size: 0.75rem;
      padding: 0.1rem 0.5rem;
      border-radius: 999px;
      font-weight: 700;
    }

    /* Full-Width Hero Section */
    .hero {
      position: relative;
      width: 100%;
      min-height: 75vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      color: #fff;
      overflow: hidden;
      background: #0f172a;
    }

    .hero-bg {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      opacity: 0.45;
      transition: transform 0.6s ease;
    }

    .hero-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(
        to bottom,
        rgba(15, 23, 42, 0.55),
        rgba(15, 23, 42, 0.85)
      );
    }

    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 700px;
      padding: 2rem 1.25rem;
    }

    .hero-tag {
      display: inline-block;
      background: rgba(16, 185, 129, 0.2);
      border: 1px solid rgba(16, 185, 129, 0.5);
      color: #6ee7b7;
      padding: 0.35rem 0.9rem;
      border-radius: 999px;
      font-size: 0.85rem;
      font-weight: 600;
      margin-bottom: 1rem;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .hero h2 {
      font-size: clamp(2.2rem, 6vw, 3.5rem);
      font-weight: 800;
      line-height: 1.15;
      margin-bottom: 0.85rem;
      text-transform: capitalize;
    }

    .hero p {
      font-size: clamp(1rem, 2.5vw, 1.2rem);
      color: #cbd5e1;
      margin-bottom: 1.75rem;
    }

    .btn-primary {
      display: inline-block;
      background: var(--primary);
      color: #fff;
      font-weight: 700;
      font-size: 1.05rem;
      padding: 0.9rem 2rem;
      border-radius: 999px;
      text-decoration: none;
      border: none;
      cursor: pointer;
      box-shadow: 0 10px 20px -5px rgba(16, 185, 129, 0.5);
      transition: background 0.2s, transform 0.2s;
    }

    .btn-primary:hover {
      background: var(--primary-dark);
      transform: translateY(-2px);
    }

    /* Section Styling */
    .container {
      max-width: 1120px;
      margin: 0 auto;
      padding: 3rem 1.25rem;
    }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 1.5rem;
    }

    .section-header h3 {
      font-size: 1.65rem;
      color: var(--secondary);
    }

    .section-header p {
      color: var(--muted);
      font-size: 0.95rem;
    }

    .carousel-controls {
      display: flex;
      gap: 0.5rem;
    }

    .ctrl-btn {
      background: #fff;
      border: 1px solid var(--border);
      color: var(--secondary);
      width: 40px;
      height: 40px;
      border-radius: 50%;
      font-size: 1.1rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
      transition: background 0.2s, color 0.2s;
    }

    .ctrl-btn:hover {
      background: var(--secondary);
      color: #fff;
    }

    /* Product Carousel */
    .carousel-wrapper {
      position: relative;
    }

    .carousel {
      display: flex;
      gap: 1.25rem;
      overflow-x: auto;
      scroll-snap-type: x mandatory;
      scroll-behavior: smooth;
      padding: 0.5rem 0.25rem 1.5rem;
      scrollbar-width: thin;
    }

    .carousel::-webkit-scrollbar {
      height: 6px;
    }

    .carousel::-webkit-scrollbar-thumb {
      background: #cbd5e1;
      border-radius: 999px;
    }

    .product-card {
      flex: 0 0 280px;
      scroll-snap-align: start;
      background: var(--card-bg);
      border-radius: var(--radius);
      border: 1px solid var(--border);
      overflow: hidden;
      box-shadow: var(--shadow);
      display: flex;
      flex-direction: column;
      transition: transform 0.25s ease;
    }

    .product-card:hover {
      transform: translateY(-4px);
    }

    .product-img-wrap {
      position: relative;
      height: 210px;
      background: #f1f5f9;
      overflow: hidden;
    }

    .product-img-wrap img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.35s ease;
    }

    .product-card:hover .product-img-wrap img {
      transform: scale(1.05);
    }

    .product-badge {
      position: absolute;
      top: 10px;
      left: 10px;
      background: rgba(15, 23, 42, 0.8);
      color: #fff;
      font-size: 0.72rem;
      font-weight: 700;
      padding: 0.25rem 0.65rem;
      border-radius: 999px;
    }

    .product-body {
      padding: 1.15rem;
      display: flex;
      flex-direction: column;
      flex-grow: 1;
      justify-content: space-between;
    }

    .product-title {
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--secondary);
      margin-bottom: 0.35rem;
    }

    .product-price {
      font-size: 1.25rem;
      font-weight: 800;
      color: var(--primary-dark);
      margin-bottom: 1rem;
    }

    .add-btn {
      width: 100%;
      background: var(--secondary);
      color: #fff;
      border: none;
      padding: 0.75rem;
      border-radius: 10px;
      font-weight: 700;
      cursor: pointer;
      transition: background 0.2s;
    }

    .add-btn:hover {
      background: var(--primary);
    }

    /* Order & Checkout Section */
    .order-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 1.75rem;
    }

    @media (min-width: 820px) {
      .order-grid {
        grid-template-columns: 1.1fr 0.9fr;
      }
    }

    .card-box {
      background: var(--card-bg);
      border-radius: var(--radius);
      border: 1px solid var(--border);
      padding: 1.5rem;
      box-shadow: var(--shadow);
    }

    .card-box h4 {
      font-size: 1.25rem;
      margin-bottom: 1rem;
      color: var(--secondary);
    }

    .cart-list {
      list-style: none;
      margin-bottom: 1.25rem;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.75rem 0;
      border-bottom: 1px solid var(--border);
      gap: 0.75rem;
    }

    .cart-item-info {
      flex-grow: 1;
    }

    .cart-item-title {
      font-weight: 600;
      font-size: 0.95rem;
    }

    .cart-item-sub {
      font-size: 0.82rem;
      color: var(--muted);
    }

    .qty-controls {
      display: flex;
      align-items: center;
      gap: 0.4rem;
    }

    .qty-btn {
      width: 28px;
      height: 28px;
      border-radius: 6px;
      border: 1px solid var(--border);
      background: #f8fafc;
      font-weight: 700;
      cursor: pointer;
    }

    .form-group {
      margin-bottom: 1rem;
    }

    .form-group label {
      display: block;
      font-size: 0.88rem;
      font-weight: 600;
      margin-bottom: 0.35rem;
      color: var(--secondary);
    }

    .form-group input {
      width: 100%;
      padding: 0.75rem 0.9rem;
      border: 1px solid var(--border);
      border-radius: 10px;
      font-size: 0.95rem;
      outline: none;
    }

    .form-group input:focus {
      border-color: var(--primary);
    }

    .order-preview {
      width: 100%;
      height: 190px;
      padding: 0.85rem;
      border-radius: 10px;
      border: 1px solid var(--border);
      background: #f8fafc;
      font-family: monospace;
      font-size: 0.86rem;
      resize: none;
      margin-bottom: 1rem;
      color: var(--secondary);
    }

    .action-buttons {
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
    }

    .btn-copy,
    .btn-email,
    .btn-wa-order {
      width: 100%;
      padding: 0.85rem 1rem;
      border-radius: 10px;
      font-weight: 700;
      font-size: 0.95rem;
      border: none;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      transition: opacity 0.2s, transform 0.15s;
    }

    .btn-copy {
      background: var(--secondary);
      color: #fff;
    }

    .btn-email {
      background: var(--primary);
      color: #fff;
    }

    .btn-wa-order {
      background: #25d366;
      color: #fff;
    }

    .btn-copy:hover,
    .btn-email:hover,
    .btn-wa-order:hover {
      opacity: 0.93;
      transform: translateY(-1px);
    }

    .toast {
      margin-top: 0.65rem;
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--primary-dark);
      min-height: 1.2rem;
      text-align: center;
    }

    /* Footer */
    footer {
      text-align: center;
      padding: 2rem 1.25rem;
      border-top: 1px solid var(--border);
      color: var(--muted);
      font-size: 0.9rem;
      background: #fff;
    }

    footer a {
      color: var(--primary-dark);
      text-decoration: none;
      font-weight: 600;
    }

    /* Floating WhatsApp Button */
    .wa-float {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 999;
      background: #25d366;
      color: #fff;
      padding: 0.8rem 1.15rem;
      border-radius: 999px;
      text-decoration: none;
      font-weight: 700;
      font-size: 0.92rem;
      box-shadow: 0 8px 20px rgba(37, 211, 102, 0.4);
      display: flex;
      align-items: center;
      gap: 0.5rem;
      transition: transform 0.2s ease;
    }

    .wa-float:hover {
      transform: scale(1.05);
    }
  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <div class="brand">
      <h1>buddy <span>sales</span></h1>
      <p>fresh finds, best prices</p>
    </div>
    <a href="#order-section" class="cart-pill">
      🛒 Cart <span class="cart-badge" id="cart-count">0</span>
    </a>
  </header>

  <!-- Hero Section -->
  <section class="hero">
    <img
      class="hero-bg"
      id="hero-img"
      src="https://www.magnific.com/free-vector/variety-stores_779752.htm#fromView=keyword&page=1&position=22&uuid=13d08467-9cb4-463d-bbb8-cc07d73d5f69&track=ais_hybrid&query=Shops+stores"
      onerror="this.onerror=null; this.src='https://i.ibb.co/sZmczkk/1792922579632.jpg';"
      alt="Buddy Sales Storefront"
    />
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <span class="hero-tag">Welcome to Buddy Sales</span>
      <h2>Fresh Finds, Best Prices</h2>
      <p>Discover daily essentials, curated value bundles, and unbeatable store deals delivered with care.</p>
      <a href="#products-section" class="btn-primary">Shop Now ↓</a>
    </div>
  </section>

  <!-- Product Carousel Section -->
  <section class="container" id="products-section">
    <div class="section-header">
      <div>
        <h3>Featured Products</h3>
        <p>Swipe or use arrows to browse our top picks</p>
      </div>
      <div class="carousel-controls">
        <button class="ctrl-btn" id="prev-btn" aria-label="Previous slide">‹</button>
        <button class="ctrl-btn" id="next-btn" aria-label="Next slide">›</button>
      </div>
    </div>

    <div class="carousel-wrapper">
      <div class="carousel" id="product-carousel"></div>
    </div>
  </section>

  <!-- Cart & Customer Order Form -->
  <section class="container" id="order-section">
    <div class="section-header">
      <div>
        <h3>Complete Your Order</h3>
        <p>Review your cart, copy your order summary, or send directly via Email</p>
      </div>
    </div>

    <div class="order-grid">
      <!-- Left: Cart + Customer Form -->
      <div class="card-box">
        <h4>1. Your Cart & Details</h4>
        <ul class="cart-list" id="cart-items-list"></ul>

        <div class="form-group">
          <label for="cust-name">Customer Name *</label>
          <input type="text" id="cust-name" placeholder="Enter your full name" required />
        </div>

        <div class="form-group">
          <label for="cust-phone">Phone Number *</label>
          <input type="tel" id="cust-phone" placeholder="Enter your mobile number" required />
        </div>
      </div>

      <!-- Right: Live Order Preview + Copy & Email Actions -->
      <div class="card-box">
        <h4>2. Order Summary (Copy or Send)</h4>
        <textarea id="order-preview" class="order-preview" readonly></textarea>

        <div class="action-buttons">
          <button type="button" class="btn-copy" id="copy-order-btn">
            📋 Copy Order Text
          </button>
          <button type="button" class="btn-email" id="email-order-btn">
            ✉️ Send Order to Owner Email
          </button>
          <button type="button" class="btn-wa-order" id="wa-order-btn">
            💬 Send Order on WhatsApp
          </button>
        </div>
        <div class="toast" id="status-toast"></div>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <p><strong>Buddy Sales</strong> — Fresh Finds, Best Prices</p>
    <p>Owner Email: <a href="mailto:justffedit9366@gmail.com">justffedit9366@gmail.com</a></p>
  </footer>

  <!-- Floating WhatsApp Button -->
  <a
    href="https://wa.me/9999999978"
    target="_blank"
    rel="noopener noreferrer"
    class="wa-float"
  >
    💬 Chat on WhatsApp
  </a>

  <script>
    const OWNER_EMAIL = "justffedit9366@gmail.com";
    const WHATSAPP_NUMBER = "9999999978";

    const products = [
      {
        id: 1,
        name: "Buddy Fresh Combo Pack",
        price: 299,
        badge: "Best Seller",
        image: "https://i.ibb.co/sZmczkk/1792922579632.jpg"
      },
      {
        id: 2,
        name: "Everyday Store Essentials",
        price: 449,
        badge: "Fresh Arrival",
        image: "https://i.ibb.co/C5Z787B1/1792922791506.jpg"
      },
      {
        id: 3,
        name: "Super Saver Value Box",
        price: 599,
        badge: "Top Value",
        image: "https://i.ibb.co/3mMLHwjK/1792922864143.jpg"
      },
      {
        id: 4,
        name: "Daily Kitchen Select",
        price: 199,
        badge: "Hot Deal",
        image: "https://i.ibb.co/sZmczkk/1792922579632.jpg"
      },
      {
        id: 5,
        name: "Premium Home Basket",
        price: 749,
        badge: "Popular",
        image: "https://i.ibb.co/C5Z787B1/1792922791506.jpg"
      },
      {
        id: 6,
        name: "Weekend Special Bundle",
        price: 399,
        badge: "Limited",
        image: "https://i.ibb.co/3mMLHwjK/1792922864143.jpg"
      }
    ];

    const cart = {};

    const carouselEl = document.getElementById("product-carousel");
    const cartListEl = document.getElementById("cart-items-list");
    const cartCountEl = document.getElementById("cart-count");
    const custNameEl = document.getElementById("cust-name");
    const custPhoneEl = document.getElementById("cust-phone");
    const orderPreviewEl = document.getElementById("order-preview");
    const statusToastEl = document.getElementById("status-toast");

    // Render Product Carousel
    function renderProducts() {
      carouselEl.innerHTML = products
        .map(
          (p) => `
        <article class="product-card">
          <div class="product-img-wrap">
            <span class="product-badge">${p.badge}</span>
            <img src="${p.image}" alt="${p.name}" loading="lazy" />
          </div>
          <div class="product-body">
            <div>
              <h4 class="product-title">${p.name}</h4>
              <div class="product-price">₹${p.price}</div>
            </div>
            <button class="add-btn" onclick="addToCart(${p.id})">
              + Add to Cart
            </button>
          </div>
        </article>
      `
        )
        .join("");
    }

    // Add or update item in Cart
    window.addToCart = function (productId) {
      cart[productId] = (cart[productId] || 0) + 1;
      updateCartUI();
      showToast("Added to cart!");
    };

    window.changeQty = function (productId, delta) {
      if (!cart[productId]) return;
      cart[productId] += delta;
      if (cart[productId] <= 0) {
        delete cart[productId];
      }
      updateCartUI();
    };

    // Update Cart & Order Text Preview
    function updateCartUI() {
      const ids = Object.keys(cart);
      let totalItems = 0;
      let totalPrice = 0;

      if (ids.length === 0) {
        cartListEl.innerHTML = `<li style="color:#64748b; padding:0.5rem 0;">Your cart is empty. Click "Add to Cart" on any product above.</li>`;
      } else {
        cartListEl.innerHTML = ids
          .map((id) => {
            const prod = products.find((p) => p.id === Number(id));
            const qty = cart[id];
            const sub = prod.price * qty;
            totalItems += qty;
            totalPrice += sub;
            return `
              <li class="cart-item">
                <div class="cart-item-info">
                  <div class="cart-item-title">${prod.name}</div>
                  <div class="cart-item-sub">₹${prod.price} × ${qty} = ₹${sub}</div>
                </div>
                <div class="qty-controls">
                  <button class="qty-btn" onclick="changeQty(${prod.id}, -1)">-</button>
                  <span>${qty}</span>
                  <button class="qty-btn" onclick="changeQty(${prod.id}, 1)">+</button>
                </div>
              </li>
            `;
          })
          .join("");
      }

      cartCountEl.textContent = totalItems;
      generateOrderText(totalPrice);
    }

    function generateOrderText(totalPrice = 0) {
      const name = custNameEl.value.trim() || "(Not entered)";
      const phone = custPhoneEl.value.trim() || "(Not entered)";
      const ids = Object.keys(cart);

      let itemsLines = "No items added yet.";
      if (ids.length > 0) {
        totalPrice = 0;
        itemsLines = ids
          .map((id, index) => {
            const prod = products.find((p) => p.id === Number(id));
            const qty = cart[id];
            const sub = prod.price * qty;
            totalPrice += sub;
            return `${index + 1}. ${prod.name} x ${qty} = ₹${sub}
