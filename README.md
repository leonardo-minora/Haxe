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
