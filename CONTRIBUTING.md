# Como contribuir

Qualquer órgão, município, empresa ou grupo de pesquisa pode incluir um módulo, uma implantação ou um artigo no diretório. Basta abrir um pull request.

## Critérios de inclusão de módulos

1. **Software livre**: licença compatível com a AGPL-3.0 do Decidim, em repositório público.
2. **Compatibilidade declarada**: faixa de versões do Decidim no gemspec, testada na versão listada.
3. **Sem fork do core**: estender por engine, `prepend`, `to_prepare` ou content blocks.
4. **Documentação e testes**: README com instalação e configuração; testes em CI.
5. **pt-BR**: textos de interface traduzidos para pt-BR (e, de preferência, inglês).
6. **Upstream**: indicar o que pode ser proposto ao Decidim no [Metadecidim](https://meta.decidim.org).

## Onde editar

| Arquivo | Conteúdo |
| --- | --- |
| `data/modules.json` | Módulos (gems) |
| `data/instances.json` | Implantações do Decidim no Brasil |
| `data/papers.json` | Artigos e pesquisas |

Textos visíveis ao público têm versão em português, inglês e espanhol: `{ "pt": "…", "en": "…", "es": "…" }`. Se faltar o espanhol, a página usa o português.

### Campos de um módulo

| Campo | Obrigatório | Descrição |
| --- | --- | --- |
| `id` | sim | Identificador único, normalmente o nome da gem |
| `name` | sim | Nome exibido |
| `category` | sim | `component`, `extension`, `channel`, `admin`, `identity` ou `platform` |
| `tagline` | sim | Frase de até ~6 palavras exibida no cartão `{ pt, en, es }` |
| `summary` | sim | Descrição curta `{ pt, en, es }` |
| `features` | não | Lista de funcionalidades `[{ pt, en, es }]` |
| `decidim` | sim | Restrição de versão do Decidim, como no gemspec (`~> 0.32.1`) |
| `version` | não | Versão da gem |
| `license` | sim | Identificador SPDX |
| `maintainer` | sim | Organização ou pessoa responsável |
| `repo` / `repo_label` | sim | URL do repositório e texto do link |
| `branch` | não | Branch recomendado para a versão listada |
| `docs` | não | Site de documentação |
| `tests` | não | `true` se há suíte de testes |
| `upstream` | não | `true` se tem funcionalidade candidata a upstream |
| `papers` | não | `id`s de `papers.json` |
| `used_by` | não | `id`s de `instances.json` |

### Campos de uma implantação

| Campo | Obrigatório | Descrição |
| --- | --- | --- |
| `id`, `name`, `url` | sim | Identificador, nome e endereço da plataforma |
| `place` | sim | Território `{ pt, en, es }`, como `Belém · PA` |
| `level` | sim | `federal`, `state`, `municipal`, `academic` ou `civil` |
| `status` | sim | `active` ou `unverified` |
| `since` | não | Ano de lançamento |
| `summary` | sim | Descrição curta `{ pt, en, es }` |
| `maintainer` | sim | Quem opera e quem dá suporte técnico |
| `decidim`, `repo` | não | Versão do Decidim e repositório, se públicos |
| `sources` | sim | Links públicos que comprovam as informações |

## Testar localmente

A página carrega os JSON com `fetch`, então precisa ser servida por HTTP:

```bash
python3 -m http.server 8000
# abra http://localhost:8000
```
