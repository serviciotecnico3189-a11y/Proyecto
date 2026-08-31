# PrecioYa PA

**Comparador de precios de alimentos en supermercados de la ciudad de Panamá**

> Borrador del proyecto — Curso de Desarrollo de Aplicaciones Móviles
> Estudiante: `[ Nombre completo ]` · Profesor(a): `[ Nombre del docente ]` · Fecha: `[ dd/mm/aaaa ]`

---

## Índice

1. [Descripción del proyecto](#1-descripción-del-proyecto)
2. [Exposición del problema](#2-exposición-del-problema)
3. [Plataforma](#3-plataforma)
4. [Interfaz de usuario e interfaz de administrador](#4-interfaz-de-usuario-e-interfaz-de-administrador)
5. [Funcionalidad](#5-funcionalidad)
6. [Diseño (wireframes)](#6-diseño-wireframes)
7. [Próximos pasos](#7-próximos-pasos)

---

## 1. Descripción del proyecto

**PrecioYa PA** es una aplicación móvil, con un panel web complementario para administradores, diseñada para ayudar a los consumidores de la ciudad de Panamá a encontrar los precios más bajos de alimentos y productos de primera necesidad entre los principales supermercados de la localidad (Super 99, Rey, Riba Smith, El Machetazo, PriceSmart, entre otros).

La aplicación centraliza información de precios actualizada, permite comparar un mismo producto entre distintas cadenas y sucursales, y sugiere al usuario dónde realizar su compra para maximizar el ahorro.

El proyecto surge como respuesta al incremento sostenido del costo de la canasta básica en Panamá y a la dispersión de la información de precios entre cadenas, la cual actualmente el consumidor debe recopilar manualmente visitando cada supermercado o revisando folletos y aplicaciones independientes de cada cadena.

Este borrador cubre la definición conceptual del producto, la plataforma tecnológica propuesta, las interfaces de usuario y administrador, la funcionalidad principal (MVP) y los primeros wireframes que servirán de base para el desarrollo del prototipo funcional.

## 2. Exposición del problema

En la ciudad de Panamá, el precio de un mismo producto de la canasta básica puede variar de forma considerable entre supermercados, e incluso entre sucursales de una misma cadena, dependiendo de promociones, ubicación y frecuencia de reabastecimiento. Sin embargo, **no existe actualmente una herramienta unificada, confiable y de uso sencillo** que le permita al consumidor panameño comparar estos precios en tiempo real antes de decidir dónde comprar.

Causas y consecuencias identificadas:

- Cada supermercado publica sus precios y ofertas únicamente en su propia aplicación, sitio web o folleto físico, obligando al usuario a revisar varias fuentes distintas para comparar.
- La información de precios cambia con frecuencia (ofertas semanales, inflación, promociones puntuales) y no siempre está disponible o actualizada en línea.
- Los consumidores de menores ingresos, que son quienes más se benefician de identificar el precio más bajo, son frecuentemente quienes menos tiempo o herramientas tienen para hacer esta comparación manualmente.
- La falta de transparencia y comparación fomenta un gasto mayor al necesario en el hogar panameño, afectando de forma directa el presupuesto familiar.

**Pregunta central del problema:** ¿Cómo puede una aplicación móvil ayudar a los consumidores de la ciudad de Panamá a identificar, de forma rápida y confiable, en qué supermercado encontrarán los alimentos que necesitan al menor precio posible?

**Justificación:** una solución digital centralizada reduce el tiempo de búsqueda del consumidor, promueve la transparencia de precios en el mercado, incentiva la competencia entre cadenas y contribuye directamente a la economía del hogar panameño.

## 3. Plataforma

Se propone una aplicación móvil **multiplataforma** (Android e iOS con un solo código base), complementada con un **panel de administración web**.

### 3.1 Tecnologías propuestas

| Componente | Tecnología propuesta | Justificación |
|---|---|---|
| App móvil (usuario) | Flutter (Dart) o React Native | Un solo código base para Android e iOS; buen soporte de mapas y notificaciones. |
| Panel administrador | Aplicación web (React o Vue) responsive | Permite cargar y actualizar precios desde cualquier navegador. |
| Backend / API | Node.js con Express o NestJS | API REST para servir productos, precios, tiendas y usuarios. |
| Base de datos | PostgreSQL o MongoDB | Almacenamiento estructurado de productos, precios históricos, tiendas y usuarios. |
| Servicios en la nube | Firebase / AWS | Autenticación, notificaciones push, almacenamiento de imágenes. |
| Mapas y geolocalización | Google Maps Platform | Ubicación de sucursales cercanas y cálculo de rutas de compra. |

### 3.2 Dispositivos y requisitos mínimos

- Android 8.0 (Oreo) en adelante.
- iOS 14 en adelante.
- Conexión a internet para sincronizar precios; modo de consulta offline de la última lista descargada.
- Permisos de ubicación (opcional) para sugerir supermercados cercanos.

## 4. Interfaz de usuario e interfaz de administrador

El sistema contempla **dos interfaces** claramente diferenciadas: el consumidor final (app móvil) y el administrador de contenido/precios (panel web).

### 4.1 Interfaz de usuario (consumidor — app móvil)

- **Inicio / Buscador:** acceso rápido a la búsqueda de productos, categorías y ofertas destacadas del día.
- **Comparación de precios:** muestra el mismo producto en distintos supermercados y sucursales, resaltando la opción más económica.
- **Lista de compras:** permite guardar productos, ver el ahorro estimado y sugerir una ruta de compra.
- **Mapa de supermercados:** ubica las sucursales más cercanas y permite filtrar por cadena.
- **Perfil:** historial de búsquedas, listas guardadas, preferencias y notificaciones de ofertas.

El diseño prioriza la simplicidad visual y un flujo de máximo 2-3 toques entre la búsqueda de un producto y ver su comparación de precios.

### 4.2 Interfaz de administrador (panel web)

- **Dashboard:** resumen general de productos, sucursales activas y reportes pendientes.
- **Gestión de productos:** alta, edición y categorización de productos.
- **Gestión de sucursales:** registro de supermercados y sucursales con su ubicación.
- **Gestión de precios:** actualización individual o carga masiva (CSV) de precios.
- **Gestión de usuarios y permisos:** control de qué administrador edita qué cadena o sucursal.
- **Validación de reportes comunitarios:** revisión de precios reportados por usuarios antes de publicarlos.

## 5. Funcionalidad

### 5.1 Funcionalidades para el usuario (consumidor)

- Registro e inicio de sesión (correo, teléfono o cuenta de Google).
- Búsqueda de productos por nombre, categoría o código de barras (escaneo con cámara).
- Comparación de precios entre supermercados y sucursales, con indicador del más económico.
- Creación y edición de listas de compras con cálculo automático de ahorro.
- Sugerencia de ruta de compra cuando la lista incluye productos en distintos supermercados.
- Geolocalización de sucursales cercanas.
- Notificaciones push de ofertas relevantes.
- Reporte comunitario de precios vistos en tienda.
- Historial de precios de un producto.

### 5.2 Funcionalidades para el administrador

- Autenticación con roles y permisos (super admin, admin de cadena, editor de sucursal).
- Alta, edición y desactivación de productos, categorías, supermercados y sucursales.
- Actualización individual y carga masiva de precios (CSV/Excel).
- Revisión, aprobación o rechazo de precios reportados por la comunidad.
- Panel de métricas: productos más buscados, sucursales desactualizadas, actividad de usuarios.
- Exportación de reportes en CSV/PDF.

### 5.3 Alcance del MVP

La primera entrega funcional priorizará: registro/inicio de sesión, búsqueda y comparación de precios de un catálogo inicial, lista de compras con cálculo de ahorro, mapa de sucursales cercanas y el panel de administrador con gestión manual de productos, sucursales y precios. El escaneo de código de barras, las notificaciones push personalizadas y el historial gráfico de precios quedan para fases posteriores.

## 6. Diseño (wireframes)

Bocetos de baja fidelidad de las pantallas principales. Se refinarán visualmente en la etapa de diseño de interfaz (UI).

### Usuario — Inicio / Buscador de producto
![Pantalla de inicio y buscador](./wireframes/1_home_busqueda.png)

### Usuario — Comparación de precios
![Comparación de precios](./wireframes/2_comparacion_precios.png)

### Usuario — Lista de compras
![Lista de compras](./wireframes/3_lista_compras.png)

### Usuario — Mapa de supermercados cercanos
![Mapa de supermercados](./wireframes/4_mapa_tiendas.png)

### Administrador — Panel de gestión de precios
![Panel de administrador](./wireframes/5_panel_admin.png)

## 7. Próximos pasos

- [ ] Validar el flujo de pantallas con usuarios potenciales (prueba de usabilidad informal).
- [ ] Definir el modelo de datos completo (entidad-relación) para productos, precios, sucursales y usuarios.
- [ ] Diseñar la interfaz visual de alta fidelidad (UI) a partir de estos wireframes.
- [ ] Estructurar el repositorio en carpetas: `/app` (móvil), `/backend` (API) y `/admin` (panel web).
- [ ] Documentar el avance de forma incremental en este README.
