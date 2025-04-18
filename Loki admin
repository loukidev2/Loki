<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LOKI_SHOP - Admin Panel</title>
  <style>
    body {
      background-color: #111;
      color: #fff;
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
    }
    h1 {
      color: #e00;
      text-align: center;
    }
    form {
      max-width: 400px;
      margin: 20px auto;
      background-color: #222;
      padding: 20px;
      border-radius: 10px;
    }
    input, button {
      display: block;
      width: 100%;
      margin: 10px 0;
      padding: 10px;
      border: none;
      border-radius: 5px;
    }
    input {
      background-color: #333;
      color: #fff;
    }
    button {
      background-color: #e00;
      color: #fff;
      cursor: pointer;
    }
    .product-list {
      max-width: 800px;
      margin: 30px auto;
    }
    .product-item {
      background-color: #222;
      margin-bottom: 15px;
      padding: 15px;
      border-radius: 8px;
    }
    .product-item img {
      max-width: 100px;
      border-radius: 5px;
    }
    .actions {
      margin-top: 10px;
    }
    .actions button {
      background-color: #c00;
      margin-right: 10px;
    }
  </style>
</head>
<body>
  <h1>LOKI_SHOP - Admin Panel</h1>  <form id="productForm">
    <input type="text" id="name" placeholder="Product Name" required />
    <input type="number" id="price" placeholder="Price ($)" required />
    <input type="url" id="image" placeholder="Image URL" required />
    <button type="submit">Add Product</button>
  </form>  <div class="product-list" id="adminProductList"></div>  <script>
    let products = JSON.parse(localStorage.getItem('products')) || [];

    const form = document.getElementById('productForm');
    const adminProductList = document.getElementById('adminProductList');

    form.addEventListener('submit', e => {
      e.preventDefault();
      const name = document.getElementById('name').value;
      const price = parseFloat(document.getElementById('price').value);
      const image = document.getElementById('image').value;

      products.push({ id: Date.now(), name, price, image });
      localStorage.setItem('products', JSON.stringify(products));
      form.reset();
      renderAdminProducts();
    });

    function renderAdminProducts() {
      adminProductList.innerHTML = '';
      products.forEach((product, index) => {
        const div = document.createElement('div');
        div.className = 'product-item';
        div.innerHTML = `
          <h3>${product.name}</h3>
          <img src="${product.image}" alt="${product.name}" />
          <p>Price: $${product.price}</p>
          <div class="actions">
            <button onclick="deleteProduct(${index})">Delete</button>
          </div>
        `;
        adminProductList.appendChild(div);
      });
    }

    function deleteProduct(index) {
      products.splice(index, 1);
      localStorage.setItem('products', JSON.stringify(products));
      renderAdminProducts();
    }

    renderAdminProducts();
  </script></body>
</html>
