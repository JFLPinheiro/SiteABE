# CHANGELOG

## [2026-11-09] — Versão 0.1.4
### Adicionado
- 26 novos produtos no catálogo: máscara PFF2, botas, botinas, protetores auditivos, abafador, óculos, protetor facial, luvas, aventais, blusão, colete, mangote, perneira, toucas, cinta ergométrica e palmilha.
- Campo `imagem` nos produtos, com fotos representativas para calçados, luvas e proteção auditiva.
### Alterado
- `dados/produtos.json` atualizado com os novos itens.
- `index.html` deve receber os mesmos itens no `window.CATALOG` para exibição no catálogo.
### Motivo
- Ampliar o catálogo de EPIs disponíveis para consulta e orçamento.
### Impacto
- Aumenta o número de produtos exibidos no site; fotos provisórias permanecem nas categorias sem imagem própria.
### Próximos passos
- Substituir imagens provisórias por fotos reais de cada produto em `/img/`.
- Confirmar marcas, CA, tamanhos, referências e disponibilidade.
### Teste
- Abrir `index.html`, buscar por “bota”, “luva”, “protetor auditivo”, “avental” e “touca”.
- Conferir se os 26 novos produtos aparecem, abrem o detalhe e adicionam ao orçamento.
