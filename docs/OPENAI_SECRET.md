# Chave da API da OpenAI

A chave precisa ficar somente no cofre de segredos do GitHub.

## Ação única necessária

No repositório `gateway`, abra:

`Settings → Secrets and variables → Actions → New repository secret`

Crie o segredo com este nome exato:

`OPENAI_API_KEY`

Cole nele uma chave criada na plataforma da OpenAI. Nunca coloque a chave em arquivo, conversa, commit ou variável pública.

Depois, abra `Actions → Validar conexao OpenAI → Run workflow`.

Resultado esperado:

```
OPENAI_API_CONNECTION=OK
GATEWAY_CONFIGURATION=OK
```

A Action apenas valida a credencial e o arquivo de configuração. Ela não mantém o gateway ligado; a execução contínua será feita no TUNEL-CORE.
