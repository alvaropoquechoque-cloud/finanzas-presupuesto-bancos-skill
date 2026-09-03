# Presupuesto

## Propósito

Controlar el presupuesto mensual de Sommos y compararlo contra la ejecución real.

## Fuente de ejecución

El P&L mensual debe calcularse desde `Transacciones` usando únicamente:

- Tipo = `Egreso`
- Estado pago = `Pagado/Cobrado`
- Fecha correspondiente al mes analizado

Una CxP pendiente no forma parte del P&L realizado.

## Estructura conocida

La matriz presupuestaria contiene por mes:

- Budget
- P&L
- %
- Resumen

Categorías documentadas:

- Salaries
- Outsourced services
- Contingency
- RH expenses
- Administrative expenses
- Travel
- Innovatech
- Sales expenses
- Product expenses
- Softwares for development
- Platform cost
- Bank fees
- Exchange rate differences
- Financial expense
- Taxes
- Startup Chile
- Marketing services

## Salaries

`Salaries` puede consolidar diferentes categorías salariales.

Antes de modificar fórmulas, revisar qué categorías está agrupando actualmente el Sheet.

## Variación

Fórmula conceptual:

`(P&L - Budget) / Budget`

Interpretación:

- negativo = bajo presupuesto
- positivo = sobre presupuesto
- Budget = 0 → N/A o lógica vigente en el Sheet

Convención visual conocida:

- bajo presupuesto → verde
- sobre presupuesto → rojo

## Advertencia

El P&L visible del presupuesto no necesariamente equivale al burn total.

Puede haber egresos en categorías de `Transacciones` que no estén incluidas en la matriz presupuestaria.

No usar automáticamente el total de Presupuesto como burn ejecutivo.
