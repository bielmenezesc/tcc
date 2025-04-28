# Um Relato de Experiência sobre o Uso da Ferramenta n8n na Criação de Automações com Inteligência Artificial para Atendimento ao Cliente

Este repositório contém os fluxos de automação desenvolvidos no n8n para relatar a experiência de desenvolvimento nesta plataforma, com um foco em automações com inteligência artificial envolvendo agentes IA para realizar atendimento ao cliente. Foram implementadas três arquiteturas distintas utilizando o modelo GPT-4o mini:

- **Prompt Engineering Simples**
- **RAG Tradicional**
- **Agentic RAG com Memória de Longo Prazo**

## Estrutura dos Fluxos

Abaixo, uma breve demonstração visual da estrutura de cada arquitetura:

### 1. Prompt Engineering Simples

![image](https://github.com/user-attachments/assets/e6da6a94-f9b8-450e-a8f0-1c6da33381e6)


- **Descrição**: Integra todas as informações relevantes diretamente no prompt do LLM via templates dinâmicos.
- **Características**:  
  - Alta dependência da janela de contexto.  
  - Custo elevado devido à alta quantidade de tokens.
  - Rápido e eficaz para consultas simples.

### 2. RAG Tradicional

![image](https://github.com/user-attachments/assets/50a2a448-440e-4c46-8e4e-1caeee9b1795)

- **Descrição**: Utiliza recuperação vetorial para obter até 4 *chunks* dos dados mais relevantes, que são então injetados no prompt.
- **Características**:  
  - Menor custo operacional.  
  - Limitação dos *chunks* pode resultar na perda de informações em consultas complexas.

### 3. Agentic RAG com Memória de Longo Prazo

![image](https://github.com/user-attachments/assets/0d9f1cf3-9333-4978-aff6-d45380769d68)

- **Descrição**: Adiciona um agente capaz de avaliar a resposta inicial e decidir, de forma autônoma, entre diferentes estratégias de recuperação (como RAG ou busca completa via list documents/get content). Incorpora também memória de longo prazo para contextos contínuos.
- **Características**:  
  - Maior robustez e adaptabilidade.  
  - Permite uma segunda etapa de consulta se o primeiro resultado não for satisfatório.
  - Ideal para cenários com alta complexidade de dados.

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

## Contato

Para mais informações ou dúvidas, entre em contato:  
Gabriel Menezes Cabral – bielmenezesc@gmail.com – [Meu Linkedin](https://www.linkedin.com/in/gabrielmenezesc/)
