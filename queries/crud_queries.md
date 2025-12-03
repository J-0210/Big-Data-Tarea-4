# Consultas CRUD en MongoDB

Este archivo contiene los ejemplos de las consultas CRUD utilizadas en la colección `products` del proyecto.

---

## 1. Crear (CREAT)

```js
db.products.insertOne({
  product_id: "P2000",
  name: "Producto de Prueba",
  category: "Prueba",
  price: 19.99,
  stock: 50
});
## 2. LEER (READ)
## 3. ACTUALIZAR (UPDATE)
## 4. ELIMINAR (DELETE)
