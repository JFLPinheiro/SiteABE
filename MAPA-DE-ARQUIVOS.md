# Mapa de arquivos — Araújo Brasílio Equipamentos de Segurança

Data: 09/11/2026
Versão da documentação: 0.1.3
Último registro anterior informado: 0.1.2 — 09/11/2026
Escopo: documentação da estrutura; nenhuma alteração no funcionamento do site.

## 1. Estrutura adotada
Esta é a estrutura padrão aprovada pelo usuário para a pasta local e para o GitHub. A correspondência do GitHub foi informada pelo usuário e mostrada em captura; não houve auditoria remota nesta entrega. Preservar nomes e caminhos nas próximas alterações.

```text
/
├── dados/
│   └── produtos.json
├── img/
│   ├── logo-original.jpg
│   ├── logo.webp
│   ├── altura.svg
│   ├── auditiva.svg
│   ├── calcado.svg
│   ├── capacete.svg
│   ├── luva.svg
│   ├── oculos.svg
│   ├── respirador.svg
│   └── vestimenta.svg
├── js/
│   └── config.js
├── produtos/
│   ├── altura.html
│   ├── auditiva.html
│   ├── calcado.html
│   ├── capacete.html
│   ├── luva.html
│   ├── oculos.html
│   ├── respirador.html
│   └── vestimenta.html
├── versoes/
│   ├── 2026-11-02-v0.1.0.md
│   └── 2026-11-09-v0.1.2.md
├── CHANGELOG.md
├── DECISOES-DO-PROJETO.md
├── index.html
├── README.md
├── robots.txt
└── MAPA-DE-ARQUIVOS.md       ← adicionar este documento na raiz
```

Os nomes internos foram mapeados pelo inventário disponível nas Fontes e pela estrutura documentada do pacote. As capturas mostram as pastas da raiz, não uma verificação de cada arquivo interno do GitHub. O logo adicional logo-arujobrasilioequipamentps.jpeg nas Fontes é referência original do projeto; não inserir um novo caminho no site sem conferir as referências.

## 2. Onde alterar cada informação

