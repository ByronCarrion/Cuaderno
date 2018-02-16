ejemplos_javascript_curso_

```javascript
console.log("El area de un triangulo de base 5 y altura 7 es: " + 5 * 7 / 2)
console.log(`El area de un triangulo de base 5 y altura 7 es: ${5 *7 / 2}`)
```


```javascript
// CALCULAR LABASE DE UN TRIANGULO
let base = 5
let height = 7
console.log(`El area de un triangulo de base ${base} y ${height}  es: ${base * height / 2}`)
```

```javascript
// CALCULAR LABASE DE UN TRIANGULO
    let base = 5
    let height = 7
    function triangleArea(base, height){
        return base * height / 2
    }

    console.log(`El area de un triangulo de base ${base} y ${height}  es: ${triangleArea(base, height)}`)
```


```javascript
// CALCULAR LABASE DE UN TRIANGULO
let base = 5
let height = 7
let triangleArea = (base, height) => base * height / 2


console.log(`El area de un triangulo de base ${base} y ${height}  es: ${triangleArea(base, height)}`)
```


```javascript
// CALCULAR LABASE DE UN TRIANGULO
let base = 5
let height = 7
const triangleArea = (base, height) => { //ARROW FUNTIONS
    //COMENTARIO
    return base * height / 2
}

console.log(`El area de un triangulo de base ${base} y ${height}  es: ${triangleArea(base, height)}`)
```


```javascript
// RESTRICCION POR EDAD
const startWars7 = 'Start Wars: El despertar de la fuerza'
const pgStartWars7 = 13

const nameSacha = 'Sacha'
const ageSacha = 26

const nameSantiago = 'Santiago'
const ageSantiago = 12

function canWatchStartWars7(name, age, isWhitAdult = false){
    if (age >= pgStartWars7 ){
        alert(`${name} puede pasar a ver ${startWars7} `)
    } else if (isWhitAdult) {
        alert(` ${name} puede pasar a ver ${startWars7}.
         Aunque su edad es ${age}, se cuentra acompañad@ por un adulto `)
    } else {
        alert(` ${name} no puede pasar a ver ${startWars7}.
        tiene ${age} años y necesita tener ${pgStartWars7} `)
    }
}

canWatchStartWars7(nameSacha, ageSacha)
canWatchStartWars7(nameSantiago, ageSantiago, true)
```

```javascript
// RESTRICCION POR EDAD
const startWars7 = 'Start Wars: El despertar de la fuerza',
    pgStartWars7 = 13,
    nameSacha = 'Sacha',
    ageSacha = 26,
    nameSantiago = 'Santiago';
let ageSantiago = 12

const canWatchStartWars7 = (name, age, isWhitAdult = false) => {
    if (age >= pgStartWars7 ){
        alert(`${name} puede pasar a ver ${startWars7} `)
    } else if (isWhitAdult) {
        alert(` ${name} puede pasar a ver ${startWars7}.
         Aunque su edad es ${age}, se cuentra acompañad@ por un adulto `)
    } else {
        alert(` ${name} no puede pasar a ver ${startWars7}.
        tiene ${age} años y necesita tener ${pgStartWars7} `)
    }
}

canWatchStartWars7(nameSacha, ageSacha)
canWatchStartWars7(nameSantiago, ageSantiago, true)
```


```javascript
// MANEJO DE STRINGS
function platzom(str) {
    let translation = str

    //SI LA PALABRA ORIGINAL ES UN PALINDROMO
    //NINGUNA ANTERIOR CUENTA Y SE DEVUELBE LA MISMA PALABRA
    //INTERCALANDO MAYUSCULAS Y MINUSCULAS
    const reverse = (str) => str.split('').reverse().join('')

    function minMay(str){
        const length = str.length
        let translation = ''
        let capitalize = true
        for (let i = 0; i < length; i++) {
            const char = str.charAt(i)
            translation += capitalize ? char.toUpperCase() : char.toLowerCase()
            capitalize = !capitalize
        }
        return translation
    }

    if (str == reverse(str)) {
        return minMay(str)
    }

    // SI LA PALABRA TERMINA CON ar SE LE ELIMINAN 
    if (str.toLowerCase().endsWith('ar')) { //1ro CONVIERTE A MINUSCULAS, DESPUES VERIFICA QUE TERMINE CON ar
        translation = str.slice(0, -2) //SE LE QUITA LAS LETRAS ar
    }
    
    // SI LA PALABRA INICIA CON Z SE LE AÑADE AL FINAL 'pe'
    if (str.toLowerCase().startsWith('z')) {
        translation += 'pe'
    }
    
    // SI LA PALABRA TRADUCIDA TIENE MAS DE 10 LETRAS SE PARTE A LA MITAD Y SE UNE CON
    // UN GUION
    const length = translation.length
    if ( length >= 10) {
        const firtsHalf = translation.slice(0, Math.round(length / 2))
        const secondHalf = translation.slice(Math.round(length / 2))
        translation = `${firtsHalf}-${secondHalf}`
    }

    return translation
}
console.log(platzom("Programar")) // Program
console.log(platzom("Zorro")) // Zorrope
console.log(platzom("Zarpar")) // Zarpe
console.log(platzom("abecedario")) //abece-dario
console.log(platzom("sometemos")) //SoMeTeMoS
```

