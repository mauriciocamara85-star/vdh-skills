---
name: informe-local
description: >
  Genera el informe diario de ventas de los locales MDQ Rivadavia o MDQ San Martín (Mar del Plata)
  a partir de una imagen o datos de la planilla de ventas. Detecta automáticamente de qué sucursal
  se trata según el encabezado de la planilla. Produce un mensaje listo para copiar y pegar en
  WhatsApp con: venta del día anterior vs objetivo, acumulado semanal, ranking semanal de vendedores,
  ranking mensual acumulado y objetivo del día siguiente con recupero de desvío.
---

# Skill: Informe Diario de Local (Rivadavia / San Martín)

Genera el informe diario de ventas de cualquiera de los dos locales, listo para WhatsApp.

---

## Paso 1 — Detectar la sucursal

Leer el encabezado de la planilla o imagen:
- Si dice **"MDQ Rivadavia"** o **"Rivadavia"** → aplicar config de Rivadavia
- Si dice **"MDQ San Martín"** o **"San Martín"** → aplicar config de San Martín
- Si no es claro → preguntar al usuario antes de continuar

---

## Configuración por sucursal

### Rivadavia
| Campo | Valor |
|---|---|
| Nombre en informe | Rivadavia |
| Todos los vendedores | Agus, Delfi, Nano, Juli, Mau |
| Ranking semanal | Agus, Delfi, Nano |
| Ranking mensual | Agus, Delfi, Nano |
| Cierre motivacional | "¡Vamos Rivadavia que [frase]! 🔥🙌" |

### San Martín
| Campo | Valor |
|---|---|
| Nombre en informe | San Martín |
| Todos los vendedores | Mel, Seba, Lau, Tizi, Mau, Nano |
| Ranking semanal | Seba, Mel, Lau |
| Ranking mensual | Seba, Mel, Lau |
| Cierre motivacional | "¡Vamos San Martín que [frase]! 🔥🙌" |

---

## Estructura del informe

### 1. Encabezado
Informe [Sucursal] – Semana [N]

### 2. Venta de ayer
- Día y fecha
- Objetivo del día
- Venta real del día
- Desvío absoluto y porcentual

### 3. Acumulado semana
- Rango de días
- Objetivo acumulado y venta real acumulada
- Desvío absoluto y porcentual

### 4. Ranking semana
- Solo los vendedores del ranking según sucursal
- Con medallas 🥇🥈🥉 y venta acumulada

### 5. Ranking mensual acumulado
- Suma ventas de cada vendedor en todas las semanas hasta ayer
- Con medallas 🥇🥈🥉

### 6. Acumulado general hasta ayer
- Objetivo total vs venta real total
- Desvío con 💚 si positivo, ❌ si negativo

### 7. Objetivo de hoy
- Objetivo base del día siguiente
- Si desvío semanal negativo → agregar recupero
- Cierre motivacional

---

## Cálculos clave

Desvío diario = Venta real ayer - Objetivo ayer
Desvío % = Desvío / Objetivo × 100
Acumulado semana = Suma ventas reales desde lunes hasta ayer
Ranking mensual = Suma ventas de cada vendedor del ranking en TODAS las semanas

---

## Formato de salida

- Texto plano sin asteriscos ni markdown
- Emojis tal como en los ejemplos
- Números: $1.073.334 (pesos con puntos de miles)
- Listo para copiar y pegar en WhatsApp