| Caminho | Conteúdo e finalidade |
|---|---|
| index.html | Página principal, navegação, banner, categorias, cartões, seções institucionais e contato; nesta implementação também contém CSS e a lógica principal de JavaScript. |
| js/config.js | window.SITE_CONFIG: WhatsApp, telefone, e-mail, endereço, horários, cidade, UF, domínio e modo demonstrativo. |
| dados/produtos.json | Referência editorial dos produtos: IDs, nomes, categorias, referências, unidades, variações e campos técnicos. Não atualiza automaticamente a página. |
| produtos/*.html | Páginas próprias dos oito exemplos, com descrição e informações essenciais em HTML. |
| img/logo.webp | Cópia recortada e otimizada do logotipo. Conferir uso antes de substituir: a página principal também utiliza imagens embutidas. |
| img/logo-original.jpg | Captura original preservada para referência e recuperação. |
| img/*.svg | Ilustrações genéricas dos exemplos, não fotografias de produtos reais. |
| versoes/*.md | Registros datados de entregas. Não substituem os arquivos executáveis nem constituem backup completo do site. |
| CHANGELOG.md | Histórico consolidado: data, versão, alterações, motivo, impacto, testes e reversão. |
| DECISOES-DO-PROJETO.md | Padrões aprovados, limitações e decisões que devem orientar futuras edições. |
| README.md | Edição, testes locais, publicação, backup, reversão e pendências. |
| robots.txt | Diretivas para rastreadores. No protótipo, bloqueia rastreamento; não é controle de acesso. |
| MAPA-DE-ARQUIVOS.md | Este mapa e as regras de localização e manutenção dos arquivos. |

## 3. Dependências importantes
- Usar index.html da estrutura completa como entrada principal. Não alternar com o HTML avulso antigo, que possui configuração embutida.
- O pacote utiliza js/config.js. O campo whatsapp deve conter código 55, DDD e número, somente dígitos. Último valor fornecido: 5519989470259. Configuração não prova conta ativa nem teste concluído.
- Manter modoDemonstracao: true até a revisão dos produtos e das informações comerciais.
- Não presumir que todo campo de configuração altera automaticamente todos os textos, metadados e dados estruturados.
- Mudanças de produto precisam ser sincronizadas entre dados/produtos.json, window.CATALOG, cartões e categorias de index.html e a página correspondente em produtos/.
- Imagens também podem estar embutidas no HTML e no índice do catálogo. Substituir um arquivo em img/ pode não atualizar todas as aparições. Conferir referências externas e embutidas.
- Não criar css/ ou dividir scripts apenas para adaptar uma estrutura recomendada: a estrutura acima é o padrão atual. Qualquer reorganização precisa de plano, atualização das referências e registro.
- Preservar IDs e URLs dos produtos, inclusive no planejamento futuro de WordPress.

## 4. Fontes do projeto, pasta local e GitHub
- No computador e no repositório, manter exatamente as pastas e os nomes originais.
- Nas Fontes deste projeto, os arquivos podem aparecer avulsos com seus nomes originais. Usar este mapa para identificar a pasta de cada um.
- Nesta estrutura, .html de produto corresponde a produtos/ e .svg corresponde a img/; config.js corresponde a js/ e produtos.json a dados/.
- Não é necessário renomear os arquivos atuais com prefixos. Se surgirem arquivos homônimos em pastas diferentes, registrar o caminho explicitamente e combinar uma convenção antes de enviar.
- Antes de editar, consultar este mapa, o changelog, as decisões e os arquivos atuais disponíveis.
- Se GitHub, Fontes e cópia local divergirem, pedir confirmação sobre qual versão usar. Não presumir que o número da versão no documento comprova sincronização dos arquivos.
- Acesso ao repositório ou aos arquivos locais não é automático; consultar as ferramentas disponíveis e pedir o arquivo se estiver indisponível.
- Não afirmar gravação nas Fontes, GitHub ou hospedagem sem realizar e confirmar a operação. Escritas remotas exigem aprovação.

## 5. Procedimento para cada alteração
1. Identificar versão de partida e arquivos afetados.
2. Fazer backup ou preservar commit anterior.
3. Aplicar somente as mudanças solicitadas.
4. Atualizar CHANGELOG.md e o registro datado de versão.
5. Atualizar DECISOES-DO-PROJETO.md se houver mudança de padrão.
6. Atualizar este mapa se houver inclusão, remoção ou movimentação de arquivos.
7. Testar navegação, catálogo, detalhes, orçamento, WhatsApp e layout móvel conforme os arquivos afetados.
8. Salvar a atualização no projeto e sincronizar com o GitHub após revisão.
9. Registrar o que foi testado e o que permanece pendente.

## 6. Registro desta entrega — 0.1.3
### Adicionado
- MAPA-DE-ARQUIVOS.md na raiz, documentando a estrutura adotada e as responsabilidades dos arquivos.
### Motivo
- Evitar perda de contexto quando os arquivos forem enviados avulsos às Fontes e manter consistência entre pasta local e GitHub.
### Impacto
- Somente documentação; sem alteração em HTML, configurações, catálogo, imagens ou publicação.
### Aplicação
- Salvar este arquivo ao lado de index.html, CHANGELOG.md e README.md.
- Adicionar uma cópia às Fontes para consulta futura.
- Acrescentar ao CHANGELOG.md uma entrada datada de 09/11/2026, versão 0.1.3, resumindo este registro.
- Acrescentar à DECISOES-DO-PROJETO.md: “09/11/2026 — Estrutura atual aprovada como padrão; consultar MAPA-DE-ARQUIVOS.md antes de reorganizar arquivos.”
### Teste
- Conferir se os caminhos deste mapa correspondem à cópia local e ao repositório; verificar links caso haja divergência.
### Reversão
- Remover este documento e reverter as respectivas entradas documentais, sem modificar o site.
### Limite da entrega
- Arquivo gerado para download. Nenhuma alteração automática nas Fontes ou no GitHub; teste remoto não realizado.

Salve esta atualização no projeto e faça backup antes de publicar, se aplicável.
