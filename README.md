# LP Tratamento de Ar Comprimido e Rede de Ar Comprimido — Vazão Engenharia

Landing page de produto e serviço da **Vazão Engenharia e Montagem** para indústrias de Pernambuco e Ceará.
Recebe o tráfego dos grupos **NOVO 1 — Tubulação de Ar** e **NOVO 2 — Tratamento de Ar** da campanha *[PES] Compressores - Nova* (Google Ads).
Palavras-chave principais: **tratamento de ar comprimido** + **rede de ar comprimido** (as duas no H1 e no título da aba).

Regras de texto: Parker aparece só como "soluções Parker" (nunca distribuidor, revenda, representante ou autorizado). Ingersoll Rand pode ser chamada de distribuidor. SimplAir usa os números do fabricante.

## Estrutura

- `index.html`: página única e autocontida (HTML, CSS e JS inline), mesma identidade visual da LP NR13 e do site da Vazão.
- Seções: topo com chat · linhas de produto (carrossel) · vitrine com abas Parker / Ingersoll Rand (23 itens) · sistema de tratamento (fluxo do ar + refrigeração × adsorção) · etapas do atendimento + dados para a cotação · diferenciais · perguntas frequentes · banner · formulário de cotação.
- O botão "Solicitar cotação" de cada produto já preenche **Interesse** e **Produto** no formulário.

## Imagens (`assets/`)

Todas entram **sozinhas** quando o arquivo for adicionado com o nome exato. Até lá aparece um ícone no lugar.

| Arquivo | Onde aparece | Tamanho |
|---|---|---|
| `logo-vazao.webp` (já incluída) | topo e rodapé | 230×72 |
| `logo-parker.png` | aba Parker da vitrine | 400×160, fundo transparente |
| `logo-ingersoll-rand.png` | aba Ingersoll Rand da vitrine | 400×160, fundo transparente |
| `banner-topo.jpg` (já incluída) | foto do topo, atrás do chat | 1200×900 |
| `cta-fundo.jpg` (já incluída) | foto do banner azul | 800×724 |
| `linha-filtros-oil-x.jpg` (já incluída) | linha Filtros OIL-X | 800×600 |
| `linha-secadores-pse.jpg` (já incluída) | linha Secadores PSE | 800×600 |
| `linha-secadores-adsorcao.jpg` (já incluída) | linha CDAS HL e K-MT | 800×600 |
| `linha-tubulacao-simplair.jpg` (já incluída) | linha SimplAir | 800×600 |

Fotos da vitrine em `assets/produtos/`. As 8 da Parker já estão incluídas (imagens ilustrativas, 2:1 com fundo azul-claro). As da Ingersoll Rand: 800×600, produto recortado em fundo branco.

| Parker | Ingersoll Rand |
|---|---|
| `parker-filtro-coalescente-oil-x.jpg` | `ir-tubulacao-aluminio-simplair.jpg` |
| `parker-secador-refrigeracao-pse.jpg` | `ir-secadores-refrigeracao.jpg` |
| `parker-secador-adsorcao-cdas-hl.jpg` | `ir-separadores-polysep.jpg` |
| `parker-secador-adsorcao-k-mt.jpg` | `ir-dreno-liquidator.jpg` |
| `parker-elemento-coalescente.jpg` | `ir-drenos-eletronicos.jpg` |
| `parker-filtro-aco-carbono.jpg` | `ir-drenos-pnld-ii.jpg` |
| `parker-filtro-carvao-ativado.jpg` | `ir-filtros-coalescentes-aco-carbono.jpg` |
| `parker-filtro-alta-pressao.jpg` | `ir-filtros-coalescentes-serie-f.jpg` |
| | `ir-secador-adsorcao-sem-aquecimento.jpg` |
| | `ir-secador-adsorcao-hoc-1088.jpg` |
| | `ir-secador-adsorcao-hoc-1191.jpg` |
| | `ir-secador-adsorcao-4-226.jpg` |
| | `ir-secador-adsorcao-ventilador.jpg` |
| | `ir-secador-adsorcao-d-ila.jpg` |
| | `ir-secador-adsorcao-hl.jpg` |

## Configuração (bloco `CONFIG` no fim do `index.html`)

- `gtmId`: ID do Google Tag Manager. Vazio = não carrega.
- `leadEndpoint`: URL que recebe o lead (POST JSON). **Enquanto estiver vazio, o lead segue pelo WhatsApp da campanha (81) 99203-9379**, já com os dados preenchidos.
- `privacyUrl`: link da política de privacidade.

O lead leva junto UTMs, `gclid` e `keyword` da URL (guardados por 90 dias), além de campanha, grupo, interesse e produto.
Eventos no `dataLayer`: `cta_click` (com `produto`), `vitrine_aba`, `chat_start`, `generate_lead`.

## Pendências

- URL final: o canonical, o `robots.txt` e o `sitemap.xml` usam `vazao.b2marketingindustrial.com.br/tratamento-de-ar-comprimido/` como provisória.
- Link da política de privacidade, GTM e endpoint do lead.
- Fotos e logos listadas acima.

## Rodar localmente

```bash
python3 -m http.server 8000   # http://localhost:8000
```

## Deploy

Vercel, conectada a este repositório: todo push na `main` publica em produção.
