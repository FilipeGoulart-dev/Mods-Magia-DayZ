# 🧙 Mods-Magia-DayZ

[![GitHub Pages](https://img.shields.io/badge/guia-online-10b981?style=flat-square)](https://filipegoulart-dev.github.io/Mods-Magia-DayZ/)
[![DayZ 1.29+](https://img.shields.io/badge/DayZ-1.29%2B-65a30d?style=flat-square)](https://dayz.com/)
[![Single-file](https://img.shields.io/badge/site-index.html%20%C3%BAnico-a855f7?style=flat-square)](#estrutura-do-reposit%C3%B3rio)

Guia interativo de **mods de magia, feitiços e alquimia para servidores DayZ PvE**.
Reúne uma curadoria de 12 mods da Steam Workshop com análise voltada para PvE
(zumbis, hordas, IA, cura em grupo, mapas medievais) e uma ferramenta para
montar e exportar o *pack* de mods do seu servidor.

> 🔗 **Acesse o guia:** <https://filipegoulart-dev.github.io/Mods-Magia-DayZ/>

---

## 📖 Sobre o projeto

O site é um **arquivo único** (`index.html`) com HTML, CSS e JavaScript embutidos —
sem build, sem dependências, sem framework e sem CDN. As imagens dos mods estão
embutidas em base64 (WebP), então o guia funciona **offline**: basta abrir o arquivo
no navegador. O deploy é feito automaticamente pelo GitHub Pages a cada push na `main`.

### O que o guia oferece

| Recurso | Descrição |
| --- | --- |
| 🎛️ **Curadoria por categoria** | Filtros: `⭐ Melhores para PvE (6)`, `🛠️ Utilitários & Trader (2)`, `🗺️ Mapas Medievais (2)` e `⚠️ Evitar / Desatualizados (2)` |
| 🔍 **Busca instantânea** | Procura em nome, descrição, elemento, ID da Workshop, tags e análise PvE |
| 🛡️ **Análise PvE por mod** | Pontuação PvE, público-alvo (zumbis, IA, co-op) e destaques de cada mod |
| 🖼️ **Imagem local + oficial** | Botão para alternar entre a imagem embutida e a imagem original da Steam |
| 📋 **Copiar ID / link** | Copia com um clique o Workshop ID ou o link do mod para colar no seu servidor |
| ➕ **Montar o pack do servidor** | Marca mods com `+ Pack` e gera um resumo pronto para o admin |
| ⭐ **Combo recomendado** | Seleciona automaticamente a combinação sugerida (6 mods essenciais) |
| ✨ **Ambiente temático** | HUD estilo DayZ (mana, HP, sangue), partículas arcanas em canvas e efeitos ao clicar nos cards |

> ℹ️ A seleção do pack fica **em memória**: recarregar a página limpa a seleção
> (o projeto não usa `localStorage`). Use o botão de copiar do painel de exportação
> para guardar o resultado.

---

## 📁 Estrutura do repositório

```text
Mods-Magia-DayZ/
├── index.html                              # 🌐 O site inteiro (HTML + CSS + JS + imagens)
├── assets/
│   └── audio/
│       └── narnia-lullaby-extended.mp3     # 🎵 Áudio de apoio (não usado pelo site hoje)
├── .gitattributes                          # Normalização de LF + arquivos binários
├── .gitignore                              # Lixo de SO, editores, builds, segredos
├── .nojekyll                               # Impede o Jekyll de processar o site no Pages
└── README.md
```

> ⚠️ **`index.html` deve continuar na raiz.** O GitHub Pages está configurado para
> publicar a branch `main`, pasta `/`. Se mover o arquivo, ajuste também
> *Settings → Pages* ou o site sai do ar.

---

## 🚀 Como usar

### Ver o guia online

Acesse <https://filipegoulart-dev.github.io/Mods-Magia-DayZ/>.

### Rodar localmente

Como é um arquivo estático, você pode simplesmente abrir `index.html` no navegador.
Para servir via HTTP (recomendado, igual ao ambiente de produção):

```bash
# na raiz do repositório
python3 -m http.server 8000
# depois abra http://localhost:8000
```

---

## ✏️ Como adicionar ou editar um mod

Todos os dados ficam no array `const MODS = [...]` **dentro do `index.html`**
(por volta da linha 1044). Não existe banco de dados nem arquivo de configuração
externo: o conteúdo é o próprio código do site.

Cada item do array segue este formato:

```js
{
  "id":            "3703543669",                     // Workshop ID (aparece no link da Steam)
  "name":          "Nome do mod",
  "author":        "Autor / Comunidade",
  "category":      "essencial",                       // essencial | utilitario | mapa | evitar
  "tier_badge":    "🏆 TOP #1 — Essencial PvE",       // selo exibido no card
  "tier_color":    "purple",                          // purple | gold | emerald | cyan | red
  "pve_score":     "10/10 para PvE & Co-op",
  "size":          "56.3 MB",
  "updated":       "Compatível 1.29+",
  "url":           "https://steamcommunity.com/sharedfiles/filedetails/?id=3703543669",
  "img_main":      "data:image/webp;base64,...",      // imagem embutida (ou URL)
  "img_alt":       "data:image/webp;base64,...",      // 2ª imagem; se igual a img_main, o botão de alternar não aparece
  "img_steam_url": "https://images.steamusercontent.com/...",
  "element":       "Arcano / Necromancia / Elemental",
  "short_desc":    "Resumo do que o mod faz.",
  "pve_highlights": [
    "Ponto forte 1 para PvE.",
    "Ponto forte 2 para PvE."
  ],
  "tags": ["Barra de Mana (GUI)", "Necromancia vs Zumbis"],
  "SelectedDefault": true                             // true = já entra no combo recomendado
}
```

Depois de editar, recarregue a página: a lista, os filtros e as contagens são
gerados automaticamente a partir desse array.

---

## 🗂️ Curadoria atual

| Mod | Categoria | Workshop ID | Tamanho |
| --- | --- | --- | --- |
| Admirals Magik Mod 1.29+ | essencial | `3703543669` | 56.3 MB |
| Arcane Arsenal | essencial | `3704076180` | 186.7 MB |
| TB Herblore | essencial | `3797454932` | 14.6 MB |
| Swamp Witch Apothecary | essencial | `3565317966` | 215.7 MB |
| SLiiPS_ELiiXARS: Ancient Alchemy | essencial | `3647730817` | 2.99 MB |
| Staff of Light | essencial | `3746125419` | 16.8 MB |
| SpellbookOfVehicles | utilitario | `3751599846` | 1.2 MB |
| Book Magic | utilitario | `3626785209` | 1.85 MB |
| Camelot - Medieval Map (Bônus) | mapa | `3393881067` | Mapa customizado |
| Heavens Hollow: The Forgotten Realm (Bônus) | mapa | `3577983663` | 3.82 GB |
| Admirals Magik Mod (versão antiga) | ⚠️ evitar | `2885717278` | 36.5 MB |
| Dark Medieval Age (DMA) | ⚠️ evitar | `2306387035` | 5.52 GB |

---

## 🎵 Sobre o arquivo de áudio

`assets/audio/narnia-lullaby-extended.mp3` (~9,2 MB, ~10 min, 128 kbps) está no
repositório como material de apoio, mas **não é referenciado pelo site** hoje — o
`index.html` não carrega nenhum áudio. Se ele não for ser usado (por exemplo, como
música de fundo), remova-o para deixar o clone bem mais leve:

```bash
git rm assets/audio/narnia-lullaby-extended.mp3
```

---

## ☁️ Deploy (GitHub Pages)

1. O deploy é automático: qualquer push na branch `main` republica o site.
2. Configuração atual: *Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`*.
3. Como o site é um arquivo estático único, não há etapa de build nem dependências.

---

## 🤝 Contribuindo

- **Correção de dados** (ID, tamanho, compatibilidade de versão, mod quebrado): abra
  uma *issue* ou envie um *pull request* editando o array `MODS` no `index.html`.
- **Novo mod sugerido:** informe nome, link da Workshop, categoria e por que ele é
  bom (ou ruim) para PvE.
- Mantenha o padrão de um commit por assunto, com mensagem curta e descritiva.

---

## ⚖️ Aviso legal

Projeto **não oficial**, sem vínculo com a Bohemia Interactive ou com os autores dos
mods. *DayZ* é marca da Bohemia Interactive; todos os mods listados pertencem aos seus
respectivos criadores e são distribuídos pela Steam Workshop. O guia apenas reúne
links, IDs e análises de uso em servidores PvE.
