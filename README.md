# Fluxo NPS Blitz — CS/CX — Sankhya ABC Paulista (fluxo-nps-blitz-cscx-sankhya-abc-paulista)

**Versão:** 1.1  
**Atualizado em:** 10/02/2026  
**Objetivo:** servir como **launcher operacional** da **Blitz NPS mensal**, centralizando o **texto oficial** e preparando disparos por **Gmail** e **WhatsApp Web** com o mínimo de esforço — **sem enviar nada automaticamente** (você sempre revisa e confirma).

> Projeto **100% front-end** (HTML/CSS/JS puro). Ideal para **GitHub Pages**.

---

## 🌐 O que este projeto entrega

- **Texto padrão da Blitz** já preenchido (editável).
- Botão para **copiar** a mensagem.
- **Disparo por Gmail (compose pronto)**:
  - Abre o Gmail com **Para**, **CCO**, **Assunto** e **Corpo** preenchidos;
  - Ferramentas para **numerar**, **remover duplicados** e exibir **estatística** da lista;
  - **Abertura em lotes** quando ultrapassar o limite (painel com “próximos e-mails”).
- **Disparo por WhatsApp (links wa.me)**:
  - Gera um link por telefone com a mensagem pronta (abre em nova aba).
- **Mini fluxos / gatilhos (SenseData)**:
  - Acordeões com modais de roteiros e checklists (Monitoramento NPS e Detratores).
- Card de **backup/conferência** da tela **CS - NPS** (caminho + ID).

---

## ✅ Regras e comportamentos importantes (como a página funciona)

### Gmail (corporativo)
- O compose é aberto “ancorado” no Gmail corporativo via `authuser`:
  - Conta configurada no código: `gustavo.germano@sankhya.com.br`
- **Para:** fixo no seu e-mail corporativo  
- **CCO:** lista de clientes
- **Limite por disparo:** a página considera política de **50 destinatários** e, por segurança, abre com **49 no CCO** (deixando seu e-mail em “Para”).
- Se a lista tiver mais que o limite:
  - abre o **1º lote**
  - mostra o restante no painel **“Próximos e-mails”** (com botões para copiar/aplicar/restaurar)

> Observação: a página **não envia** e-mail. Ela apenas abre o Gmail pronto para revisar, anexar `NPS_Blitz.jpg` e clicar em **Enviar**.

### WhatsApp
- Telefones devem conter **DDI + DDD + número** (um por linha).
- A página remove caracteres não numéricos e gera links:
  - `https://wa.me/<telefone>?text=<mensagem_codificada>`

> Observação: a página **não envia** mensagens. Ela apenas abre as conversas no WhatsApp Web com o texto pronto.

---

## 🧭 Fluxo operacional (passo a passo)

### 1) Ajustar a mensagem
- Edite o campo **“Texto padrão da Blitz”** se precisar (pequenos ajustes de tom, contexto, etc.).
- Use **“Copiar texto da Blitz”** quando quiser colar manualmente em outro canal.

### 2) Disparo por e-mail (Gmail)
1. Cole os e-mails dos clientes em **“Lista de e-mails (um por linha)”**
2. (Opcional) Use:
   - **Numerar lista**
   - **Remover duplicados**
3. Ajuste o **Assunto** se necessário
4. Clique em **“Abrir Gmail com a Blitz”**
5. No Gmail:
   - revise o texto
   - **anexe `NPS_Blitz.jpg`**
   - clique em **Enviar**
6. Se aparecer o painel de lotes:
   - clique em **Aplicar próximos e-mails**
   - repita o disparo do próximo lote

### 3) Disparo via WhatsApp
1. Cole os telefones em **“Telefones (com DDI/DDD, um por linha)”**
2. Clique em **“Gerar links de envio”**
3. Abra cada link e envie no WhatsApp Web (após revisar)

### 4) Mini fluxos (SenseData)
Use os botões para abrir roteiros e checklists (modais) de:
- **Monitoramento NPS — Plano de Ação** (síntese/forecast)
- **Fechamento de Loop NPS Detratores**
  - Entendimento do cenário e contato inicial
  - Montagem e execução do plano
  - Plano com colaboração de outras áreas
  - Follow-up pós plano de ação

---

## 🧾 Backup / conferência (Sankhya)
Caso precise confirmar dados:
- **Caminho:** `Dashboards » Customer Success » CS - NPS`
- **ID:** `br.com.sankhya.menu.adicional.nuDsb.1431.1`

---

## 🧱 Estrutura do projeto

```text
/ (raiz do repositório)
├── index.html      # página única com layout + lógica (Gmail/WhatsApp) + modais
├── NPS_Blitz.jpg   # arte da Blitz (preview na tela + anexo no e-mail)
└── README.md
