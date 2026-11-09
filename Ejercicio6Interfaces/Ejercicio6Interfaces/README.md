# Ejercicio 6 - Polimorfismo via Interfaces

Proyecto Java Swing + consola para Apache NetBeans, sin dependencias externas.

## Abrir en NetBeans

1. Descomprime el ZIP.
2. En NetBeans usa **File > Open Project** y selecciona la carpeta `Ejercicio6Interfaces` (contiene `build.xml` y `nbproject`).
3. Haz clic en **Run Project (F6)**. Se abre la ventana Swing.

La ventana Swing esta construida directamente en `src/vista/VentanaPrincipal.java`, no en un formulario `.form` del GUI Builder. Se puede editar desde la pestaña **Source** de NetBeans.

## Compilar desde terminal

```bash
ant clean jar
java -jar dist/Ejercicio6Interfaces.jar
```

Para ejecutar el menu de consola (tras compilar):

```bash
java -cp build/classes principal.Main consola
```

## Funcionalidades

- 10 integraciones precargadas: pagos, logistica, FEL y consulta.
- Una sola coleccion persistente `ArrayList<IntegracionAPI>`.
- Interfaces `Transaccional`, `Documentable`, `Auditable`.
- `Comparable<IntegracionAPI>` para ordenar por latencia sin alterar el orden original.
- Buscar por ID y mostrar configuracion; consultar estado de conexion.
- Operaciones simuladas: cobro, reintegro, documento, consulta y auditoria.
- Operaciones no compatibles se ignoran con mensaje sin excepcion.
- MVC: modelo, vista Swing y consola, controlador, main.
- Sobrecarga `procesar(...)` en controlador usando parametros de interfaz.

**No se realizan solicitudes HTTP ni operaciones financieras reales.** Las direcciones son ejemplos locales.

## Pruebas manuales sugeridas

1. Listar: deben aparecer 10 integraciones.
2. Ordenar: primera C01 (70 ms), ultima F01 (230 ms).
3. Buscar P01: muestra parametros de configuracion.
4. P01 / Cobrar / Q150: mensaje de cobro simulado.
5. L01 / Reintegrar: mensaje IGNORADA, sin excepcion.
6. F01 / Documento: XML de ejemplo.
7. C01 / Consultar: estado simulado.
8. L03 / Documento: IGNORADA por desconexion.
9. P01 / Auditar: muestra contador de operaciones.

## Nota de diseno

La implementacion es un prototipo academico: los proveedores y respuestas son ficticios. La vista de consola se conserva por ser parte del enunciado; Swing ofrece la interfaz grafica para el puntaje adicional.
