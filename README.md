# EXAMEN PRÁCTICO – BLOQUE 1
## Diseño Relacional y SQL en la Nube

**Asignatura:** Base de Datos en la Nube  
**Tipo de Evaluación:** Examen Práctico  

---

### Contexto del Problema (Caso Práctico)

Una academia de cursos en línea requiere una base de datos para gestionar eficientemente la información de sus estudiantes, la oferta académica de cursos y el registro de inscripciones.

El sistema de base de datos debe satisfacer los siguientes requerimientos funcionales:
1.  **Registrar Estudiantes:** Almacenar datos personales de los alumnos.
2.  **Registrar Cursos:** Gestionar la información de los cursos disponibles.
3.  **Controlar Inscripciones:** Vincular a los estudiantes con los cursos que toman, registrando la fecha de inscripción.
4.  **Consultas Académicas:** Permitir la extracción de información relevante para la toma de decisiones y administración.

---

### Parte A – Diseño del Modelo Relacional (Workbench)

**Herramienta:** MySQL Workbench

**Requisitos del Modelo:**
*   El diseño debe contener un máximo de **4 tablas**.
*   Debe implementar al menos **una relación Uno a Muchos (1:N)**.
*   Debe implementar al menos **una relación Muchos a Muchos (N:M)** (lo que implicará una tabla intermedia).
*   Todas las tablas deben contar con:
    *   **Clave Primaria (PK)** definida.
    *   **Tipos de datos** adecuados para cada atributo.
    *   Definición correcta de **Claves Foráneas (FK)** para mantener la integridad referencial.

**Esquema Sugerido:**

1.  **Tablas Principales:**
    *   `estudiantes`: `id_estudiante` (PK), `nombre`, `correo`, `edad`.
    *   `cursos`: `id_curso` (PK), `nombre`, `duracion_horas`.

2.  **Tabla de Relación:**
    *   `inscripciones`: `id_inscripcion` (PK), `id_estudiante` (FK), `id_curso` (FK), `fecha_inscripcion`.

3.  *(Opcional)* `instructores`: Puede incluirse si se desea, siempre que no se exceda el límite de tablas.

---

### Parte B – Implementación en la Nube

**Plataforma:** Clever Cloud (MySQL)

**Instrucciones:**
1.  **Generación de Script:** Exporte el script SQL DDL (Data Definition Language) desde MySQL Workbench.
2.  **Creación de BD:** Provisione una base de datos MySQL en Clever Cloud.
3.  **Ejecución de Estructura:** Ejecute el script generado para crear las tablas y definir las claves.
4.  **Inserción de Datos (DML):** Desarrolle y ejecute un script SQL para poblar la base de datos con los siguientes datos mínimos:
    *   Al menos **5 estudiantes**.
    *   Al menos **4 cursos**.
    *   Al menos **6 inscripciones**.

---

### Parte C – Consultas SQL (10 Puntos)

Se evaluará la capacidad de extraer información mediante consultas SQL. Cada consulta tiene un valor de **1 punto**.

**Sentencias Requeridas:**
Además de `SELECT`, `FROM`, `WHERE` e `INNER JOIN`, se deberá demostrar el uso de:
*   `COUNT()`
*   `GROUP BY`
*   `ORDER BY`
*   `AVG()`
*   `DISTINCT`

#### Cuestionario de Consultas:

1.  **Lista de contactos:** Liste el nombre y correo de todos los estudiantes registrados.
2.  **Filtro por edad:** Obtenga los estudiantes cuya edad sea mayor a 20 años.
3.  **Cursos extensos:** Muestre el nombre de los cursos con una duración mayor a 30 horas.
4.  **Detalle de inscripciones:** Liste los nombres de los estudiantes junto con los cursos en los que están inscritos.
5.  **Demanda de cursos:** Muestre cuántos estudiantes están inscritos en cada curso.
6.  **Edad promedio:** Obtenga el promedio de edad de los estudiantes.
7.  **Ranking de duración:** Liste los cursos ordenados por duración de mayor a menor.
8.  **Estudiantes específicos:** Muestre los estudiantes inscritos en el curso llamado “Bases de Datos”.
9.  **Cursos activos:** Obtenga los cursos que tienen al menos un estudiante inscrito.
10. **Total de registros:** Muestre la cantidad total de inscripciones registradas en el sistema.

---

