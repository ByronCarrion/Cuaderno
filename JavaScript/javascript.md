ejemplos_javascript_curso_

```javascript
console.log("El area de un triangulo de base 5 y altura 7 es: " + 5 * 7 / 2)
console.log(`El area de un triangulo de base 5 y altura 7 es: ${5 *7 / 2}`)
```


```javascript
let base = 5
let height = 7
console.log(`El area de un triangulo de base ${base} y ${height}  es: ${base * height / 2}`)
```

```javascript
    let base = 5
    let height = 7
    function triangleArea(base, height){
        return base * height / 2
    }

    console.log(`El area de un triangulo de base ${base} y ${height}  es: ${triangleArea(base, height)}`)
```


```javascript
let base = 5
let height = 7
let triangleArea = (base, height) => base * height / 2


console.log(`El area de un triangulo de base ${base} y ${height}  es: ${triangleArea(base, height)}`)
```


```javascript
let base = 5
let height = 7
const triangleArea = (base, height) => { //ARROW FUNTIONS
    //COMENTARIO
    return base * height / 2
}

console.log(`El area de un triangulo de base ${base} y ${height}  es: ${triangleArea(base, height)}`)
```


```javascript
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
const p1 = {
    x: 0,
    y: 4,
    moverEnX: function (x) { this.x += x }, // SE HACE REFERENCIA AL VALOR DE x QUE VALE 0
    moverEnY: function (y) { this.y += y }, // SE HACE REFERENCIA AL VALOR DE Y QUE VALE 4
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

console.log(distancia(p1,p2))
```

```javascript
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
class Punto{ // SE CREA UN NUEVO OBJETO DE TIPO PUNTO
    constructor(x, y){ // DICE QUE ES CLASE PERO FUNCIONA COMO PROTOTIPO
        this.x = x
        this.y = y
    }

    moverEnX (x) {
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



































