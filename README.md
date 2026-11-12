# LP Tratamento de Ar Comprimido e Rede de Ar Comprimido — Vazão Engenharia

Landing page de produto e serviço da **Vazão Engenharia e Montagem** para indústrias de todo o Nordeste.
Recebe o tráfego dos grupos **NOVO 1 — Tubulação de Ar** e **NOVO 2 — Tratamento de Ar** da campanha *[PES] Compressores - Nova* (Google Ads).
Palavras-chave principais: **tratamento de ar comprimido** + **rede de ar comprimido** (as duas no H1 e no título da aba).

Regras de texto: Parker aparece só como "soluções Parker" (nunca distribuidor, revenda, representante ou autorizado). Ingersoll Rand pode ser chamada de distribuidor. SimplAir usa os números do fabricante.

## Estrutura

- `index.html`: página única e autocontida (HTML, CSS e JS inline), mesma identidade visual da LP NR13 e do site da Vazão.
- Seções: topo com o shortcode do chat · vitrine Ingersoll Rand (20 itens) · sistema de tratamento (fluxo do ar + refrigeração × adsorção) · etapas do atendimento + dados para a cotação · diferenciais · perguntas frequentes · banner · cotação com o shortcode do formulário · rodapé em uma linha (padrão B2).
- Shortcodes do plugin de atendimento do WordPress: `[atendimento_chat id="default"]` na coluna de 300px do topo e `[atendimento_form id="default-form"]` na cotação. Fora do WordPress aparecem como texto cru.
- Todo CTA é `<button type="button" class="btn-slave-whats" data-cta="…">`: o plugin captura o clique e abre o formulário do WhatsApp. Não há formulário nem envio de lead na página.

## Imagens (`assets/`)

Todas entram **sozinhas** quando o arquivo for adicionado com o nome exato. Até lá aparece um ícone no lugar.

| Arquivo | Onde aparece | Tamanho |
|---|---|---|
| `logo-vazao.webp` (já incluída) | topo e rodapé | 230×72 |
| `logo-ingersoll-rand.png` (já incluída) | topo, ao lado do logo da Vazão | 476×100 |
| `hero-ir.webp` / `hero-ir.jpg` (já incluídas) | foto do topo (hero), à direita do texto | 1091×771 |
| `cta-fundo.jpg` (já incluída) | foto do banner azul | 800×724 |

Fotos da vitrine (Ingersoll Rand) em `assets/produtos/`: 800×400 (2:1), produto em fundo branco, recortadas dos prints do site da Vazão. Entram sozinhas quando o arquivo for adicionado com o nome exato.

| Produto | Arquivo |
|---|---|
| Tubulação alumínio SimplAir | `ir-tubulacao-aluminio-simplair.jpg` |
| Dreno sem perdas Liquidator | `ir-dreno-liquidator.jpg` |
| Drenos eletrônicos sem perda | `ir-drenos-eletronicos.jpg` |
| Drenos sem perda (PNLD II) | `ir-drenos-pnld-ii.jpg` |
| Filtros coalescentes aço carbono | `ir-filtros-coalescentes-aco-carbono.jpg` |
| Filtros coalescentes Série F | `ir-filtros-coalescentes-serie-f.jpg` |
| Secador por adsorção sem aquecimento | `ir-secador-adsorcao-sem-aquecimento.jpg` |
| Secador por adsorção (HOC) 1.088/23.703 m³/h | `ir-secador-adsorcao-hoc-1088.jpg` |
| Secador por adsorção (HOC) 1.191/24.119 m³/h | `ir-secador-adsorcao-hoc-1191.jpg` |
| Secador por adsorção 4,2 a 226 m³/min | `ir-secador-adsorcao-4-226.jpg` |
| Secador por adsorção com ventilador 4,2 a 226 m³/min | `ir-secador-adsorcao-ventilador.jpg` |
| Secador por adsorção D-ILA | `ir-secador-adsorcao-d-ila.jpg` |
| Secador por adsorção HL | `ir-secador-adsorcao-hl.jpg` |
| Secador por adsorção modular | `ir-secador-adsorcao-modular.jpg` |
| Secador por adsorção ponto de uso | `ir-secador-adsorcao-ponto-de-uso.jpg` |
| Secadores por adsorção HOC 420/3.680 m³/h | `ir-secadores-adsorcao-hoc-420.jpg` |
| Secadores por adsorção HLA | `ir-secadores-adsorcao-hla.jpg` |
| Secador por refrigeração 10–150 cfm | `ir-secador-refrigeracao-10-150-cfm.jpg` |
| Secadores por refrigeração 3.600 a 24.000 CFM | `ir-secadores-refrigeracao-3600-24000-cfm.jpg` |
| Secadores por refrigeração Nirvana | `ir-secadores-refrigeracao-nirvana.jpg` |

## Configuração (bloco `CONFIG` no fim do `index.html`)

- `gtmId`: ID do Google Tag Manager. Vazio = não carrega (no WordPress o GTM costuma vir do site).

Evento no `dataLayer`: `cta_click`, com `cta_local` (o `data-cta`) e `produto` quando o clique vem da vitrine (`linhas-<produto>`).
CTAs: `header-cta` · `hero-primary` · `hero-secondary` · `linhas-cta` · `linhas-<produto>` (20) · `sistema-cta` · `dados-cta` · `perguntas-cta` · `banner-cta` · `cotacao-whatsapp` · `mobile-cta`.

## Publicação

Push em `main` → GitHub Actions (`.github/workflows/build-wp.yml`) copia `index.html`, `assets/`, `robots.txt` e `sitemap.xml` para a raiz da branch órfã `wp-build` → o plugin B2 LP Publisher (WordPress) lê de lá. Não há build: a página é HTML puro com caminhos relativos.

## Pendências

- URL final: o canonical, o `robots.txt` e o `sitemap.xml` usam `vazao.b2marketingindustrial.com.br/tratamento-de-ar-comprimido/` como provisória.
- GTM (se não vier do WordPress).
- Fotos e logos listadas acima.

## Rodar localmente

```bash
python3 -m http.server 8000   # http://localhost:8000
```

## Deploy

Vercel, conectada a este repositório: todo push na `main` publica em produção.
