# Supabase:

## Por quê?

Ao invés de criar um app com flask, por exemplo, ou express, o
supabase/firebase/pocketbase, já provê a api para manipulação do banco
de dados. Para isso, ao invés de você autenticar tudo pelo backend, você
pode configurar e autenticar tudo pelo supabase. Dessa forma, a
comunicação é direta com o banco, sem precisar de intermediários.

## Para quê?

Desenvolver mais rápido, sem precisar configurar um servidor e banco de
dados só para isso.

## Quais alternativas?

Criar um app com servidor para ser intermediário entre o app e o
servidor.

## Quais offs?

menor controle de banco de dados, já que é uma solução pronta, mas
atende a maior parte das necessidades mais comuns e algumas até mais
avançadas que um app possa precisar.

# Entendendo serverless

Seu código no computador:

``` python
escolha = int(input('escolha um número'))
if escolha >= 5:
    print('maior do que 5')
else:
    print('menor do que 5')
```

Seu código na web:

``` python
from flask import Flask

app = Flask(__name__)
@app.get('/escolha/<int:numero>')
def escolha(numero):
    if escolha >= 5:
        return 'maior do que 5'
    else:
        return 'menor do que 5'
```

Seu código em serverless:

``` python
import json
def lambda_handler(event, context):
    numero = int(event['queryStringParameters']['numero'])


    if numero >= 5:
        resultado = 'maior do que 5'
    else:
        resultado = 'menor do que 5'


    return {
        'statusCode': 200,
        'body': json.dumps({'resultado': resultado})
    }
```

    curl -X GET https://<URL_DO_API_GATEWAY>?numero=7

# DJANGO
## Como expor settings ou qualquer outro arquivo nos templates?

context_processors

