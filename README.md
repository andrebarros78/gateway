# gateway

Módulo independente que posiciona o **Agentgateway** entre a IA e o TUNEL-CORE.

```
IA/GPT → gateway → TUNEL-CORE → Windows MCP → computadores
```

## Limites

- Este repositório não é fork, submódulo ou cópia de qualquer outro projeto.
- Ele não contém credenciais, chaves de API, túneis ou dados pessoais.
- O TUNEL-CORE continua responsável pela conexão persistente.
- O gateway aplica entrada controlada, autenticação, limites, roteamento e observabilidade.

## Componente adotado

- Projeto: [Agentgateway](https://github.com/agentgateway/agentgateway)
- Versão fixada: `v1.4.1`
- Licença do componente: Apache-2.0
- Registro técnico: [UPSTREAM.lock](UPSTREAM.lock)

A instalação executável só será feita no computador central depois da conexão Windows MCP estar estável e da validação da versão e integridade do pacote.
