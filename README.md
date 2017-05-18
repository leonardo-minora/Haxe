# Haxe
## Componentes
* Pedro Oliveira <20141011110158> <@pedrowoliveira>
* Nestor Caetano <2014101111>
* Jorge Enrique <2014101111>
## Resumo
Haxe é uma linguagem de alto nível, open source e compilador. Ela permite compilar programas usando sintaxe baseada no ECMAScript para diversas linguagens finais (JS, PHP, Neko, Python, C++, Java, C#, etc). O desenvolvedor afirma que, mantendo a abstração apropriada, é póssível ter um só código compilando para diversas linguagens. Aceita, por tanto, orientação a objetos, linguagem funcional e procedural. A linguagem/compilador é mantido pela [Haxe Foundation](https://haxe.org/foundation/people.html "Haxe Foundation"). Ela foi criada em 2005, porém, a fundação só surgiu depois. 
## Instalação e uso
Haxe é instalado apartir de seu executável que pode ser baixado [aqui](https://haxe.org/download/). Arquivos que o compilador Haxe entende são .hx. Após instalado, pode ser utilizado a partir do command line. Suponha o seguinte código, salvo no arquivo "Main.hx"
```csharp
class Main {
  static public function main():Void {
    trace("Hello World");
  }
}
```
Isto pode ser compilado com o seguinte comando no terminal.
`haxe -main HelloWorld -js HelloWorld.js`
Para compilar e executar o programa, é possível:
`haxe -main Main --interp`
Assim, o arquivo será compilado em Javascript. Veja o [guia completo do compilador](https://haxe.org/manual/compiler-usage.html).
## Sintaxe básica
### Variáveis e constantes
#### Variáveis
Variáveis em Haxe são declaradas da seguinte forma:
```csharp
var a; // Declara variável local a.
var b:Int; // Declara variável b do tipo Int
var c = 1; // Declara variável c e a inicializa com valor 1
var d,e = 2; // Declara variaveis d & e, inicializa-as com valor 2
```
#### Constantes
Constantes em Haxe são declaradas como variáveis, da seguinte forma:
```csharp
class Classe {
  public static inline var CONSTANTE = 100;
}
```
#### Tipos
No Haxe, os tipos das variáveis são inferidos ao atribuir um valor. Porém, é possível atribuir o tipo no momento da declaração da variável, como visto acima. Os tipos básicos são `Bool`, `Float`, `Int`, `String`.
#### Operadores lógicos
* Operador igual (`==`)
* Operador e (`&&`)
* Operador diferente (`!=`)
* Operador negação (`!`)
* Operador ou (`||`)
#### Estrutura For

```csharp

```
## Sintaxe OO
A sintaxe de orientação a objetos em Haxe é familiar aqueles que desenvolvem em C#, Java, PHP e outras linguagens similares.
#### Classes
A mais importante estrutura no Haxe. É declarada da seguinte forma:
```csharp
class Pessoa {
  var Nome : String;
  var Idade : Int;
  public function new(n, i){
    Nome = n;
    Idade = i;
  }
  public function toString(){
    return Nome + " de " + Idade " anos."; 
  }
}
```
A classe tem nome (`Pessoa`), campos (`Nome`, `Idade`), funções construtor (`function new(n, i)`) e declarada (`toString()`);
##### Campos de uma classe
Podem ser variáveis, propriedades e metódos.
##### Variáveis
Dentro de uma classe, declara-se:
```csharp
static var nome:String = "Fulano";
```
Percebe-se que as variáveis tem:
1. Um nome (`nome`);
2. Um tipo (`String`);
3. Pode ter um valor de inicialização (`"Fulano"`);
4. Pode ter modificadores de acesso (`static`) (Ver mais abaixo);
##### Propriedades
Muito parecido com variavéis, propriedades oferecem mais controle sobre read/write de seu valor. São declaradas assim, dentro de uma classe:
```csharp
public var nome(identificador read, identificador write):String;
```
Como pode-se perceber, a diferença entre declaração de variáveis e propriedades é a presença dos identificadores de acesso.
##### Identificadores de acesso
Podem ser
* `default`: Permite acesso normal ao campo, dado que este tenha visibilidade pública. Se não, é igual ao acesso `null`.
* `null`: Acesso permitido somente de dentro da classe.
* `get`/`set`: Acesso é feito a partir de um método que deve existir (gera exceção em tempo de compilação).
* `dynamic`: Como o acima, mas não gera exceção.
* `never`: O campo nunca é acessado.
Alguns casos comuns de combinação de identificadores de acesso:
```csharp
class Main {
  // Lê de fora, escreve somente de dentro do Main
  public var ro(default, null):Int;
  
  // Escreve de fora, só lê dentro do Main
  public var wo(null, default):Int;
  
  // Acesso a partir de getter get_x e setter set_x
  public var x(get, set):Int;
  
  // Lê pelo getter, nunca escreve
  public var y(get, never):Int;
  
  // Getter do campo x
  function get_x() return 1;
  
  // Setter do campo x
  function set_x(x) return x;
  
  // Getter do campo y
  function get_y() return 1;
}
```
##### Métodos
Declaração:
```csharp
class Main {
  static public function main():Void {
    trace("Olá, mundo!");
    minhaFunc("birll", 1);
  }
  
  static function minhaFunc(a:String, i) {
    return true;
  }
}
```
Tomemos a função minhaFunc(). Ela tem:
1. Um nome (`minhaFunc`)
2. Argumentos (`a:String, i`)
3. Pode ter modificadores de acesso (`static`, `public`)
4. Pode ter uma expressão (Não tem)
5. Pode ter um retorno (`return true`);
##### Sobrescrevendo métodos
Quando em herança, é possível a sobrescrita de um método da classe superior pelo modificador de acesso `override`:
```csharp
class Base {
  public function new() { }
  public function myMethod() {
    return "Base";
  }
}

class Child extends Base {
  public override function myMethod() {
    return "Child";
  }
}

class Main {
  static public function main() {
    var child:Base = new Child();
    trace(child.myMethod()); // Child
  }
}
```
##### Modificadores de acesso
##### Visibilidade
Podem ser:
1. `public`: O acesso é de qualquer escopo
2. `private`: O acesso é restrito a classe e a subclasses.
##### Especial
Em Haxe, existe o modificador `inline`, que permite a escrita do código da função diretamente, ao invés de uma chamada para ela.
