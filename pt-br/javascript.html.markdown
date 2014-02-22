---
language: javascript
contributors:
    - ["Adam Brenecki", "http://adam.brenecki.id.au"]
filename: javascript.js
---

JavaScript was created by Netscape's Brendan Eich in 1995. It was originally
intended as a simpler scripting language for websites, complimenting the use of
Java for more complex web applications, but its tight integration with Web pages
and built-in support in browsers has caused it to become far more common than
Java in web frontends.

JavaScript isn't just limited to web browsers, though: Node.js, a project that
provides a standalone runtime for Google Chrome's V8 JavaScript engine, is
becoming more and more popular.

Feedback would be highly appreciated! You can reach me at
[@adambrenecki](https://twitter.com/adambrenecki), or
[adam@brenecki.id.au](mailto:adam@brenecki.id.au).

```js
// Comentários são como em C. Os de linha única começam com duas barras
/* e os comentários multilinha começam com barra-asterisco 
   e terminam com asterisco-barra */

// Comandos podem terminar com ;
facaAlgo();

// ... mas eles não precisam, uma vez que ponto e vírgula são inseridos
// aonde quer que haja uma nova linha, a não ser em casos específicos.
facaAlgo()

// Em alguns casos, resultados inesperados podem ser causados, por isso
// nós usaremos ponto e vírgula neste guia.

///////////////////////////////////
// 1. Números, Strings e Operadores

// JavaScript tem um tipo número (que é um double de 64-bit IEEE 754).
// Assim como Lua, não se preocupe com a capacidade de inteiros: doubles 
// tem 52-bit matemáticos, que é o suficiente para armazenar inteiros
// até cerca de 9✕10¹⁵ precisamente.
3; // = 3
1.5; // = 1.5

// Toda a aritmética básica funciona como você pode esperar.
1 + 1; // = 2
8 - 1; // = 7
10 * 2; // = 20
35 / 5; // = 7

// Incluíndo divisão irregular.
5 / 2; // = 2.5

// Lógica binária também funciona; quando você realiza uma operação de lógica
// binária, seu flaot é convertido para um signed int *até* 32 bits.
1 << 2; // = 4

// Precedência é definida com parênteses
(1 + 3) * 2; // = 8

// Há três valores especiais de números não-reais:
Infinity; // resultado de, por exemplo: 1/0
-Infinity; // resultado de, por exemplo: -1/0
NaN; // resultado de, por exemplo: 0/0

// Também há o tipo booleano.
true;
false;

// Strings são criadas com ' ou ".
'abc';
"Olá, mundo!";

// Negação usa o símbolo !
!true; // = false
!false; // = true

// Igualdade é ==
1 == 1; // = true
2 == 1; // = false

// Desigualdade é !=
1 != 1; // = false
2 != 1; // = true

// Mais comparações
1 < 10; // = true
1 > 10; // = false
2 <= 2; // = true
2 >= 2; // = true

// Strings são concatenadas com +
"Hello " + "world!"; // = "Hello world!"

// e comparadas com < e >
"a" < "b"; // = true

// Coerção(conversão de tipos) é realizada para comparações...
"5" == 5; // = true

// ...a não ser que você use ===
"5" === 5; // = false

// Você também pode acessar caracteres de uma String com charAt
"Isto é uma String".charAt(0);

// Também há null e undefined
null; // usado para indicar que algo não tem valor
undefined; // usado para indicar que um valor não está presente (todavia,
           // o próprio undefined é um valor)

// false, null, undefined, NaN, 0 e "" são false; todo o resto é true.
// Note que 0 é false e "0" is true, no entanto 0 == "0".

///////////////////////////////////
// 2. Variáveis, Arrays e Objetos.

// Variáveis são declaradas com a palavra chave var. JavaScript é dinamicamente tipada,
// então você não precisa especificar o tipo. Atribuição usa o caractere = apenas.
var algumaVariavel = 5;

// se você não usar a palavra chave var, isto não causará um erro...
someOtherVar = 10;

// ...mas sua variável será criada no escopo global, não no escopo que
// você a definiu.

// Variáveis declaradas sem atribuição de valor, tem seu valor definido como undefined.
var algumaVariavelQualquer; // = undefined

// Há atalhos para realizar operações matemáticas em variáveis:
algumaVariavel += 5; // equivalente a algumaVariavel = algumaVariavel + 5; algumaVariavel agora é 10
algumaVariavel *= 10; // now algumaVariavel é 100

// e também atalho para incrementar ou decrementar
algumaVariavel++; // agora algumaVariavel é 101
algumaVariavel--; // agora para 100

// Arrays são listas ordenadas de valores, de quaisquer tipos.
var meuArray = ["Olá", 45, true];

// Seus membros podem ser acessados usando a sintaxe com colchetes.
// Índices de Arrays começam no zero .
meuArray[1]; // = 45

// Arrays são flexíveis quanto a mudanças de tamanho.
meuArray.push("Mundo");
meuArray.length; // = 4

// Objetos JavaScript são equivalentes a 'dicionários' ou 'mapas' em outras
// linguagens: uma coleção de pares ordendados de chave-valor.
var meuObjeto = {chave1: "Olá", chave2: "Mundo"};

// Chaves são Strings, mas aspas não são necessárias se elas forem um
// identificador JavaScript válido. Valores podem ser de qualquer tipo.
var meuObjeto = {minhaChave: "meuValor", "minha outra chave": 4};

// Atributos de objetos também podem ser acessados usando a chave como índice,
meuObjeto["minha outra chave"]; // = 4

// ... ou usando a sintaxe com ponto, desde que a chave seja um identificador válido.
meuObjeto.minhaChave; // = "meuValor"

// Objetos são mutáveis; valores podem ser alterados e novas chaves adicionadas.
meuObjeto.minhaNovaChave = true;

// Se você tentar acessar um valor que não foi definido, receberá undefined.
meuObjeto.minhaChaveQueNaoExiste; // = undefined

///////////////////////////////////
// 3. Estruturas Lógicas e de Controle

// A estrutura if funciona como você já deve esperar.
var contador = 1;
if (contador == 3){
    // executado se contador é 3
} else if (contador == 4){
    // executado se contador é 4
} else {
    // executado se contador não for 3 nem 4...
}

// Bem como o while.
while (true){
    // Um loop infinito!
}

// Loops Do-while são como os loops while, exceto por serem executados antes
// de testar a condição.
var entrada
do {
    entrada = getEntrada();
} while (!isValid(entrada))

// o loop for é o mesmo que em C e Java:
// inicialização; condição de continuidade; iteração.
for (var i = 0; i < 5; i++){
    // rodará 5 vezes
}

// && é o AND lógico, || é o OR lógico
if (casa.tamanho == "grande" && casa.cor == "azul"){
    casa.contem = "urso";
}
if (cor == "vermelho" || cor == "azul"){
    // cor é vermelho ou azul
}

// && e || podem ser usados em um "short circuit", que é útil para atribuição de valores.
var nome = outroNome || "valorPadrão";

///////////////////////////////////
// 4. Functions, Scope and Closures

// JavaScript functions are declared with the function keyword.
function myFunction(thing){
    return thing.toUpperCase();
}
myFunction("foo"); // = "FOO"

// Note that the value to be returned must start on the same line as the
// 'return' keyword, otherwise you'll always return 'undefined' due to
// automatic semicolon insertion. Watch out for this when using Allman style.
function myFunction()
{
    return // <- semicolon automatically inserted here
    {
        thisIsAn: 'object literal'
    }
}
myFunction(); // = undefined

// JavaScript functions are first class objects, so they can be reassigned to
// different variable names and passed to other functions as arguments - for
// example, when supplying an event handler:
function myFunction(){
    // this code will be called in 5 seconds' time
}
setTimeout(myFunction, 5000);
// Note: setTimeout isn't part of the JS language, but is provided by browsers
// and Node.js.

// Function objects don't even have to be declared with a name - you can write
// an anonymous function definition directly into the arguments of another.
setTimeout(function(){
    // this code will be called in 5 seconds' time
}, 5000);

// JavaScript has function scope; functions get their own scope but other blocks
// do not.
if (true){
    var i = 5;
}
i; // = 5 - not undefined as you'd expect in a block-scoped language

// This has led to a common pattern of "immediately-executing anonymous
// functions", which prevent temporary variables from leaking into the global
// scope.
(function(){
    var temporary = 5;
    // We can access the global scope by assiging to the 'global object', which
    // in a web browser is always 'window'. The global object may have a
    // different name in non-browser environments such as Node.js.
    window.permanent = 10;
})();
temporary; // raises ReferenceError
permanent; // = 10

// One of JavaScript's most powerful features is closures. If a function is
// defined inside another function, the inner function has access to all the
// outer function's variables, even after the outer function exits.
function sayHelloInFiveSeconds(name){
    var prompt = "Hello, " + name + "!";
    // Inner functions are put in the local scope by default, as if they were
    // declared with 'var'.
    function inner(){
        alert(prompt);
    }
    setTimeout(inner, 5000);
    // setTimeout is asynchronous, so the sayHelloInFiveSeconds function will
    // exit immediately, and setTimeout will call inner afterwards. However,
    // because inner is "closed over" sayHelloInFiveSeconds, inner still has
    // access to the 'prompt' variable when it is finally called.
}
sayHelloInFiveSeconds("Adam"); // will open a popup with "Hello, Adam!" in 5s

///////////////////////////////////
// 5. More about Objects; Constructors and Prototypes

// Objects can contain functions.
var myObj = {
    myFunc: function(){
        return "Hello world!";
    }
};
myObj.myFunc(); // = "Hello world!"

// When functions attached to an object are called, they can access the object
// they're attached to using the this keyword.
myObj = {
    myString: "Hello world!",
    myFunc: function(){
        return this.myString;
    }
};
myObj.myFunc(); // = "Hello world!"

// What this is set to has to do with how the function is called, not where
// it's defined. So, our function doesn't work if it isn't called in the
// context of the object.
var myFunc = myObj.myFunc;
myFunc(); // = undefined

// Inversely, a function can be assigned to the object and gain access to it
// through this, even if it wasn't attached when it was defined.
var myOtherFunc = function(){
    return this.myString.toUpperCase();
}
myObj.myOtherFunc = myOtherFunc;
myObj.myOtherFunc(); // = "HELLO WORLD!"

// We can also specify a context for a function to execute in when we invoke it
// using 'call' or 'apply'.

var anotherFunc = function(s){
    return this.myString + s;
}
anotherFunc.call(myObj, " And Hello Moon!"); // = "Hello World! And Hello Moon!"

// The 'apply' function is nearly identical, but takes an array for an argument list.

anotherFunc.apply(myObj, [" And Hello Sun!"]); // = "Hello World! And Hello Sun!"

// This is useful when working with a function that accepts a sequence of arguments
// and you want to pass an array.

Math.min(42, 6, 27); // = 6
Math.min([42, 6, 27]); // = NaN (uh-oh!)
Math.min.apply(Math, [42, 6, 27]); // = 6

// But, 'call' and 'apply' are only temporary. When we want it to stick, we can use
// bind.

var boundFunc = anotherFunc.bind(myObj);
boundFunc(" And Hello Saturn!"); // = "Hello World! And Hello Saturn!"

// Bind can also be used to partially apply (curry) a function.

var product = function(a, b){ return a * b; }
var doubler = product.bind(this, 2);
doubler(8); // = 16

// When you call a function with the new keyword, a new object is created, and
// made available to the function via the this keyword. Functions designed to be
// called like that are called constructors.

var MyConstructor = function(){
    this.myNumber = 5;
}
myNewObj = new MyConstructor(); // = {myNumber: 5}
myNewObj.myNumber; // = 5

// Every JavaScript object has a 'prototype'. When you go to access a property
// on an object that doesn't exist on the actual object, the interpreter will
// look at its prototype.

// Some JS implementations let you access an object's prototype on the magic
// property __proto__. While this is useful for explaining prototypes it's not
// part of the standard; we'll get to standard ways of using prototypes later.
var myObj = {
    myString: "Hello world!"
};
var myPrototype = {
    meaningOfLife: 42,
    myFunc: function(){
        return this.myString.toLowerCase()
    }
};

myObj.__proto__ = myPrototype;
myObj.meaningOfLife; // = 42

// This works for functions, too.
myObj.myFunc(); // = "hello world!"

// Of course, if your property isn't on your prototype, the prototype's
// prototype is searched, and so on.
myPrototype.__proto__ = {
    myBoolean: true
};
myObj.myBoolean; // = true

// There's no copying involved here; each object stores a reference to its
// prototype. This means we can alter the prototype and our changes will be
// reflected everywhere.
myPrototype.meaningOfLife = 43;
myObj.meaningOfLife; // = 43

// We mentioned that __proto__ was non-standard, and there's no standard way to
// change the prototype of an existing object. However, there are two ways to
// create a new object with a given prototype.

// The first is Object.create, which is a recent addition to JS, and therefore
// not available in all implementations yet.
var myObj = Object.create(myPrototype);
myObj.meaningOfLife; // = 43

// The second way, which works anywhere, has to do with constructors.
// Constructors have a property called prototype. This is *not* the prototype of
// the constructor function itself; instead, it's the prototype that new objects
// are given when they're created with that constructor and the new keyword.
MyConstructor.prototype = {
    myNumber: 5,
    getMyNumber: function(){
        return this.myNumber;
    }
};
var myNewObj2 = new MyConstructor();
myNewObj2.getMyNumber(); // = 5
myNewObj2.myNumber = 6
myNewObj2.getMyNumber(); // = 6

// Built-in types like strings and numbers also have constructors that create
// equivalent wrapper objects.
var myNumber = 12;
var myNumberObj = new Number(12);
myNumber == myNumberObj; // = true

// Except, they aren't exactly equivalent.
typeof(myNumber); // = 'number'
typeof(myNumberObj); // = 'object'
myNumber === myNumberObj; // = false
if (0){
    // This code won't execute, because 0 is falsy.
}
if (Number(0)){
    // This code *will* execute, because Number(0) is truthy.
}

// However, the wrapper objects and the regular builtins share a prototype, so
// you can actually add functionality to a string, for instance.
String.prototype.firstCharacter = function(){
    return this.charAt(0);
}
"abc".firstCharacter(); // = "a"

// This fact is often used in "polyfilling", which is implementing newer
// features of JavaScript in an older subset of JavaScript, so that they can be
// used in older environments such as outdated browsers.

// For instance, we mentioned that Object.create isn't yet available in all
// implementations, but we can still use it with this polyfill:
if (Object.create === undefined){ // don't overwrite it if it exists
    Object.create = function(proto){
        // make a temporary constructor with the right prototype
        var Constructor = function(){};
        Constructor.prototype = proto;
        // then use it to create a new, appropriately-prototyped object
        return new Constructor();
    }
}
```

## Further Reading

The [Mozilla Developer
Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript) provides
excellent documentation for JavaScript as it's used in browsers. Plus, it's a
wiki, so as you learn more you can help others out by sharing your own
knowledge.

MDN's [A re-introduction to
JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
covers much of the concepts covered here in more detail. This guide has quite
deliberately only covered the JavaScript language itself; if you want to learn
more about how to use JavaScript in web pages, start by learning about the
[Document Object
Model](https://developer.mozilla.org/en-US/docs/Using_the_W3C_DOM_Level_1_Core)

[JavaScript Garden](http://bonsaiden.github.io/JavaScript-Garden/) is an in-depth
guide of all the counter-intuitive parts of the language.

In addition to direct contributors to this article, some content is adapted
from Louie Dinh's Python tutorial on this site, and the [JS
Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
on the Mozilla Developer Network.
