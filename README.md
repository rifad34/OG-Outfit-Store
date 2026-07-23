# OG-Outfit-Store
<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>OG OUTFIT - Premium Fashion</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    .product-card { transition: all 0.3s; }
    .product-card:hover { transform: translateY(-8px); box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1); }
  </style>
</head>
<body class="bg-gray-50">

  <!-- Header -->
  <header class="bg-black text-white sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-6 py-4">
      <div class="flex justify-between items-center">
        <div class="text-3xl font-bold">OG OUTFIT</div>
        
        <nav class="hidden md:flex space-x-8 text-lg">
          <a href="#" class="hover:text-gray-300">Home</a>
          <a href="#shop" class="hover:text-gray-300">Shop</a>
          <a href="#categories" class="hover:text-gray-300">Categories</a>
          <a href="#about" class="hover:text-gray-300">About</a>
        </nav>

        <div class="flex items-center gap-4">
          <input type="text" id="search" placeholder="Search products..." 
                 class="bg-gray-800 text-white px-4 py-2 rounded-full w-64 hidden md:block">
          <a href="https://wa.me/8801312281209" target="_blank" 
             class="bg-green-500 hover:bg-green-600 px-5 py-2 rounded-full flex items-center gap-2">
            <i class="fab fa-whatsapp text-xl"></i>
          </a>
        </div>
      </div>
    </div>
  </header>

  <!-- Hero -->
  <section class="bg-gradient-to-br from-black via-gray-900 to-black text-white py-28 text-center">
    <div class="max-w-4xl mx-auto px-6">
      <h1 class="text-5xl md:text-7xl font-bold mb-6">Style That Defines You</h1>
      <p class="text-xl mb-10">Premium Quality Fashion • All Over Bangladesh Delivery</p>
      <a href="#shop" class="inline-block bg-white text-black px-10 py-4 rounded-full text-lg font-semibold hover:bg-gray-200">
        Shop Now
      </a>
    </div>
  </section>

  <!-- Categories -->
  <section id="categories" class="py-16 bg-white">
    <div class="max-w-7xl mx-auto px-6">
      <h2 class="text-4xl font-bold text-center mb-12">Categories</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
        <div class="bg-gray-100 p-8 text-center rounded-3xl hover:bg-gray-200 cursor-pointer">👕 T-Shirts</div>
        <div class="bg-gray-100 p-8 text-center rounded-3xl hover:bg-gray-200 cursor-pointer">👖 Jeans & Pants</div>
        <div class="bg-gray-100 p-8 text-center rounded-3xl hover:bg-gray-200 cursor-pointer">🧥 Hoodies</div>
        <div class="bg-gray-100 p-8 text-center rounded-3xl hover:bg-gray-200 cursor-pointer">👟 Shoes</div>
      </div>
    </div>
  </section>

  <!-- Products -->
  <section id="shop" class="py-16 bg-gray-100">
    <div class="max-w-7xl mx-auto px-6">
      <h2 class="text-4xl font-bold text-center mb-12">Our Products</h2>
      
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8" id="product-grid">
        <!-- Products will be added by JS -->
      </div>
    </div>
  </section>

  <!-- Product Modal -->
  <div id="product-modal" class="hidden fixed inset-0 bg-black/70 flex items-center justify-center z-50">
    <div class="bg-white max-w-2xl w-full mx-4 rounded-3xl overflow-hidden">
      <div class="p-8" id="modal-content">
        <!-- Dynamic content -->
      </div>
    </div>
  </div>

  <!-- Footer -->
  <footer class="bg-black text-white py-16">
    <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-3 gap-10">
      <div>
        <h3 class="text-2xl font-bold mb-4">OG OUTFIT</h3>
        <p>Premium Fashion Brand</p>
      </div>
      <div>
        <h4 class="font-semibold mb-4">Contact</h4>
        <p>WhatsApp: <a href="https://wa.me/8801312281209" class="text-green-400">+880 1312-281209</a></p>
        <p>Email: og.outfitbd@gmail.com</p>
      </div>
      <div>
        <h4 class="font-semibold mb-4">Delivery</h4>
        <p>সারা বাংলাদেশে হোম ডেলিভারি</p>
        <p>Online & Offline Available</p>
      </div>
    </div>
  </footer>

  <script>
    const products = [
      { id: 1, name: "Premium Cotton Shirt", price: "1299", img: "https://via.placeholder.com/400x400?text=Shirt" },
      { id: 2, name: "Slim Fit Jeans", price: "1899", img: "https://via.placeholder.com/400x400?text=Jeans" },
      { id: 3, name: "Casual Hoodie", price: "1599", img: "https://via.placeholder.com/400x400?text=Hoodie" },
      { id: 4, name: "Formal Shirt", price: "1399", img: "https://via.placeholder.com/400x400?text=Formal" },
    ];

    function renderProducts() {
      const grid = document.getElementById('product-grid');
      grid.innerHTML = '';
      
      products.forEach(product => {
        const card = document.createElement('div');
        card.className = 'bg-white rounded-3xl overflow-hidden shadow-lg product-card cursor-pointer';
        card.innerHTML = `
          <img src="${product.img}" class="w-full h-64 object-cover">
          <div class="p-6">
            <h3 class="font-semibold text-xl">${product.name}</h3>
            <p class="text-2xl font-bold mt-2">৳ ${product.price}</p>
            <button onclick="showProduct(${product.id}); event.stopImmediatePropagation()" 
              class="mt-6 w-full bg-black text-white py-3.5 rounded-2xl hover:bg-gray-800">
              View Details
            </button>
          </div>
        `;
        card.onclick = () => showProduct(product.id);
        grid.appendChild(card);
      });
    }

    function showProduct(id) {
      const product = products.find(p => p.id === id);
      if (!product) return;

      const modal = document.getElementById('product-modal');
      const content = document.getElementById('modal-content');
      
      content.innerHTML = `
        <div class="flex justify-end"><button onclick="closeModal()" class="text-3xl">×</button></div>
        <img src="${product.img}" class="w-full h-80 object-cover rounded-2xl mb-6">
        <h2 class="text-3xl font-bold">${product.name}</h2>
        <p class="text-4xl font-bold mt-3">৳ ${product.price}</p>
        <p class="mt-6 text-gray-600">High quality premium fabric. Perfect for everyday wear and special occasions.</p>
        <button onclick="orderNow('${product.name}')" 
          class="mt-8 w-full bg-green-500 hover:bg-green-600 text-white py-4 rounded-2xl text-lg font-semibold">
          Order via WhatsApp
        </button>
      `;
      modal.classList.remove('hidden');
    }

    function closeModal() {
      document.getElementById('product-modal').classList.add('hidden');
    }

    function orderNow(name) {
      const message = `Hello, I want to buy: ${name}`;
      window.open(`https://wa.me/8801312281209?text=${encodeURIComponent(message)}`, '_blank');
      closeModal();
    }

    // Initialize
    renderProducts();
  </script>
</body>
</html>
