---
name: finanzas-presupuesto-bancos
description: Controla presupuesto, ejecución, cierres bancarios y conciliación mensual de Sommos.
---

# Finanzas Sommos — Presupuesto y Bancos

## Propósito

Combinar el control presupuestario con la validación de caja real y el cierre bancario mensual.

Archivo principal:
- Spreadsheet ID: `1RXy19WZMPQePflFaFeIIHnh09BpJbwOnk6Wumw8bW4E`
- URL: `https://docs.google.com/spreadsheets/d/1RXy19WZMPQePflFaFeIIHnh09BpJbwOnk6Wumw8bW4E/edit`

## Alcance principal

Esta skill opera principalmente:
- `Presupuesto`
- `Bancos`

También puede consultar:
- `Transacciones`
- `Dashboard`
- `Runway Mensual`

## Presupuesto

La pestaña `Presupuesto` controla la comparación entre presupuesto y ejecución real.

Estructura funcional conocida por mes:
- Budget
- P&L
- %
- Resumen

## Regla de ejecución real

El P&L del presupuesto debe considerar únicamente movimientos que cumplan:

- Tipo = `Egreso`
- Estado pago = `Pagado/Cobrado`
- Fecha dentro del mes correspondiente

No incluir obligaciones `Pendiente` como ejecución real.

## Salaries

La línea `Salaries` puede consolidar varias categorías salariales, por ejemplo:
- IT salaries
- Sales salaries
- Finance salaries
- Operative salaries
- RH salaries

Antes de modificar la fórmula, revisar cómo está consolidando actualmente las categorías.

## Variación presupuestaria

Fórmula conceptual:

`(P&L - Budget) / Budget`

Interpretación:
- resultado negativo → bajo presupuesto
- resultado positivo → sobre presupuesto
- presupuesto igual a cero → tratar como N/A o según fórmula existente

Convención visual documentada:
- bajo presupuesto → verde
- sobre presupuesto → rojo

## Advertencia sobre burn

El total visible del presupuesto no necesariamente equivale al burn total.

Puede haber categorías de `Transacciones` que no estén incluidas en la matriz presupuestaria.

Por eso:
- no usar el P&L del presupuesto como burn total sin validación
- para burn ejecutivo usar la lógica definida en `Runway Mensual` / `Dashboard`

## Bancos

La pestaña `Bancos` representa cierres mensuales por banco/cuenta.

Campos funcionales conocidos:
- Banco / Entidad
- País
- Mes
- Moneda
- Saldo inicial
- TC inicial
- Saldo inicial USD
- Saldo final banco manual
- TC cierre
- Saldo final banco USD
- Responsable
- Notas
- Ingresos mes
- Egresos mes
- Saldo final calculado
- Diferencia
- Conciliación

## Regla de flujo bancario

Solo movimientos `Pagado/Cobrado` deben afectar bancos.

Los pendientes:
- no afectan saldo bancario
- no forman parte del flujo realizado

## Cierre bancario

Fórmula conceptual:

`Saldo final calculado = Saldo inicial + Ingresos - Egresos`

Luego:

`Diferencia = Saldo final real banco - Saldo final calculado`

Si la diferencia está dentro de la tolerancia definida por el modelo, la cuenta puede quedar `Conciliado`.

No inventar movimientos para forzar una conciliación.

## Investigación de diferencias

Si existe una diferencia:
1. revisar movimientos faltantes;
2. revisar duplicados;
3. revisar transferencias internas;
4. revisar fechas;
5. revisar moneda y TC;
6. revisar cargos bancarios;
7. comparar con extracto real.

La diferencia debe investigarse, no corregirse artificialmente.

## Cierre mensual

Antes de cerrar un mes:
1. confirmar transacciones completas;
2. revisar categorías;
3. revisar TC;
4. conciliar bancos;
5. revisar CxC y CxP;
6. revisar presupuesto vs real;
7. validar burn;
8. revisar Runway y Dashboard;
9. buscar errores de fórmulas.

## Reglas transversales obligatorias

- El Google Sheet `Finanzas Sommos — Workflow y Control` es la fuente viva.
- `Transacciones` es la fuente de verdad operativa.
- Antes de escribir, leer en vivo encabezados, fórmulas, validaciones y filas relacionadas.
- Nunca asumir posiciones históricas de columnas.
- Nunca duplicar una transacción existente.
- Nunca inventar movimientos para conciliar.
- `Pendiente` no equivale a dinero realizado.
- Después de cualquier modificación, verificar las vistas dependientes.
- Los snapshots en GitHub documentan contexto; si contradicen el Sheet, prevalece el Sheet.
