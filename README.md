# WEEDO.it JavaScript Code Style

### Geral
- Aspas simples para strings
- Usar camelCase

### Identação

- Usar 4 espaços

```js

/* Variaveis */

//Not good

var a = 1,
b = 2,
x = 4;

// Good
var a = 1,
    b = 2,
    x = 4;

//Not good
var a = 1, b = 2, x = 4;

// Good
var a = 1,
    b = 2,
    x = 4;


/* Arrays */

//Not good

var a = [
    item1,
    item2,
    item3
];

// Good
var a = [
        item1,
        item2,
        item3
    ];
    
// Mais Good ainda (em caso de arrays pequenos)
var a = [item1, item2, item3];


/* Encadeamento */

//Not good

MinhaClass.metodo1().outroMetodoAi().metodoComArgumentos(1,2,3).metodoComCallCallback(function () {
    // ...
});

MinhaClass.metodo1().outroMetodoAi()
.metodoComArgumentos(1,2,3).metodoComCallCallback(function () {
    // ...
});


//Good

MinhaClass.metodo1()
    .outroMetodoAi()
    .metodoComArgumentos(1,2,3)
    .metodoComCallCallback(function () {
        // ...
    });



/* Callbacks */

// No good
fazAMagica(arg1, function (data) {
    // ..
}, function (err) {
    // ..
});

// Good
fazAMagica(arg1,
    function (data) {
        // ..
    },
    function (err) {
        // ..
    }
);

```

### Espaçamentos

- Deixar um espaço entre o nome da variável e o operador e entre o operador e o valor da variável;
- Na declaração de metodos, deixar um espaço entre o nome do metodo e o parenteses;
- Na declaração de metodos, deixar um espaço entre os argumentos;
- Na declaração de metodos, deixar um espaço entre o parentese que fecha os argumentos e a abertura das chaves;
- Na declaração de loops, espacar os operadores e as variavies e deixar um espaco entre o ponto e virgula e a proxima variavel;
- Em Arrays de uma unica linha, deixar um espaco entre os itens;

```js
/* Declaração de variavies */

// Not good
var a=1;

// Good
var a = 1;


/* Declaração de funções */

// Not good
function minhaFuncaoSupimposa(arg1,arg2){
    // ..
}
// Good
function minhaFuncaoSupimposa (arg1, arg2) {
    // ..
}

/* Declaração de loops */

// Not good
for(x=0;x<len;x+=1){
    // ..
}
// Good
for (x = 0; x < len; x += 1) {
    // ..
}


/* Ternárias */

// Not good
var a=(minhaCondicao)?true:false;

// Good
var a = (minhaCondicao) ? true : false;


/* Arrays */

// Not good
var a = [1,2,4,"string"];

// Good
var a = [1, 2, 4, "string"];


/* Objetos */

// Not good
var a = {a:1,b:2:c:"string"};
var a = {a:1, b:2: c:"string"};

// Good
var a = {a: 1, b: 2, c: "string"};

```

### Declaração de Variáveis

- Agrupar as declarações em um *let* ou *var* só;
- Ao agrupar variavies, deixar as que possuem valor definido no topo e depois as sem valores.
- Declarar as variavies que serão utilizadas dentro do metodo na primeira linha após os chaves;
- Em loops, declarar as variáveis antes de usar;

```js
// Not good
var a=1;
var b=2;

// Good
var a = 1,
    b = 2;
    

// Not good
var listaDeItens,
    meuArrayLindao = [1, 2],
    outraCoisa,
    minhaVariavelComValor = "valor";
    

// Good
var meuArrayLindao = [1, 2],
    minhaVariavelComValor = "valor",
    listaDeItens,
    outraCoisa;
    
    
// Mais Good Ainda
var minhaVariavelComValor = "valor",
    meuArrayLindao = [1, 2],
    listaDeItens,
    outraCoisa;


// Not good
function () {
    if (condicao) {
        var a = 1;
    }
}

// Good
function () {
    var a;
    
    if (condicao) {
        a = 1;
    }
}

// Not good
for (var x=0, len=list.length; x<len; x++) {
    // ...
}

// Good
var len = list.length,
    x;
    
for (x = 0; x < len; x++) {
    // ...
}
```

### Quebra de linhas

Abra chaves na mesma linha da declaracao do metodo ou class
```js

// Not good

class MinhaClasseUltraMegaPower
{
    // ...
}

function funcaozinhaMarota ()
{
    // ...
}

// Good
class MinhaClasseUltraMegaPower {
    // ...
}

function funcaozinhaMarota () {
    // ...
}

```

