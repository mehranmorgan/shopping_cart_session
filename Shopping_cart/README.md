
<p align="center">
  <img src="https://img.shields.io/badge/Django-Cart-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django Cart Badge">
  <img src="https://img.shields.io/badge/Session-Based-Lightweight-4B8BBE?style=for-the-badge" alt="Session Badge">
</p>

<h1 align="center">🛒 Django Session-Based Shopping Cart</h1>

<p align="center">
  A minimal and extensible shopping cart system built on Django sessions — no database required.
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-usage">Usage</a> •
  <a href="#-cart-data-structure">Cart Structure</a> •
  <a href="#️-demo">Demo</a> •
  <a href="#-license">License</a>
</p>

---

## 🚀 Features

- ✅ Add / remove / update cart items
- 📦 Stored in user sessions (not database)
- 🧠 Auto-fetches product data from Django `Product` model
- 💰 Calculates item-wise and total price
- 🛠 Easy to extend for discounts, coupons, or shipping

---

## 🧠 Usage

### 1. Initialize Cart

```python
from path.to.cart import Cart

cart = Cart(request)
```

### 2. Add Product to Cart

```python
cart.add(pk=1, qty=3)
```

### 3. Iterate Over Cart Items

```python
for item in cart:
    print(item['product'].name)
    print(item['qty'], item['total'])
```

### 4. Delete or Clear Cart

```python
cart.delete(id=1)
cart.remove()
```

### 5. Count and Total

```python
cart.count()  # Number of items
cart.total()  # Total price
```

---

## 🧾 Cart Data Structure (In Session)

```json
{
  "1": {
    "id": 1,
    "price": "20000",
    "qty": 2
  },
  "2": {
    "id": 2,
    "price": "15000",
    "qty": 1
  }
}
```

---

## ⚙️ Product Model Example

```python
class Product(models.Model):
    name = models.CharField(max_length=255)
    price = models.PositiveIntegerField()
    off_price = models.PositiveIntegerField()
```

> The cart uses `off_price` as the selling price

---

## 🔥 Demo

> 🔗 [Live Demo](https://yourdomain.com) *(add your deployed link here)*  
> 🧪 Or test directly in your Django views.

---

## 🧩 Advanced Tips

- You can customize the `Cart` class to:
  - Apply discount codes
  - Include shipping fees
  - Persist cart items across sessions (optional)

---

## 📄 License

Released under the MIT License.

<p align="center">
  Made with ❤️ using <strong>Django</strong>
</p>
