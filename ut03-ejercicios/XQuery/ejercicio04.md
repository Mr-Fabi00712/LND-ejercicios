# Ejercicio 4. Archivo estudiantes.xml

```xml

<estudiantes>
  <estudiante id="1" carrera="Ingeniería">
    <nombre>Juan</nombre>
    <edad>20</edad>
    <nota>8.5</nota>
  </estudiante>
  <estudiante id="2" carrera="Derecho">
    <nombre>María</nombre>
    <edad>22</edad>
    <nota>9.0</nota>
  </estudiante>
  <estudiante id="3" carrera="Medicina">
    <nombre>Pedro</nombre>
    <edad>19</edad>
    <nota>7.5</nota>
  </estudiante>
  <estudiante id="4" carrera="Ingeniería">
    <nombre>Ana</nombre>
    <edad>21</edad>
    <nota>8.8</nota>
  </estudiante>
</estudiantes>
```

__Pregunta 1.__ Devuelve los nombres de los estudiantes.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
return $estudiante/nombre
```

__Pregunta 2.__ Filtra los estudiantes con una nota mayor a 8.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
where xs:decimal($estudiante/nota) > 8
return $estudiante
```

__Pregunta 3.__ Devuelve los nombres y las carreras de los estudiantes.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
return <item>
           <nombre>{$estudiante/nombre}</nombre>
           <carrera>{$estudiante/@carrera}</carrera>
       </item>
```

__Pregunta 4.__ Calcula la nota promedio de los estudiantes (usa let).

```XQuery
let $notas := for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
              return xs:decimal($estudiante/nota)
return sum($notas) div count($notas)
```

__Pregunta 5.__ Devuelve los estudiantes de la carrera "Ingeniería".

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
where $estudiante/@carrera = "Ingeniería"
return $estudiante
```

__Pregunta 6.__ Ordena a los estudiantes por edad.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
let $edad := xs:decimal($estudiante/edad)
return <estudianteOrdenado>
           <nombre>{$estudiante/nombre}</nombre>
           <edad>{$estudiante/edad}</edad>
           <nota>{$estudiante/nota}</nota>
           <carrera>{$estudiante/@carrera}</carrera>
       </estudianteOrdenado>
order by $edad ascending
```

__Pregunta 7.__ Devuelve el estudiante más joven.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
let $edad := xs:decimal($estudiante/edad)
return $estudiante
order by $edad ascending
limit 1
```

__Pregunta 8.__ Devuelve los nombres y las notas incrementadas en 0.5.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
let $notaIncrementada := xs:decimal($estudiante/nota) + 0.5
return <item>
           <nombre>{$estudiante/nombre}</nombre>
           <notaIncrementada>{$notaIncrementada}</notaIncrementada>
       </item>
```

__Pregunta 9.__ Devuelve los estudiantes cuya nota es mayor a 8 y pertenecen a Ingeniería.

```XQuery
for $estudiante in doc("estudiantes.xml")/estudiantes/estudiante
where xs:decimal($estudiante/nota) > 8 and $estudiante/@carrera = "Ingeniería"
return $estudiante
```

__Pregunta 10.__ Cuenta cuántos estudiantes hay en total.

```XQuery
count(doc("estudiantes.xml")/estudiantes/estudiante)
```
