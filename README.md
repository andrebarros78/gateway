# gateway

Módulo independente da cadeia operacional:

```
Pipo
  ↓
gateway
  ↓
TUNEL-CORE
  ↓
Supervisor / Watchdog
  ↓
Túnel
  ↓
Windows MCP
```

## Função

O gateway recebe as chamadas de IA do Pipo, aplica autenticação, limites, roteamento e observabilidade, e as entrega ao TUNEL-CORE.

## Limites

- Este repositório não é fork, submódulo ou cópia de qualquer outro projeto.
- Ele não contém credenciais, chaves de API, túneis ou dados pessoais.
- O Supervisor / Watchdog mantém, monitora e recupera a operação antes do túnel.
- O túnel é a única passagem até o Windows MCP.
- O gateway não executa tarefas diretamente nos computadores.

## Componente adotado

- Projeto: [Agentgateway](https://github.com/agentgateway/agentgateway)
- Versão fixada: `v1.4.1`
- Licença do componente: Apache-2.0
- Registro técnico: [UPSTREAM.lock](UPSTREAM.lock)

A instalação executável só será feita no computador central depois da estabilidade comprovada da cadeia completa.
