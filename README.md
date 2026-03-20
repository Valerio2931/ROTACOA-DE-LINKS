# 🔀 Link Rotator

Um único link encurtado que rotaciona entre vários destinos a cada clique.

## Como funciona

Você publica **dois arquivos** no GitHub Pages:

| Arquivo | Função |
|---|---|
| `index.html` | O link que você compartilha. Redireciona automaticamente. |
| `admin.html` | Painel visual para gerenciar os links (só você usa). |

---

## Passo a passo — Deploy no GitHub Pages

### 1. Crie o repositório
- Acesse [github.com/new](https://github.com/new)
- Nome sugerido: `links` ou `r` (quanto menor, mais curto a URL)
- Deixe **público**
- Clique em **Create repository**

### 2. Faça upload dos arquivos
- Clique em **Add file → Upload files**
- Arraste `index.html` e `admin.html`
- Clique em **Commit changes**

### 3. Ative o GitHub Pages
- Vá em **Settings → Pages**
- Em "Source", selecione: **Deploy from a branch**
- Branch: `main` / pasta: `/ (root)`
- Clique em **Save**

### 4. Aguarde ~1 minuto
Seu link estará disponível em:
```
https://SEU_USUARIO.github.io/NOME_DO_REPO/
```

---

## Configurando seus links

### Opção A — Pelo painel visual (recomendado)
1. Acesse `https://SEU_USUARIO.github.io/NOME_DO_REPO/admin.html`
2. Adicione seus links e escolha o modo
3. Clique em **"Baixar index.html pronto"**
4. Substitua o `index.html` no repositório pelo baixado

### Opção B — Editando o código direto
Abra o `index.html` e edite o bloco de configuração:

```javascript
const LINKS = [
  "https://link1.com",
  "https://link2.com",
  "https://link3.com",
  // ... até onde quiser
];

const MODE = "sequential"; // "sequential" ou "random"
```

---

## Modos de rotação

| Modo | Comportamento |
|---|---|
| `sequential` | Cada clique vai para o próximo link na ordem (1→2→3→1…) |
| `random` | Cada clique escolhe um link aleatório |

---

## Encurtando a URL

A URL do GitHub Pages já é relativamente curta. Para deixar ainda menor, use serviços gratuitos:

- **[Bitly](https://bitly.com)** — bit.ly/seulink
- **[TinyURL](https://tinyurl.com)** — tinyurl.com/seulink
- **[Short.io](https://short.io)** — com domínio próprio

Você aponta o encurtador para:
```
https://SEU_USUARIO.github.io/NOME_DO_REPO/
```

---

## Limitações importantes

- O modo **sequencial** usa `localStorage` do navegador. Isso significa que o contador é **por dispositivo/navegador** — cada pessoa que clicar começa do índice 0 no próprio dispositivo.
- Para um rotador verdadeiramente global (um contador compartilhado entre todos os cliques), seria necessário um backend (ex: Cloudflare Workers, Supabase). O GitHub Pages é estático.
- Se precisar de **distribuição equilibrada entre usuários diferentes**, use o modo `random`.

---

## Estrutura dos arquivos

```
seu-repo/
├── index.html   ← link que você compartilha
└── admin.html   ← painel de gerenciamento
```
