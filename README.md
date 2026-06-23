# TPI_FoodStore_Programa2_
# Food Store – Sistema de Gestión de Pedidos

**Materia:** Programación 2 – UTN Tecnicatura Universitaria en Programación A Distancia  
**Alumno:** Garrido, Gonzalo  
**Entrega:** Trabajo Práctico Integrador (TPI)

---

## Descripción

Food Store es un sistema de consola desarrollado en Java 21 que permite gestionar
categorías, productos, usuarios y pedidos mediante un menú interactivo.
Toda la información se almacena **en memoria** usando Colecciones (ArrayList).

---

## Estructura del proyecto

```
src/
└── integrado/prog2/
    ├── Main.java                    ← Punto de entrada
    ├── entities/
    │   ├── Base.java                ← Clase abstracta base (id, eliminado, createdAt)
    │   ├── Calculable.java          ← Interfaz con calcularTotal()
    │   ├── Categoria.java
    │   ├── Producto.java
    │   ├── Usuario.java
    │   ├── Pedido.java              ← Implementa Calculable
    │   └── DetallePedido.java
    ├── enums/
    │   ├── Rol.java                 ← ADMIN, USUARIO
    │   ├── Estado.java              ← PENDIENTE, CONFIRMADO, TERMINADO, CANCELADO
    │   └── FormaPago.java           ← TARJETA, TRANSFERENCIA, EFECTIVO
    ├── exception/
    │   ├── EntidadNoEncontradaException.java
    │   ├── StockInvalidoException.java
    │   └── ValidacionException.java
    ├── service/
    │   ├── CategoriaService.java
    │   ├── ProductoService.java
    │   ├── UsuarioService.java
    │   └── PedidoService.java
    └── menu/
        ├── MenuUtils.java
        ├── CategoriaMenu.java
        ├── ProductoMenu.java
        ├── UsuarioMenu.java
        └── PedidoMenu.java
```

---

## Cómo ejecutar

### Requisitos
- Java 21 o superior instalado
- Terminal / consola

### Compilación

Desde la raíz del proyecto (donde está la carpeta `src`):

```bash
# Crear carpeta de salida
mkdir -p out

# Compilar todos los archivos .java
find src -name "*.java" | xargs javac -d out

# Ejecutar
java -cp out integrado.prog2.Main
```

### Con un IDE (IntelliJ IDEA / Eclipse / VS Code)
1. Importar el proyecto como proyecto Java simple.
2. Marcar `src` como carpeta fuente (Sources Root).
3. Ejecutar `Main.java`.

---

## Funcionalidades principales

| Módulo      | Operaciones disponibles                                      |
|-------------|--------------------------------------------------------------|
| Categorías  | Listar, Crear, Editar, Eliminar (baja lógica)               |
| Productos   | Listar, Listar por categoría, Crear, Editar, Eliminar        |
| Usuarios    | Listar, Crear, Editar, Eliminar (baja lógica)               |
| Pedidos     | Listar, Crear con detalles, Actualizar estado/pago, Eliminar |

---

## Reglas de negocio implementadas

- **Soft delete**: el campo `eliminado` se marca `true`; el objeto permanece en memoria.
- **Mail único**: no se permiten dos usuarios activos con el mismo mail.
- **Precio y stock**: no pueden ser negativos (se lanza `StockInvalidoException`).
- **Pedido sin usuario**: no permitido (se lanza `ValidacionException`).
- **Cantidad en detalle**: debe ser > 0 y no superar el stock disponible.
- **Categoría con productos**: no se puede eliminar si tiene productos activos.

---

## Video demostrativo

> 🔗 [Insertar link al video aquí]

## Documentación PDF

> https://github.com/GonGaFa/TPI_FoodStore_Programa2_/blob/1c8b3ae31662c41768db63fc6be359ab5c0866ff/TPI_FoodStore.pdf
