# Fluxo NPS — CS/CX — Sankhya ABC Paulista

**Versão:** 2.1  
**Objetivo:** centralizar a rotina mensal de NPS da unidade, incluindo consulta da base, leitura automática da planilha de contatos, envio assistido da Blitz por Gmail/WhatsApp, acompanhamento no INDECX, tratativa de playbooks e apoio ao GPD.

> Projeto 100% front-end para GitHub Pages. A página prepara listas e disparos para revisão manual; ela não envia e-mails ou WhatsApps automaticamente em segundo plano.

---

## O que este projeto entrega

- Acesso rápido ao **INDECX**.
- Orientação da tela **CS - NPS** no Sankhya.
- Mapeamento do quadrante **CS - Pesquisas NPS**.
- Leitura automática da planilha **Tabela para envio de email aos clientes.xlsx**.
- Filtro automático por **RESPONDE NPS = SIM**.
- Preenchimento automático da lista de e-mails.
- Preenchimento automático da lista de telefones.
- Disparo assistido por Gmail com controle de lotes.
- Geração de links de WhatsApp Web.
- Roteiro de playbooks para neutros e detratores.
- Modelo de preenchimento para **Apuração do Resultado / GPD**.

---

## Arquivos do repositório

```text
/
├── index.html
├── Tabela para envio de email aos clientes.xlsx
├── NPS_Blitz.jpg
└── README.md
```

> Importante: para a busca automática funcionar no GitHub Pages, o arquivo `Tabela para envio de email aos clientes.xlsx` deve estar na mesma pasta do `index.html`.

---

## Planilha de contatos NPS

### Colunas esperadas

A planilha deve conter, no mínimo:

| Coluna | Obrigatória | Uso |
|---|---:|---|
| CLIENTE | Sim | Nome da empresa/cliente |
| NOME CONTATO | Sim | Nome do contato |
| EMAIL | Sim | E-mail usado no disparo da Blitz |
| TELEFONE | Sim | Telefone usado para WhatsApp |
| RESPONDE NPS | Sim | Filtro principal: somente `Sim` entra na lista |
| CARGO | Não | Informação complementar, se existir |

### Regra de filtro

A tela considera apenas linhas onde:

```text
RESPONDE NPS = Sim
```

A partir disso, ela separa automaticamente:

- e-mails para o campo **Lista de e-mails**;
- telefones para o campo **Telefones do WhatsApp**.

---

## Como funciona a busca automática

Ao clicar nos botões de preenchimento, a página tenta buscar nesta ordem:

1. `Tabela para envio de email aos clientes.xlsx` no próprio GitHub Pages;
2. variações de nome do arquivo no mesmo repositório;
3. exportação XLSX/CSV da planilha online do Google Sheets, se estiver pública/exportável.

A fonte mais estável é o `.xlsx` publicado junto com o site no GitHub Pages.

---

## Botões principais

### Base de Contatos NPS

- **Buscar planilha e preencher e-mails + telefones**  
  Busca o arquivo automaticamente e preenche os dois campos.

- **Buscar e preencher somente e-mails**  
  Busca o arquivo automaticamente e preenche apenas a lista de e-mails.

- **Buscar e preencher somente telefones**  
  Busca o arquivo automaticamente e preenche apenas a lista de telefones.

- **Processar contatos NPS**  
  Usado como reserva manual quando os dados forem colados no campo de importação.

### Gmail

- **Buscar planilha e preencher e-mails**
- **Numerar lista**
- **Remover duplicados**
- **Abrir Gmail com a Blitz**

### WhatsApp

- **Buscar planilha e preencher telefones**
- **Gerar links de envio**

---

## Limites e observações técnicas

- O GitHub Pages é estático.
- A tela consegue ler um `.xlsx` público hospedado no mesmo repositório.
- A leitura direta da planilha online depende das permissões/CORS do Google.
- O envio por Gmail continua assistido: a tela abre o compose pronto, mas o clique final em **Enviar** é manual.
- O envio por WhatsApp continua manual por links `wa.me`.
- Para envio automático mensal por e-mail, usar **Google Apps Script** na própria planilha.

---

## Rotina mensal sugerida

1. Acessar **CS - NPS**.
2. Conferir o quadrante **CS - Pesquisas NPS**.
3. Validar a base mensal de clientes aptos.
4. Abrir o **Fluxo NPS**.
5. Clicar em **Buscar planilha e preencher e-mails + telefones**.
6. Conferir estatística dos contatos com **RESPONDE NPS = SIM**.
7. Revisar a mensagem da Blitz.
8. Abrir Gmail com a Blitz.
9. Anexar `NPS_Blitz.jpg`.
10. Enviar os lotes necessários.
11. Gerar links de WhatsApp e enviar manualmente.
12. Acompanhar retornos no INDECX.
13. Tratar playbooks de neutros e detratores.
14. Preencher GPD quando solicitado.

---

## Links principais

- **INDECX:** https://v3.app-indecx.com/live-dash/687b07ebc9bc6a00278be59e
- **Planilha de contatos:** https://docs.google.com/spreadsheets/d/1h1OVkdOMMCKP_KBGaKdw4Je-TA5gFJX2/edit?gid=168915867#gid=168915867
- **CS - NPS:** `Dashboards » Customer Success » CS - NPS`
- **ID CS - NPS:** `br.com.sankhya.menu.adicional.nuDsb.1431.1`
- **CS - Gestão de Sucesso do Cliente:** `Analytics AI » Sucesso do Cliente » CS - Resultados » CS - Gestão de Sucesso do Cliente`
- **ID CS - Gestão de Sucesso do Cliente:** `br.com.sankhya.analytics2.new.sc.t_20293.10.130`
- **Apuração do Resultado:** `Gestão Estratégica » Apuração do Resultado`
- **ID Apuração do Resultado:** `br.com.sankhya.apuracao.resultado`
