# reyes-post1-u6

## Taller U6 - Refactorizacion de God Object aplicando SRP

Este repositorio contiene el laboratorio en la carpeta [refactoring-lab](refactoring-lab/).

## Antipatron identificado

Se identifico el antipatron **God Object** en la clase `GestorBiblioteca`, ya que concentraba multiples responsabilidades en una sola clase.

## 4 responsabilidades encontradas

1. Gestion del catalogo de libros (agregar, buscar, listar).
2. Gestion de socios (registrar, validar, buscar).
3. Gestion de prestamos (prestar, devolver).
4. Generacion de reportes del sistema.

## Patron aplicado

Se aplico **SRP (Single Responsibility Principle)** separando responsabilidades en clases especializadas:

- `CatalogoLibros`
- `RegistroSocios`
- `ServicioPrestamos`
- `GeneradorReportes`

Clases de dominio:

- `Libro`
- `Socio`

## Evidencias de ejecucion

- Antes de refactorizar: [refactoring-lab/docs/evidencias/salida-antes.txt](refactoring-lab/docs/evidencias/salida-antes.txt)
- Despues de refactorizar: [refactoring-lab/docs/evidencias/salida-despues.txt](refactoring-lab/docs/evidencias/salida-despues.txt)

Capturas recomendadas:

- `refactoring-lab/docs/evidencias/captura-antes.png`
- `refactoring-lab/docs/evidencias/captura-despues.png`

Si agregas esas imagenes con esos nombres, puedes mostrarlas asi:

![Captura antes](refactoring-lab/docs/evidencias/captura-antes.png)

![Captura despues](refactoring-lab/docs/evidencias/captura-despues.png)

## Proyecto Maven

Para compilar y ejecutar desde la carpeta del laboratorio:

```bash
cd refactoring-lab
mvn compile
mvn exec:java
```

## README del laboratorio

Tambien puedes ver el README interno en [refactoring-lab/README.md](refactoring-lab/README.md).
