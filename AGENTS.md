# Instruções do módulo gateway

## Arquitetura obrigatória

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

O gateway recebe chamadas de IA do Pipo. Ele controla entrada, autenticação, limites, roteamento e observabilidade. Não substitui o TUNEL-CORE, o Supervisor / Watchdog, o túnel nem o Windows MCP.

## Limites obrigatórios

- Não criar fork, submódulo, vínculo Git ou dependência de projetos externos do André.
- Não copiar credenciais, chaves, tokens, logs pessoais ou configurações de computadores para este repositório.
- Nunca gravar `OPENAI_API_KEY` em arquivo, commit, issue, comentário ou saída de teste.
- A chave da OpenAI deve existir somente como segredo `OPENAI_API_KEY` no GitHub e, na execução contínua, no cofre de segredos do TUNEL-CORE.
- O componente externo adotado é Agentgateway, versão fixada em `UPSTREAM.lock`. Atualizações exigem verificação de licença, integridade, compatibilidade e teste.

## Operação

- A GitHub Action valida a chave e a configuração sob execução manual.
- GitHub Actions não é ambiente de operação permanente.
- O Supervisor / Watchdog deve iniciar e recuperar TUNEL-CORE e túnel antes de liberar passagem ao Windows MCP.
- O gateway deve iniciar sem depender de caminhos em `D:\`, pendrives ou perfil do Windows.

## Critério de conclusão de uma mudança

Uma mudança só é concluída quando houver:

1. configuração validada;
2. segredo fora do código;
3. teste de conexão aprovado;
4. reinício e recuperação comprovados em toda a cadeia;
5. nenhuma exposição de credencial no repositório.

## Comunicação de execução

Registrar apenas evidência objetiva: encontrado, alterado, testado, resultado e pendência real.
