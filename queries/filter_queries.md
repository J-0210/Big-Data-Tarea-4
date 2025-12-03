# Consultas con filtros y operadores en MongoDB

Este archivo contiene los ejemplos de las consultas con filtros y operadores utilizadas en el proyecto.

---

## 1. Observar campos específicos, ordenar y limitar

// Mostrar 10 documentos (solo algunos campos)
db.products.find({}, { product_id:1, name:1, category:1, price:1, _id:0 }).limit(10)

// Mostrar 10 documentos ordenados por precio descendente
db.products.find({}, { product_id:1, name:1, price:1, _id:0 }).sort({ price: -1 }).limit(10)

// Paginación: saltar 20 y mostrar 10
db.products.find({}, { product_id:1, name:1, price:1 }).sort({ product_id:1 }).skip(20).limit(10)

});

## 2. Operadores de comparación
// Precio exactamente igual a 99.99
db.products.find({ price: 99.99 }).pretty()

// Precio mayor a 500
db.products.find({ price: { $gt: 500 } }).pretty()

// Precio entre 50 y 200 (inclusive)
db.products.find({ price: { $gte: 50, $lte: 200 } }).pretty()

// Categorías en un conjunto (Ropa o Deportes)
db.products.find({ category: { $in: ["Ropa", "Deportes"] } }).pretty()

// Excluir categorías (no Ropa ni Accesorios)
db.products.find({ category: { $nin: ["Ropa", "Accesorios"] } }).pretty()

// Stock distinto de 0
db.products.find({ stock: { $ne: 0 } }).pretty()


## 3. Filtrado por campos anidados (supplier)

// Todos los productos cuyo proveedor está en Medellín
db.products.find({ "supplier.city": "Medellín" }).pretty()

// Productos que vienen de proveedores S001 o S003
db.products.find({ "supplier.supplier_id": { $in: ["S001", "S003"] } }).pretty()

