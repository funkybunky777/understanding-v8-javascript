# Hidden Classes

Es la noción interna de tipado de V8, el motor de Javascript con el fin de crear una estructura interna para organizar tus objectos.

#### Qué es una Hidden Class?

Es un **grupo de objectos con la misma estructura**, según vayas agregando propiedades a tus objectos, V8 ira verificando cada objecto y mapeará el manojo de propiedades a una hidden class cual define un objecto exactamente con esas propiedades.

Vamos a ver el siguiente ejemplo donde tenemos dos objetos literales, `a` y `b`.

```javascript
var a = {};
a.x = 8;
a.y = 8;

var b = {};
b.x = 3;
b.y = 9;

print(%HaveSameMap(a,b));
a.z = 1;
print(%HaveSameMap(a,b));
```

El resultado para lo siguiente seria.

```javascript
$> d8 --allow_natives_syntax native_syntax.js 
true
false
```

Como puedes observar, hemos creado dos objetos literales.
