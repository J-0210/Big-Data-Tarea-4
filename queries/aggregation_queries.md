# Consultas de agregacion para calcular estadisticas en MongoDB

Este archivo contiene los ejemplos de las consultas agregacion para calcular estadisticas utilizadas en el proyecto.

---

## 1. Productos por categoría

db.products.aggregate
  { $group: { _id: "$category", total: { $sum: 1 } }},
  { $sort: { total: -1 }}

## 2. Promedio de precios por categoría
db.products.aggregate
  { $group: { _id: "$category", avgPrice: { $avg: "$price" }, count: { $sum: 1 } }},
  { $sort: { avgPrice: -1 }}


## 3. valor de inventario por proveedor

db.products.aggregate
  { $project: {
      supplier: "$supplier.name",
      totalValue: { $multiply: ["$price", "$stock"] }
  }},
  { $group: { _id: "$supplier", total: { $sum: "$totalValue" }}},
  { $sort: { total: -1 }}
