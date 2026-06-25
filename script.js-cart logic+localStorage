// Mock SA products for demo
const products = [
  {id: 1, name: "MTN Airtime R20", price: 20},
  {id: 2, name: "Vodacom Data 1GB", price: 85},
  {id: 3, name: "Prepaid Electricity R50", price: 50},
  {id: 4, name: "Simba Chips", price: 15},
  {id: 5, name: "Coke 2L", price: 25},
  {id: 6, name: "Bread Loaf", price: 18},
  {id: 7, name: "Telkom Airtime R10", price: 10},
  {id: 8, name: "Energy Drink", price: 22}
];

let cart = JSON.parse(localStorage.getItem('cart')) || [];

const productsDiv = document.getElementById('products');
const cartItemsDiv = document.getElementById('cart-items');
const cartCount = document.getElementById('cart-count');
const cartTotal = document.getElementById('cart-total');

// Display products
products.forEach(p => {
  productsDiv.innerHTML += `
    <div class="product">
      <h4>${p.name}</h4>
      <p>R${p.price}</p>
      <button onclick="addToCart(${p.id})">Add to Cart</button>
    </div>
  `;
});

// Add item to cart
function addToCart(id) {
  const item = cart.find(i => i.id === id);
  if (item) {
    item.qty += 1;
  } else {
    cart.push({...products.find(p => p.id === id), qty: 1});
  }
  saveCart();
  renderCart();
}

// Remove item
function removeFromCart(id) {
  cart = cart.filter(i => i.id !== id);
  saveCart();
  renderCart();
}

// Save to localStorage
function saveCart() {
  localStorage.setItem('cart', JSON.stringify(cart));
}

// Render cart
function renderCart() {
  cartItemsDiv.innerHTML = '';
  let total = 0;
  
  cart.forEach(item => {
    total += item.price * item.qty;
    cartItemsDiv.innerHTML += `
      <div class="cart-item">
        <span>${item.name} x${item.qty}</span>
        <span>R${item.price * item.qty} 
          <button onclick="removeFromCart(${item.id})" style="background:red;padding:2px 6px;margin-left:8px;">x</button>
        </span>
      </div>
    `;
  });
  
  cartCount.textContent = cart.reduce((sum, i) => sum + i.qty, 0);
  cartTotal.textContent = total.toFixed(2);
}

// Mock checkout
document.getElementById('checkout').onclick = () => {
  alert('Mock checkout complete! Cart would clear here.');
  cart = [];
  saveCart();
  renderCart();
};

renderCart(); // load cart on page load