### Rúbrica de Evaluación

| Criterio | Puntaje | Detalle |
| :--- | :---: | :--- |
| **Diseño del Modelo (Workbench)** | **5 pts** | Correcta normalización, PKs, FKs y tipos de datos. |
| **Script de Creación (DDL)** | **5 pts** | Ejecución exitosa en Clever Cloud sin errores. |
| **Script de Inserción (DML)** | **5 pts** | Datos de prueba suficientes y consistentes. |
| **Consultas SQL** | **10 pts** | 1 punto por cada consulta correcta y óptima. |
| **TOTAL** | **25 pts** | |

---
---

# EXAMEN PRÁCTICO – BLOQUE 2
## Bases de Datos NoSQL – MongoDB Atlas

---

### Contexto del problema (caso práctico)

Una plataforma de cursos en línea desea almacenar información académica utilizando una base de datos NoSQL, con el fin de manejar estructuras de datos flexibles y escalables.

La plataforma necesita registrar:
1.  **Información de estudiantes**
2.  **Cursos en los que están inscritos**
3.  **Progreso académico y calificaciones**

La base de datos será implementada en MongoDB Atlas y las operaciones se realizarán mediante un Jupyter Notebook.

---

### Parte A – Diseño del modelo NoSQL

**Requisitos del modelo**

Diseñe un modelo de documentos considerando las características de MongoDB:
*   Utilice una sola colección llamada `estudiantes`.
*   Cada documento debe contener:
    *   Información básica del estudiante.
    *   Un arreglo de cursos inscritos.
*   Debe usar:
    *   Documentos anidados.
    *   Arreglos.

**Estructura sugerida del documento:**

```json
{
  "_id": ObjectId(),
  "nombre": "Juan Pérez",
  "correo": "juan@mail.com",
  "edad": 22,
  "cursos": [
    {
      "nombre": "Bases de Datos",
      "duracion_horas": 40,
      "calificacion": 85
    }
  ]
}
```

*Nota: Puede agregar campos adicionales si lo considera necesario.*

---

### Parte B – Implementación en MongoDB Atlas

1.  **Cluster:** Cree un cluster en MongoDB Atlas.
2.  **Base de Datos:** Cree una base de datos llamada `academia`.
3.  **Colección:** Cree la colección `estudiantes`.
4.  **Conexión:** Conéctese a la base de datos utilizando Jupyter Notebook y la librería `pymongo`.
5.  **Inserción:** Inserte al menos:
    *   5 documentos de estudiantes.
    *   Cada estudiante con al menos 1 curso.

---

### Parte C – Consultas NoSQL (10 puntos)

Cada consulta vale **1 punto**. Las consultas deben ejecutarse desde el Jupyter Notebook.

**Operadores y métodos que se evalúan:**
*   `find()`
*   Proyección
*   `$gt`, `$lt`
*   `$and`
*   `$in`
*   `$push`
*   `updateOne()`
*   `deleteOne()`
*   `countDocuments()`

#### Cuestionario de Consultas:

1.  **Todos los registros:** Obtenga todos los estudiantes registrados.
2.  **Proyección:** Muestre únicamente los nombres y correos de los estudiantes.
3.  **Filtro simple:** Obtenga los estudiantes cuya edad sea mayor a 20 años.
4.  **Filtro en arreglos:** Muestre los estudiantes inscritos en el curso “Bases de Datos”.
5.  **Consulta anidada:** Obtenga los estudiantes con calificación mayor o igual a 80 en algún curso.
6.  **Actualización (Push):** Agregue un nuevo curso a un estudiante específico.
7.  **Actualización (Set):** Actualice la calificación de un curso para un estudiante.
8.  **Eliminación:** Elimine un estudiante según su correo electrónico.
9.  **Conteo:** Cuente cuántos estudiantes tienen más de un curso registrado.
10. **Operador IN:** Obtenga los nombres de los estudiantes inscritos en cualquiera de los cursos: “SQL” o “MongoDB”.

---

### Rúbrica de Evaluación

| Criterio | Puntaje |
| :--- | :---: |
| **Diseño del modelo NoSQL** | **5 pts** |
| **Inserción de documentos** | **5 pts** |
| **Consultas MongoDB (10)** | **10 pts** |
| **Uso correcto de Jupyter Notebook** | **5 pts** |
| **Total Bloque 2** | **25 pts** |
