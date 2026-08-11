# Instruções do módulo gateway

## Missão

O gateway é uma peça independente entre a IA e o TUNEL-CORE:

```
IA/GPT → gateway → TUNEL-CORE → Windows MCP → computadores
```

Ele controla a entrada, a autenticação, os limites e a observabilidade. Ele não substitui o TUNEL-CORE nem executa tarefas diretamente nos computadores.

## Limites obrigatórios

- Não criar fork, submódulo, vínculo Git ou dependência de projetos externos do André.
- Não copiar credenciais, chaves, tokens, logs pessoais ou configurações de computadores para este repositório.
- Nunca gravar `OPENAI_API_KEY` em arquivo, commit, issue, comentário ou saída de teste.
- A chave da OpenAI deve existir somente como segredo `OPENAI_API_KEY` no GitHub e, na execução contínua, no cofre de segredos do TUNEL-CORE.
- O componente externo adotado é Agentgateway, versão fixada em `UPSTREAM.lock`. Atualizações exigem verificação de licença, integridade, compatibilidade e teste.

## Operação

- A GitHub Action valida a chave e a configuração sob execução manual.
- GitHub Actions não é ambiente de operação permanente.
- A operação contínua do gateway será instalada no TUNEL-CORE somente após a estabilidade comprovada do Windows MCP.
- O gateway deve iniciar sem depender de caminhos em `D:\`, pendrives ou perfil do Windows.

## Critério de conclusão de uma mudança

Uma mudança só é concluída quando houver:

1. configuração validada;
2. segredo fora do código;
3. teste de conexão aprovado;
4. reinício e recuperação comprovados no TUNEL-CORE;
5. nenhuma exposição de credencial no repositório.

## Comunicação de execução

Registrar apenas evidência objetiva: encontrado, alterado, testado, resultado e pendência real.
