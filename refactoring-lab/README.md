# reyes-post1-u6

## Taller U6 - Refactorizacion de God Object aplicando SRP

Proyecto Maven del laboratorio `refactoring-lab` para identificar y refactorizar el antipatron **God Object**.

## Antipatron identificado

Se identifico el antipatron **God Object** en la clase `GestorBiblioteca`, ya que concentra demasiadas responsabilidades de distintos dominios del sistema en una sola clase.

## Responsabilidades encontradas en GestorBiblioteca

1. Gestion del catalogo de libros (agregar, buscar, listar).
2. Gestion de socios (registrar, validar, buscar).
3. Gestion de prestamos (prestar, devolver).
4. Generacion de reportes del sistema.

## Patron aplicado en la refactorizacion

Se aplico el principio **SRP (Single Responsibility Principle)**, separando cada responsabilidad en clases especializadas:

- `CatalogoLibros`
- `RegistroSocios`
- `ServicioPrestamos`
- `GeneradorReportes`

Y se introdujeron clases de dominio:

- `Libro`
- `Socio`

## Estructura principal

```text
refactoring-lab/
├── pom.xml
├── README.md
├── docs/
│   └── evidencias/
│       ├── salida-antes.txt
│       └── salida-despues.txt
└── src/
    └── main/
        └── java/
            └── com/universidad/antipatrones/
                ├── App.java
                ├── Main.java
                ├── GestorBiblioteca.java
                ├── Libro.java
                ├── Socio.java
                ├── CatalogoLibros.java
                ├── RegistroSocios.java
                ├── ServicioPrestamos.java
                └── GeneradorReportes.java
```

## Ejecucion y verificacion

### Compilacion

```bash
mvn compile
```

### Ejecucion

```bash
mvn exec:java
```

## Capturas de ejecucion (antes y despues)

### Antes de refactorizar (God Object)

Archivo: `docs/evidencias/salida-antes.txt`

```text
Libro agregado: Clean Code
Libro agregado: Design Patterns
Socio registrado: Ana Torres
Prestamo realizado: libro L01 a socio S01
=== REPORTE BIBLIOTECA ===
Libros registrados: 2
Libros disponibles: 1
Socios registrados: 1
Prestamos activos: 1
==========================
Libro devuelto: Clean Code
=== REPORTE BIBLIOTECA ===
Libros registrados: 2
Libros disponibles: 2
Socios registrados: 1
Prestamos activos: 1
==========================
```

### Despues de refactorizar (SRP)

Archivo: `docs/evidencias/salida-despues.txt`

```text
Libro agregado: Clean Code
Libro agregado: Design Patterns
Socio registrado: Ana Torres
Prestamo realizado: Clean Code -> socio S01
=== REPORTE BIBLIOTECA ===
Libros registrados : 2
Libros disponibles : 1
Socios registrados : 1
Prestamos activos : 1
==========================
Libro devuelto: Clean Code
=== REPORTE BIBLIOTECA ===
Libros registrados : 2
Libros disponibles : 2
Socios registrados : 1
Prestamos activos : 0
==========================
```

## Commits requeridos

1. `feat: implementar GestorBiblioteca como God Object (version inicial)`
2. `feat: agregar clases de dominio Libro y Socio`
3. `refactor: dividir GestorBiblioteca en CatalogoLibros, RegistroSocios, ServicioPrestamos y GeneradorReportes`

## Checkpoints cumplidos

- Proyecto compila sin errores con `mvn compile`.
- `GestorBiblioteca` original esta presente en el repositorio.
- Existen 4 clases especializadas.
- Existen 2 clases de dominio sin uso de `String[]`.
- Dependencias inyectadas por constructor en `ServicioPrestamos` y `GeneradorReportes`.
- `Main` ejecuta el mismo flujo funcional del caso de uso original.
- Se realizaron los 3 commits descriptivos solicitados.