```javascript
// PROMEDIO CORRIDO POR SEMANA
// math.floor//rendondea hacia abajo 3.9 = 3
// math.ceil//redondea para arriba 3.1 = 4
// math.round// redondea dependiendo 3.1 = 3, 3.5 = 4

const nombre = 'rodolfo'
const dias = [
    'lunes',
    'martes',
    'miercoles',
    'jueeves',
    'viernes',
    'sabado',
    'domingo',
]

function correr(){
    const min = 5
    const max = 15
    return Math.round(Math.random() * (max - min)) + min
}

let totalKms = 0
for (let i = 0; i < dias.length; i++) {
    const kms = correr()
    totalKms += kms
    console.log(`El día ${dias[i]} ${nombre} corrio  ${kms} kms `)
}

const promedioKms = totalKms/dias.length
console.log(` En promedio ${nombre} corrio ${promedioKms.toFixed(2)} kms `)
```

```javascript
//CALCULAR GOLPES ENTRE GOKU SV SUPERMAN Y CALCULAR QUIEN GANA
let vidaGoku = 100;
let vidaSuperman = 100;

const min_power = 5;
const max_power = 12;

const ambosSiguenVivos = () => vidaGoku > 0 && vidaSuperman > 0;
const calcularGolpe = () => Math.round(Math.random() * (max_power - min_power) + min_power);
const gokuSigueVivo = () => vidaGoku > 0

let round = 0;

while(ambosSiguenVivos())
{
  round++
  console.log(`Round: ${round}`)

  const golpeGoku = calcularGolpe();
  const golpeSuperman = calcularGolpe();

  if (golpeGoku > golpeSuperman)
  {
    console.log(`Goku ataca a Superman con un golpe de ${golpeGoku}`);
    vidaSuperman -= golpeGoku;
    console.log(`Superman queda en ${vidaSuperman} puntos de vida`);
  }
  else
  {
    console.log(`Superman ataca a Goku con un golpe de ${golpeSuperman}`);
    vidaGoku -= golpeSuperman;
    console.log(`Goku queda en ${vidaGoku} puntos de vida`);
  }
}

if(gokuSigueVivo())
    {
        console.log(`Goku gano la pelea. su vida es de: ${vidaGoku}`);
    } else {
        console.log(`Superman gano la pelea. su vida es de: ${vidaSuperman}`);
    }

```

