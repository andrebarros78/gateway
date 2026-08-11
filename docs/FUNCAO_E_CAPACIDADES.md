# Gateway — função e capacidades

## Função

O **gateway** é a porta controlada entre Pipo e a infraestrutura local.

```
Pipo
  ↓
Gateway
  ↓
TUNEL-CORE
  ↓
Supervisor / Watchdog
  ↓
Túnel
  ↓
Windows MCP
```

Ele recebe pedidos de IA, aplica regras de acesso e encaminha somente o tráfego autorizado ao TUNEL-CORE. Ele não substitui o túnel, não executa comandos no Windows e não guarda a chave da OpenAI no código.

## Capacidades do gateway

### 1. Conexão com IA

- Conecta o gateway à API da OpenAI por meio da variável protegida `OPENAI_API_KEY`.
- Mantém a chave fora de arquivos, commits, conversas e registros.
- Usa o Agentgateway como componente de integração, fixado na versão definida em `UPSTREAM.lock`.
- Permite que Pipo use uma única entrada para a IA, sem expor a infraestrutura interna diretamente.

### 2. Controle de entrada

Quando implantado no TUNEL-CORE, o gateway poderá:

- autenticar quem tenta entrar;
- limitar chamadas excessivas;
- aplicar regras de autorização;
- encaminhar cada chamada ao destino correto;
- registrar métricas e erros técnicos;
- impedir que serviços externos alcancem diretamente o Windows MCP.

### 3. Verificação por GitHub Action

A Action `Validar conexao OpenAI` existe para validar manualmente:

1. se o segredo `OPENAI_API_KEY` foi cadastrado;
2. se a chave consegue acessar a API da OpenAI;
3. se o arquivo de configuração do gateway está presente.

Ela não é o gateway em operação contínua. Ela é apenas a prova controlada de que a ligação com a IA está configurada.

## Responsabilidades das demais camadas

| Camada | Responsabilidade |
|---|---|
| Pipo | Decide e solicita a ação técnica. |
| Gateway | Controla a entrada e a ligação com a IA. |
| TUNEL-CORE | Coordena a comunicação interna e o estado operacional. |
| Supervisor / Watchdog | Monitora, reinicia e recupera serviços. |
| Túnel | Mantém a passagem persistente entre redes. |
| Windows MCP | Executa ferramentas e ações no computador autorizado. |

## Estado atual comprovado

- Repositório independente criado.
- Configuração do Agentgateway para OpenAI publicada.
- Action manual de validação publicada.
- Chave de API ausente do código e protegida por regra.
- Cópia local preparada em `C:\New Projet\gateway`.

## O que ainda falta para a operação real

- Cadastrar `OPENAI_API_KEY` como segredo do GitHub.
- Executar a Action e obter `OPENAI_API_CONNECTION=OK`.
- Instalar o Agentgateway no TUNEL-CORE.
- Integrar o Supervisor / Watchdog, o túnel e o Windows MCP.
- Validar reinício, recuperação e bloqueio de acesso não autorizado.

**Conclusão:** o gateway está preparado como módulo de conexão e controle da IA; ele ainda não está operando ponta a ponta até o Windows MCP.
