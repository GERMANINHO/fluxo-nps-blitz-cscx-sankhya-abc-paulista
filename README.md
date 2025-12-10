# Fluxo NPS Blitz — CS/CX Sankhya ABC Paulista

Launcher operacional da **Blitz NPS** do time de **CS/CX Sankhya ABC Paulista**.  

Esta página em **HTML/CSS/JS puro** centraliza o texto oficial da Blitz e automatiza a preparação dos disparos por **e-mail (Gmail)** e **WhatsApp Web**, sem enviar nada sozinha: você sempre revisa e confirma antes de disparar.

---

## 🔎 Visão geral

- **Objetivo:**  
  Facilitar a execução da **Blitz NPS mensal**, garantindo:
  - Texto padrão alinhado com o time de CS/CX;
  - Disparo consistente para todos os clientes selecionados;
  - Menos tempo clicando/manual, mais tempo analisando resposta.

- **Como funciona:**  
  A página oferece:
  - Campo com o **texto padrão da Blitz**, que pode ser ajustado;
  - Botão para **copiar** a mensagem para a área de transferência;
  - Card para **disparo por e-mail (Gmail)**:
    - Define assunto;
    - Lista de destinatários;
    - Abre o Gmail com **Para**, **CCO**, **assunto** e **corpo** preenchidos;
  - Card para **disparo via WhatsApp**:
    - Lista de telefones (com DDI/DDD);
    - Gera links `wa.me` com a mensagem pronta.

- **Arquitetura:**  
  - 100% **front-end** (HTML + CSS + JS);
  - Nenhum backend ou armazenamento de dados;
  - Ideal para **GitHub Pages**.

---

## 🧭 Fluxo operacional (passo a passo)

### 1. Preparar o texto da Blitz

Na coluna esquerda:

- Campo **“Texto padrão da Blitz”**:
  - É preenchido automaticamente com o texto oficial (NPS, Indecx, impacto no CS etc.);
  - Você pode ajustar a mensagem (nome do CS, tom, detalhes do cliente).
- Botão **“Copiar texto da Blitz”**:
  - Copia o texto atual para a área de transferência;
  - Útil se quiser colar manualmente em outro canal/sistema.

> Dica (exibida na própria tela):  
> Depois de abrir o Gmail ou o WhatsApp Web, revise o texto, **anexe a arte `NPS_Blitz.jpg`** e só então clique em **Enviar**.

Abaixo, há um **preview da arte da Blitz**:

- `NPS_Blitz.jpg` exibida no card;
- Legenda: “Preview da arte da Blitz. Arquivo: `NPS_Blitz.jpg`”.

---

### 2. Disparo por e-mail (Gmail)

Na coluna direita, primeiro card:

- **Remetente:**  
  O Gmail corporativo logado, ex.:  
  `gustavo.germano@sankhya.com.br` (vai em **Para**).

- **Destinatários (clientes):**
  - Campo **“Lista de e-mails (um por linha)”** (`id="emails"`).
  - Você pode colar:
    - Um e-mail por linha, ou  
    - Separados por `,` ou `;` (o script limpa e organiza).

- **Assunto:**
  - Campo `id="subject"` com valor padrão:  
    `Pesquisa NPS Sankhya — a sua opinião tem poder transformador`
  - Pode ser alterado antes de clicar no botão.

- **Botão “Abrir Gmail com a Blitz” (`id="btn-gmail")`:**
  - Valida se há pelo menos um e-mail;
  - Monta o corpo:
    - **Texto da Blitz** (campo da esquerda ou padrão, se estiver vazio);
    - Rodapé automático:

      ```text
      ---
      Qualquer dúvida, estou à disposição.
      Gustavo Germano
      ```

  - Monta o compose do Gmail com:
    - **Para:** `gustavo.germano@sankhya.com.br` (padrão no código);
    - **CCO:** lista de e-mails informados;
    - **Assunto:** valor do campo `subject`;
    - **Corpo:** mensagem + assinatura.

  - Abre uma nova aba do Gmail usando a URL base:

    ```js
    https://mail.google.com/mail/u/<GMAIL_USER_INDEX>/?view=cm&fs=1
    ```

> Observação: a página **não envia** o e-mail.  
> Ela apenas abre o Gmail com tudo pronto para você revisar, anexar `NPS_Blitz.jpg` e clicar em **Enviar**.

---

### 3. Disparo via WhatsApp

No segundo card da coluna direita:

- **Telefone base:**  
  O texto orienta usar o WhatsApp Web conectado ao celular  
  **`11 91441-9960`** (ajustável no HTML, se necessário).

- **Telefones:**
  - Campo `id="whatsapps"`:
    - Um telefone por linha;
    - Deve incluir **DDI + DDD + número** (ex.: `5599999999999`).
  - A página remove caracteres não numéricos (`x.replace(/\D/g,'')`), então:
    - Pode colar números com espaços, parênteses, traços etc.

- **Botão “Gerar links de envio” (`id="btn-wa")`:**
  - Valida se há pelo menos um telefone;
  - Usa o texto da Blitz (campo da esquerda ou padrão);
  - Para cada telefone, cria um link:

    ```text
    https://wa.me/<telefone>?text=<mensagem_codificada>
    ```

  - Lista os links em `#wa-links` como:
    - “**Enviar Blitz para \<telefone\>**” (um link por cliente).

> Basta clicar em cada link para abrir a conversa no **WhatsApp Web** com a mensagem pronta — você só revisa e envia.

---

## 🧱 Estrutura do projeto

```text
/ (raiz do repositório)
├── index.html      # página única com layout, lógica e estilos
└── NPS_Blitz.jpg   # arte utilizada na Blitz (preview e anexos de e-mail)
