Elixir:
Para que serve o ^ (pin operator) em elixir?
Quando estamos aprendendo elixir, não fica claro o motivo pelo qual precisaríamos usar o pin operator.
Vamos lá:
Já sabemos que elixir trabalha com pattern matching.

```elixir 
map = %{code: %{country: "UK", city: "London"}, name: "United Kingdom"}
```
Se quiser pegar o valor de city, podemos usar pattern matching:

```elixir
%{code: %{city: cidade}} = map
```
Agora, cidade tem o valor de London.

Vamos imaginar que em outro momento do código, precisemos fazer pattern matchin com esse valor, aí que entra o ^ (pin operator):

```elixir
map2 = %{code: %{country: "UK", city: "notLondon"}, name: "United Kingdom"}
{:ok, ^country} = {:ok, map2.code.country}
```
Se fossemos usar {:ok, country}, iríamos reatribuir o valor de country para notLondon, mas o que queremos nesta etapa é verificar se o map2.code.country é "London", para isso colocamos um ^(pin operator), 
a fim de dizer para o Elixir: não reatribua essa variável, verifique se os valores dão match.

