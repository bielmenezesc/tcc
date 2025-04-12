# Aplicando Arquitetura Agentic RAG com N8N para Atendimento ao Cliente

Este repositório contém os fluxos de automação desenvolvidos no n8n para comparar e evidenciar diferentes estratégias de recuperação de informação aplicadas ao atendimento ao cliente. Foram implementadas três arquiteturas distintas utilizando o modelo GPT-4o mini:

- **Prompt Engineering Simples**
- **RAG Tradicional**
- **Agentic RAG com Memória de Longo Prazo**

## Visão Geral

O objetivo deste repositório é demonstrar, de forma prática e comparativa, os benefícios e limitações de cada abordagem no contexto de atendimento ao cliente. Em cenários de baixa complexidade, todas as abordagens podem fornecer respostas satisfatórias. Entretanto, quando a complexidade e o volume de informações aumentam, surgem diferenças importantes:

- **Prompt Engineering Simples**:  
  - **Vantagens**: Respostas precisas em consultas simples.  
  - **Limitações**: Altos custos devido à dependência da janela de contexto; manutenção constante se as informações mudarem frequentemente.

- **RAG Tradicional**:  
  - **Vantagens**: Redução do custo operacional ao reduzir a quantidade de informações passadas no prompt.  
  - **Limitações**: Restrição do retorno a 4 *chunks* (cada um com 1000 caracteres) pode ocasionar perda de informações essenciais em consultas complexas.

- **Agentic RAG com Memória de Longo Prazo**:  
  - **Vantagens**: Maior robustez e autonomia. O agente avalia a resposta inicial e, se necessário, recorre a estratégias alternativas (como recuperar documentos inteiros) para compor uma resposta mais completa.  
  - **Limitações**: Maior tempo de resposta e custo intermediário, mas isso é compensado pela melhoria na qualidade das respostas em situações desafiadoras.

## Estrutura dos Fluxos

Cada fluxo foi construído no n8n e está disponível no repositório. Abaixo, uma breve descrição da estrutura de cada arquitetura:

### 1. Prompt Engineering Simples

![image](https://github.com/user-attachments/assets/545f12ce-4ed0-4024-8076-9184daeba7be)

- **Descrição**: Integra todas as informações relevantes diretamente no prompt do LLM via templates dinâmicos.
- **Características**:  
  - Alta dependência da janela de contexto.  
  - Custo elevado devido à alta quantidade de tokens.
  - Rápido e eficaz para consultas simples.

### 2. RAG Tradicional

![image](https://github.com/user-attachments/assets/6cd18272-c021-49e6-830b-d9053ae10eca)

- **Descrição**: Utiliza recuperação vetorial para obter até 4 *chunks* dos dados mais relevantes, que são então injetados no prompt.
- **Características**:  
  - Menor custo operacional.  
  - Limitação dos *chunks* pode resultar na perda de informações em consultas complexas.

### 3. Agentic RAG com Memória de Longo Prazo

![image](https://github.com/user-attachments/assets/37cf0d04-2c96-4e93-9e8c-92dda687426c)

- **Descrição**: Adiciona um agente capaz de avaliar a resposta inicial e decidir, de forma autônoma, entre diferentes estratégias de recuperação (como RAG ou busca completa via list documents/get content). Incorpora também memória de longo prazo para contextos contínuos.
- **Características**:  
  - Maior robustez e adaptabilidade.  
  - Permite uma segunda etapa de consulta se o primeiro resultado não for satisfatório.
  - Ideal para cenários com alta complexidade de dados.

## Resultados e Discussões

Os testes comparativos avaliaram as três arquiteturas utilizando métricas de:

- **Precisão das respostas**
- **Redução de alucinações**
- **Tempo de resposta**
- **Custo operacional**

Os resultados indicaram que, embora todas as arquiteturas funcionem de forma satisfatória em consultas simples, a abordagem Agentic RAG se destaca por sua capacidade de adaptar a estratégia de busca e fornecer respostas mais robustas em cenários complexos.

## Instruções de Uso

1. **Configuração do Ambiente**:  
   - Certifique-se de ter o n8n instalado e configurado.
   - Configure suas credenciais para acesso a ferramentas externas (ex.: Supabase, API da OpenAI, etc.) conforme instruções nos fluxos.

2. **Importação dos Fluxos**:  
   - Importe os arquivos de fluxo (JSON) disponíveis neste repositório para o seu ambiente n8n.
   - Verifique e ajuste as configurações dos nodes, se necessário, de acordo com seu ambiente de teste.

3. **Execução e Testes**:  
   - Realize testes com um conjunto variado de perguntas para avaliar cada arquitetura.
   - Compare os resultados qualitativos e quantitativos utilizando as métricas descritas no TCC.

## Trabalhos Futuros

Embora os testes realizados tenham demonstrado que todas as arquiteturas podem fornecer respostas satisfatórias para consultas simples, investigações futuras poderão expandir os cenários para casos com maior complexidade, onde as vantagens do Agentic RAG serão mais evidentes, como em consultas com múltiplas fontes de informação e interações de alta complexidade.

## Contato

Para mais informações ou dúvidas, entre em contato:  
Gabriel Menezes Cabral – bielmenezesc@gmail.com – [Meu Linkedin](https://www.linkedin.com/in/gabrielmenezesc/)