Evite quebra de linhas em excesso

```js

// Not good

function fazAlgoAi (valor) {
    var a = 1,
        b = 0;
    
    b = calculaRaizQuadrada(a, valor);
    
    b = valor * (a + b);
    
    if (valor > 29) {
    
        a += 35;
        
        a = a * -1 + b;
        
    }
    
    return Math.sin(a);
}


// Good
function fazAlgoAi (valor) {
    var a = 1,
        b = 0;
    
    b = calculaRaizQuadrada(a, valor);
    b = valor * (a + b);
    
    if (valor > 29) {
        a += 35;
        a = a * -1 + b;
    }
    
    return Math.sin(a);
}

```

Deixe uma linha antes e depois de um bloco (if, for, while...) caso nao seja o inicio ou o fim do metodo.
```js

// Not good

function fazAlgoAi (valor) {
    var a = 0;
    if (valor > 29) {
        a += 35;
        a = a * -1 + b;
    }
    return Math.sin(a);
}

function fazAlgoAi (valor) {

    if (valor > 29) {
        fazAquiloLa();
    }

}



// Good
function fazAlgoAi (valor) {
    var a = 0;
    
    if (valor > 29) {
        a += 35;
        a = a * -1 + b;
    }
    
    return Math.sin(a);
}

function fazAlgoAi (valor) {
    if (valor > 29) {
        fazAquiloLa();
    }
}

```

Agrupe o codigo por contexto sempre que possivel.

```js

// Not good

function fazAlgoAi (user) {
    var infos = {};
    
    user.name = 'Fred';
    
    infos.url = 'http://weedo.it';
    
    user.idade = 34;
    
    user.possuiNecessidadesEspeciais = false;
    
    infos.mobile = true;
    
    if (user.id) {
        user.origin = 'system';
    }
    
    return [user, infos];
}


// Good
function fazAlgoAi (user) {
    var infos = {};
    
    infos.url = 'http://weedo.it';
    infos.mobile = true;
    
    user.name = 'Fred';
    user.idade = 34;
    user.possuiNecessidadesEspeciais = false;
    
    if (user.id) {
        user.origin = 'system';
    }
    
    return [user, infos];
}



```

### Chamada de metodos

```js
// Not good
minhaFuncaoMagical(true, "valor2", {valor1: 1, valor: 2, outroValor: "uma string qualquer"});

// Good
minhaFuncaoMagical(
    true,
    "valor2",
    {
        valor1: 1,
        valor: 2,
        outroValor: "uma string qualquer"
    }
);

// Mais Good ainda
var options = {
        valor1: 1,
        valor: 2,
        outroValor: "uma string qualquer"
    };

minhaFuncaoMagical(true, "valor2", options);

```


### Nomeando as coisas

- Crie variaveis para expressar melhor valores dos argumentos de um metodo;


```js
// Not good
function cadastraUsuario (nome, genero, ehUsuarioInterno) {
    // 
}
cadastraUsuario('Joaquim Frederico', 'm', 1);

// Good
var MASCULINO = 'm',
    FEMININO = 'f',
    USUARIO_INTERNO = 1,
    USUARIO_EXTERNO = 0;

function cadastraUsuario (nome, genero, ehUsuarioInterno) {
    // 
}
cadastraUsuario('Joaquim Frederico', MASCULINO, USUARIO_INTERNO);

```
Usar camelCase em nome de metodos e variavies;
```js
// Not good

var nome_do_usuario;

class MinhaClass {
    set_NomeDoUsuario () {
        // ..
    }
    get_NomeDoUsuario () {
        // ..
    }
}

// Good
var nomeDoUsuario;

class MinhaClass {
    setNomeDoUsuario () {
        // ..
    }
    getNomeDoUsuario () {
        // ..
    }
}

```

Deixe claro na assinatura do metodo o que ele faz. Não importa se ficar muito longo.

```js
// Not good
function enviar (cliente, mensagem) {
    //..
};

// Good
function enviarMensagemParaCliente (cliente, mensagem) {
    //..
};

```


Evite abreviacoes ou nomes sem semantica.

```js
// Not good
var lst = [1, 2, 3],
    a = new User();
    
a.nome = 'fred';
a.salva();


// Good
var listaDeIds = [1, 2, 3],
    user = new User();
    
user.nome = 'fred';
user.salva();

```
