# oprojeto
# 🤖 Copiloto IA

**Projeto da 1ª Disciplina de IA e Automação Digital - Fundamentos de IA com foco em IA Generativa**

* **Aluna:** Bruna Gabriela Ribeiro Sartor
* **Tutor:** Fernando Leonid
* **Professor:** Rafael Venancio
* **Instituição:** UniFECAF + Rocketseat
* **Mês da disciplina:** Outubro/2025

---

## 🎯 1. Objetivo do Projeto

Este projeto tem como objetivo reduzir a sobrecarga de serviço dedicado a questões básicas do setor interno de Recursos Humanos, utilizando, para isso, a IA Generativa e garantindo clareza, assertividade e identidade organizacional em suas respostas.
Esta automação recebe e-mails, analisa o conteúdo usando o Gemini AI e envia uma resposta automática para o remetente.

## 💡 2. A Automação (O Cenário no Make.com)

A automação segue o seguinte fluxo:

### 1. Gatilho Inicial
* **Módulo:** 'Gmail - Watch emails'
* **Função:** Inicia o cenário sempre que um novo e-mail chega à caixa de entrada conectada.

### 2. Listagem de Anexos
* **Módulo:** 'Gmail - List email attachments and media'
* **Função:** Verifica se o e-mail recebido contém anexos.

### 3. Roteamento Principal (Router 1)
Um **Router** divide o fluxo com base na existência de anexos:

* **Rota 1 (Sem Anexo):**
    * O e-mail segue diretamente para análise.
* **Rota 2 (Com Anexo):**
    * O fluxo segue para a identificação do tipo de arquivo.

### Processamento das Rotas

### Rota 1: E-mail Sem Anexo
1.  **Análise de Texto (IA):**
    * **Módulo:** 'Gemini - Generate a Response'
    * **Ação:** O corpo do e-mail é analisado pela IA, que gera uma resposta apropriada.
2.  **Envio de Resposta:**
    * **Módulo:** 'Gmail - Send an email'
    * **Ação:** Envia a resposta gerada ao remetente original.

### Rota 2: E-mail Com Anexo
Um segundo **Router (Router 2)** filtra o tipo de anexo:

#### A. Sub-rota: Arquivo PDF
1.  **Upload do Arquivo:**
    * **Módulo:** 'Gemini - Upload a file'
    * **Ação:** Carrega o PDF para análise pela IA.
2.  **Resumo do Anexo (IA):**
    * **Módulo:** 'Gemini - Generate a Response' (1º)
    * **Ação:** Gera um resumo do conteúdo do PDF.
3.  **Análise do E-mail (IA):**
    * **Módulo:** 'Gemini - Generate a Response' (2º)
    * **Ação:** Analisa o corpo do e-mail e gera uma resposta, considerando também o resumo do anexo.
4.  **Envio de Resposta:**
    * **Módulo:** 'Gmail - Send an email'
    * **Ação:** Envia a resposta final (com o resumo) ao remetente.

#### B. Sub-rota: Arquivo DOC/DOCX
1.  **Conversão de Arquivo:**
    * **Módulo:** 'iLovePDF - Office to PDF'
    * **Ação:** Converte o arquivo DOC/DOCX para PDF.
2.  **Fluxo Segue como PDF:**
    * Após a conversão, o arquivo segue os mesmos passos da **Sub-rota A (PDF)**: Upload -> Resumo -> Análise de Texto -> Envio de Resposta.
   
---

### 🖼️ Diagrama do Cenário

<img width="1899" height="907" alt="Print Make Fluxo" src="https://github.com/user-attachments/assets/b3e7aac7-3b18-47db-b58f-6b6d63bf94c1" />


---

## 🛠️ 3. Ferramentas e Tecnologias Utilizadas

* **Plataforma de Automação:** [Make.com](https://www.make.com/)
* **IA Generativa:** Gemini 2.5 Flash
* **Gravação do Vídeo:** PowerPoint
* **Diagramas:** Miro/Lucidchart/Excalidraw/Mapify    

---

## ✏️ 4. Instruções

**Blueprint do Cenário**
Eu exportei o "Blueprint" do cenário. O json está na pasta compartilhada. Você pode importá-lo no Make.com para ver os módulos. 

1. Nos módulos Gmail conecte-se com sua conta google.
2. Nos módulos Gemini conecte-se com sua chave API fornecida pelo Google AI Studio.
3. No módulo iLovePDF conecte-se com sua chave API fornecida pelo iLovePDF.
4. Para ativar, envie um e-mail para o g-mail configurado, aguarde chegar na caixa de entrada e clique em "Run once" no cenário do Make.
5. Os módulos serão executados.
6. Verifique sua caixa de entrada para conferir se chegou a resposta.

---

## ✍️ 5. Exemplos de Uso

* **Dúvida sobre férias:**

  Input: Olá, quero tirar 15 dias de férias no próximo mês. O que preciso fazer?

  Output:

  "Prezado(a), [nome].
  Agradecemos o seu contato.
  Referente à sua solicitação sobre o agendamento de férias, o processo deve ser realizado através do Portal do Colaborador, na seção "Solicitações".
  Conforme nossa política interna, o pedido deve ser registrado com antecedência mínima de 30 dias para análise e aprovação do seu gestor direto.
  Permanecemos à disposição para qualquer esclarecimento.
  At.te,
  Recursos Humanos"

* **Dúvida sobre benefícios:**

   Input: Olá, sou novo na empresa. Pode me informar os benefícios que tenho direito, como Vale-refeição?

  Output:

  "Prezado(a), [nome].
  Agradecemos o seu contato.
  Referente à sua dúvida sobre os benefícios aos quais tem direito, como o Vale-refeição, informamos que os benefícios atualmente oferecidos pela empresa incluem Vale-refeição, Vale-transporte e Plano de Saúde.
  As informações detalhadas sobre a utilização e gestão dos seus benefícios podem ser acessadas no Portal do Colaborador, na seção "Benefícios".
  Permanecemos à disposição para qualquer esclarecimento adicional.
  At.te,
  Recursos Humanos"

* **Resumo de reunião:** 

  Input: Encaminho-lhe este anexo. Resuma a pauta dessa reunião. (junta o anexo)

  Output:
  
  "Segue seu resumo".
  At.te,
  Recursos Humanos"

---

🎖️Para concluir, aponto minha satisfação em participar desse projeto. Agradeço toda a orientação que tive e estou certa de que tirei muito proveito da disciplina, pois agreguei vários conhecimentos que me pareciam inalcançáveis.
