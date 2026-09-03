# Bancos y conciliación

## Propósito

Controlar el cierre mensual real de las cuentas bancarias de Sommos.

## Principio principal

Solo movimientos con Estado pago = `Pagado/Cobrado` afectan el flujo bancario.

Los movimientos `Pendiente` no afectan caja ni saldo bancario.

## Datos funcionales

Por banco y mes se pueden controlar:

- Banco / Entidad
- País
- Mes
- Moneda
- Saldo inicial
- TC inicial
- Saldo inicial USD
- Saldo final real banco
- TC cierre
- Saldo final USD
- Responsable
- Notas
- Ingresos del mes
- Egresos del mes
- Saldo final calculado
- Diferencia
- Conciliación

## Cálculo

`Saldo final calculado = Saldo inicial + Ingresos - Egresos`

`Diferencia = Saldo final real - Saldo final calculado`

Una cuenta puede quedar conciliada cuando la diferencia esté dentro de la tolerancia definida por el modelo.

## Regla de seguridad

Nunca inventar una transacción para hacer cuadrar un banco.

Si existe una diferencia, investigar:

- transacciones faltantes
- duplicados
- transferencias internas
- cargos bancarios
- fechas
- moneda
- TC
- movimientos registrados en cuenta incorrecta

## Referencia histórica

BancoSol julio 2026 fue conciliado.

Snapshot documentado:

- saldo inicial: Bs 3.202,06
- ingresos: Bs 43.617,92
- egresos: Bs 11.888,82
- saldo final: Bs 34.931,16

Meru y Scotiabank no tuvieron movimientos registrados en julio.

Estos datos son históricos; prevalece siempre el Sheet en vivo.