```javascript
// CALCULAR LA FECHA DE NACIMIENTO
> const nacimiento = new Date(1979, 10, 16)
> nacimiento
< Fri Nov 16 1979 00:00:00 GMT-0600 (CST)
> const hoy = new Date()
> hoy
< Sat Feb 10 2018 14:55:32 GMT-0600 (CST)
> const tiempo = hoy -nacimiento
> tiempo
< 1206716132069
> const tiempoSegundos = tiempo/1000
> tiempoSegundos
< 1206716132.069
> const tiempoMin = tiempoSegundos/60
> tiempoMin
< 20111935.534483332
> const tiempoHoras = tiempoMin/60
> tiempoHoras
< 335198.9255747222
> const proximo = new Date(hoy.getFullYear(),nacimiento.getMonth(),nacimiento.getDate())
> proximo
< Fri Nov 16 2018 00:00:00 GMT-0600 (CST)
> const diasSemana1 = [
    "Domingo",
    "Lunes",
    "Martes",
    "Miercoles",
    "Jueves",
    "Viernes",
    "Sabado",
 ]
> console.log(diasSemana1[proximo.getDay()])
  Viernes
```
```javascript
// CALCULAR LA FECHA DE NACIMIENTO
let hoy = new Date();
let diasSemana = ['Lunes','Martes','Miercoles','Jueves','Viernes','Sabado','Domingo']
const MESES = ['','Enero','Febrero','Marzo','Abril','Mayo','Junio','Julio','Agosto','Septiembre','Octubre','Noviembre', 'Diciembre',]

console.log(`Operacion realizada el dia ${hoy.getDate()} de 
            ${MESES[hoy.getMonth()]} de ${hoy.getFullYear()}`);

// Operacion realizada el dia 11 de Enero de 2018

const nacimiento = new Date(1979, 11, 16);

console.log(`Fecha de nacimiento: Dia ${nacimiento.getDate()} 
            del mes ${MESES[nacimiento.getMonth()]} del año ${nacimiento.getFullYear()}`);

// Fecha de nacimiento: Dia 16 del mes Noviembre del año 1979

const tiempo = hoy.getTime() - nacimiento.getTime();
console.log(`Tiempo ->: ${tiempo}`);

const tiempoDias = tiempo/1000/60/60/24;
console.log(`Tiempo en dias -> ${tiempoDias} `);

const tiempoAnos = Math.floor(tiempoDias/365);
console.log(`tiempoAnos -> ${tiempoAnos}`);

const tiempoMeses = Math.floor((tiempoDias - (tiempoAnos * 365)) /31);
console.log(`tiempoMeses -> ${tiempoMeses}`);

const dias = Math.floor(tiempoDias - (tiempoAnos * 365) - (tiempoMeses * 31));
console.log(`dias -> ${dias}`);

console.log(`Han pasado ${tiempoDias} años ${tiempoMeses} meses dias ${dias} desde mi nacimiento`)
// Han pasado 13937.549797256945 años 2 meses dias 5 desde mi nacimiento

```

```javascript
// DISTANCIA ENTRE DOS PUNTOS
const p1 = {
    x: 0,
    y: 4
}

const p2 = {
    x: 3,
    y: 0
}

function distancia(p1, p2){
    const x = p1.x - p2.x
    const y = p1.y - p2.y
    
    return Math.sqrt(x * x + y * y)
}

console.log(distancia(p1,p2))
// console.log(distancia(p1,x: 20, y: -7))

```

```javascript
// DISTANCIA ENTRE DOS PUNTOS

const p1 = {
    x: 0,
    y: 4,
    moverEnX(x){ // HACE LA MISMA FUNCIONQUE PARA P2
        this.x += x
    },
    moverEnX(y){ // HACE LA MISMA FUNCIONQUE PARA P2
        this.y += y
    }
}

const p2 = {
    x: 3,
    y: 0,
    moverEnX: function (x) { this.x += x }, // SE HACE REFERENCIA AL VALOR DE x QUE VALE 3
    moverEnY: function (y) { this.y += y }, // SE HACE REFERENCIA AL VALOR DE Y QUE VALE 0
}

function distancia(p1, p2){
    const x = p1.x - p2.x
    const y = p1.y - p2.y
    
    return Math.sqrt(x * x + y * y).toFixed(2)
}
// PARA MOVER CUALQUIERA DE LOS PUNTOS -> `p2.moverEnX(3)`
console.log(distancia(p1,p2))
```

```javascript
// DEFINIR LA CLASE/PROTOTIPO "Punto"

function Punto(x, y){ //PROPOTIPO
    this.x = x // CONSTRUCTOR
    this.y = y
}

// SE AGREGAN METODOS AL PROTOTIPO
Punto.prototype.moverEnX = function moverEnX (x){
    this.x += x
}

Punto.prototype.moverEnY = function moverEnY (y){
    this.y += y
}

Punto.prototype.distancia = function distancia(p){
    const x = this.x - p.x
    const y = this.y - p.y

    return Math.sqrt(x * x + y * y).toFixed(2)
}


const p1 = new Punto(0, 4) // SE CREA UN NUEVO OBJETO
const p2 = new Punto(3, 0) // SE CREA UN NUEVO OBJETO

console.log(p1.distancia(p2))
console.log(p2.distancia(p1))
p1.moverEnX(10)
console.log(p1.distancia(p2))
p2.moverEnY(-4)
console.log(p1.distancia(p2))
```

