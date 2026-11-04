---
name: manter-design
description: Mantém o design system verdadeiro — tokens, componentes base, estados e padrões visuais. Use quando token, componente, tema ou layout base mudar, ou quando uma tela nova precisar seguir o padrão existente.
---

# Manter design

Documento alvo: `DESIGN.md` na raiz do repo. É o arquivo que `impeccable-plan` (`document`) escreve e que a skill `impeccable` lê, junto com `PRODUCT.md` na mesma raiz. Se o projeto tiver um arquivo de tokens, ele continua sendo a fonte dos valores; `DESIGN.md` aponta para lá. Não crie um segundo design doc, inclusive `docs/DESIGN.md`.

`PRODUCT.md` é contexto de produto da superfície, também na raiz, escrito por `impeccable-plan` (`init`). Não copie regra de domínio para cá. Isso é `manter-produto`, no `docs/PRODUTO.md`. Os dois arquivos não se copiam.

## O que o DESIGN.md precisa ter

1. Tokens reais: cor, espaçamento, raio, tipografia, com os valores que estão no código.
2. Componentes base: nome, caminho, variantes, estados (`hover`, `focus`, `disabled`, `loading`, `empty`, `error`).
3. Padrões de layout: largura de conteúdo, breakpoints, comportamento mobile.
4. O modo das superfícies que o projeto distingue: Persuade, Operate, Read ou Experience. Um produto pode ter mais de um.
5. O que é proibido: cor solta no componente, `!important`, estilo inline para layout.

Achado de `impeccable-detect` não entra como token. Ou o valor está no código, ou é `DIVERGE`.

## Verificação

```bash
grep -rn "\-\-[a-z-]*:" src/*.css src/**/*.css 2>/dev/null | head -40
cat tailwind.config.* 2>/dev/null | head -60
ls src/components 2>/dev/null
```

Valor no documento que não existe no token ou no componente é `DIVERGE`.

## Componente sem estado documentado

Estado que não está no documento é o que quebra na mão do usuário: botão sem `disabled`, lista sem `empty`, formulário sem `error`. Se o componente não implementa o estado, registre como lacuna em vez de descrever o que deveria ser.

## Não faça

- Não invente token que o projeto não tem.
- Não descreva tela inteira; descreva padrão.
- Não troque valor no documento para "ficar bonito"; o código manda.