```javascript
// function Punto(x, y){ //PROPOTIPO
//     this.x = x // CONSTRUCTOR
//     this.y = y
// }
// 
// // SE AGREGAN METODOS AL PROTOTIPO
// Punto.prototype.moverEnX = function moverEnX (x){
//     this.x += x
// }
// 
// Punto.prototype.moverEnY = function moverEnY (y){
//     this.y += y
// }
// 
// Punto.prototype.distancia = function distancia(p){
//     const x = this.x - p.x
//     const y = this.y - p.y
// 
//     return Math.sqrt(x * x + y * y).toFixed(2)
// }

// DEFINIR LA CLASE/PROTOTIPO "Punto" - Object.create
const Punto = {
    init: function(x, y){
        this.x = x
        this.y = y

    },
    moverEnX: function moverEnX(x){
        this.x += x
    },
    moverEnY: function moverEnY(y){
        this.y += y
    },
    distancia: function distancia(p){
        const x = this.x - p.x
        const y = this.y - p.y

        return Math.sqrt(x * x + y * y).toFixed(2)
    }

}

const p1 = Object.create(Punto)
const p2 = Object.create(Punto)
p1.init(0, 4)
p2.init(3, 0)

console.log(p1.distancia(p2))
console.log(p2.distancia(p1))
p1.moverEnX(10)
console.log(p1.distancia(p2))
p2.moverEnY(-4)
console.log(p1.distancia(p2))
```

```javascript
// DEFINIR LA CLASE/PROTOTIPO "Punto" - Class de Javascript
class Punto{ // SE CREA UN NUEVO OBJETO DE TIPO PUNTO
    constructor(x, y){ // DICE QUE ES CLASE PERO FUNCIONA COMO PROTOTIPO
        this.x = x
        this.y = y
    }

    moverEnX (x) { // METODOS NO ES NECESARIO EL KEYWORD "function"
        this.x += x
    }

    moverEnY (y) {
        this.y += y
    }

    distancia(p) {
        const x = this.x - p.x
        const y = this.y - p.y

        return Math.sqrt(x * x + y * y).toFixed(2)
    }
}

const p1 = new Punto(0, 4) // SE CREA UN NUEVO OBJETO
const p2 = new Punto(3, 0) // SE CREA UN NUEVO OBJETO

console.log(p1.distancia(p2))
console.log(p2.distancia(p1))
p1.moverEnX(10)
console.log(p1.distancia(p2))
p2.moverEnY(-4)
console.log(p1.distancia(p2))

```

```javascript

var nombre = "Sacha"

function saludar10() {
  var nombre
  if (true) {
     nombre = "Eric"
  }
  
  console.log(`Hola ${nombre}`)
}

saludar("Sacha")
console.log(`La variable nombre tiene el valor ${nombre}`)


function saludarASacha10() {
  const nombre = "Sacha"

  for (let i = 0; i < 10; i++) {
    console.log(`Hola ${nombre}`)
  }
}

saludarASacha10()

```

```javascript
// OPERACIONES CON METODOS DE ARRAYS

function suma(...numeros) {
  return numeros.reduce(function (acum, numero) {
    acum += numero
    return acum
  }, 0) // <- ES EL VALOR INICIAL DEL ACOMULADOR
}

const dobles = (...numeros) => numeros.map(numero => numero * 2)

const pares = (...numeros) => numeros.filter(numero => numero % 2 == 0)

```
- [reduce](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/reduce)
- [push](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/push)
- [reduce](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/map)
- [filter](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/filter)


```javascript
// CLOSURES JAVASCRIPT
function saludarFamilia(apellido) {
  return function saludarMiembroDeFamilia(nombre) {
    console.log(`Hola ${nombre} ${apellido}`)
  }
}

const saludarGomez = saludarFamilia("Gomez")
const saludarPerez = saludarFamilia("Perez")
const saludarRomero = saludarFamilia("Romero")

saludarGomez("Pedro")
saludarGomez("Juan")
saludarGomez("Laura")
saludarGomez("Mónica")

saludarPerez("Dario")
saludarPerez("Martin")
saludarPerez("Julieta")

saludarRomero("Jorge")

```

```javascript
// CLOSURES JAVASCRIPT EJEMPLO 2
function makePrefixer(antes) {
  return function palabra(palabra) {
    console.log(`${antes}${palabra}`)
  }
}

const prefijoRe = makePrefixer("re")

makePrefixer("bueno")

// rebueno
```

## Estructura del lenguaje Js

![](img/js_01.jpg "Estructura del lenguaje JavaScript")
![](img/js_02.jpg "Estructura del lenguaje JavaScript")
![](img/js_03.jpg "Estructura del lenguaje JavaScript")
![](img/js_04.jpg "Estructura del lenguaje JavaScript")
![](img/js_05.jpg "Estructura del lenguaje JavaScript")
![](img/js_06.jpg "Estructura del lenguaje JavaScript")
![](img/js_07.jpg "Estructura del lenguaje JavaScript")


























