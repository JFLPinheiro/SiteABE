# Araújo Brasílio Equipamentos de Segurança

Site institucional e comercial estático para apresentação de EPIs e preparação de orçamentos pelo WhatsApp, com preferência por retirada no local ou entrega sob consulta.

- Atualização deste README: 09/11/2026.
- Versão documental desta entrega: 0.1.4.
- Base funcional: implementação 0.1.0 e configuração de WhatsApp registrada em 0.1.2.
- Estrutura de referência: MAPA-DE-ARQUIVOS.md, documentação 0.1.3.
- Repositório: https://github.com/JFLPinheiro/SiteABE
- Endereço informado para testes publicados: https://jflpinheiro.github.io/SiteABE/

A atualização deste documento não altera o código do site nem comprova publicação ou teste funcional concluído. O GitHub Pages e a pasta local podem estar em estados diferentes; conferir antes de editar.

## 1. Estado atual e limites

O site está em demonstração. Existem oito exemplos de produtos, com nomes genéricos e ilustrações, não ofertas confirmadas. Manter `modoDemonstracao: true` até revisar o catálogo e os dados comerciais.

Funcionalidades previstas na implementação atual:
- Página principal com categorias, vitrine, apresentação institucional, contato, entrega e retirada.
- Busca por nome, categoria, marca e referência, conforme os dados cadastrados.
- Filtro de categoria e páginas HTML de detalhes.
- Lista de orçamento com inclusão, remoção e quantidades de 1 a 999.
- Escolha entre retirada no local e entrega.
- Cidade, CEP e observações opcionais para preparar a mensagem.
- Revisão e abertura do WhatsApp com o texto do orçamento.

Não há pagamento online, login, banco de dados, cálculo automático de frete, controle real de estoque, reserva de itens ou confirmação automática de pedido. Abrir o WhatsApp não envia a mensagem: o visitante precisa confirmar o envio no serviço.

O endereço, horários, contatos e demais dados fornecidos para teste precisam de confirmação comercial antes da publicação definitiva. A existência de um número configurado não comprova que a conta está ativa ou que o destinatário foi validado.

## 2. Estrutura padrão

Manter esta organização no computador e no GitHub. Não reorganizar pastas sem revisar referências e registrar a mudança.

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
├── MAPA-DE-ARQUIVOS.md
├── README.md
└── robots.txt
```

Novos registros datados poderão ser adicionados a `versoes/` a cada entrega. A árvore acima descreve os arquivos de referência, não afirma que novos registros já foram gravados.

### Responsabilidades

| Local | Responsabilidade |
|---|---|
| index.html | Página principal, CSS e lógica principal de JavaScript da implementação atual; cartões e índice inline do catálogo. |
| js/config.js | Contatos e parâmetros operacionais em window.SITE_CONFIG. |
| dados/produtos.json | Referência editorial dos produtos; não é carregada automaticamente pelo site. |
| produtos/ | Páginas individuais dos exemplos. |
| img/ | Logotipo e ilustrações; há também imagens embutidas no HTML. |
| versoes/ | Registros de entregas; não substituem backup completo. |
| CHANGELOG.md | Histórico consolidado de modificações, motivo, impacto e testes. |
| DECISOES-DO-PROJETO.md | Padrões e decisões aprovadas. |
| MAPA-DE-ARQUIVOS.md | Localização detalhada, dependências e regras de manutenção. |
| robots.txt | Diretivas de rastreamento; não protege acesso. |

## 3. Abrir e testar localmente

1. Extraia ou baixe o projeto completo, preservando as pastas.
2. Abra o `index.html` da raiz.
3. Não use como entrada o HTML avulso antigo `araujo-brasilio-v0.1.0-2026-11-02.html`: ele possui configuração embutida e não acompanha as alterações de `js/config.js`.
4. Para testar o carregamento por HTTP, se Python estiver instalado, abra o terminal na raiz e execute:

```bash
python -m http.server 8000 --bind 127.0.0.1
```

Acesse `http://127.0.0.1:8000/` e encerre com `Ctrl+C`. O servidor é apenas para teste local.

## 4. Configuração de contatos e WhatsApp

Edite somente o `js/config.js` da pasta que está sendo testada. A estrutura é:

```js
window.SITE_CONFIG = {
  "whatsapp": "5519989470259",
  "email": "",
  "telefone": "",
  "endereco": "",
  "horarios": "",
  "cidade": "",
  "uf": "",
  "dominio": "",
  "modoDemonstracao": true
};
```

O bloco acima ilustra os campos. Não substitua todo o arquivo por esse exemplo se quiser preservar os dados já preenchidos. Mantenha apenas informações confirmadas; os campos vazios do exemplo não são uma solicitação para apagar os atuais.

### Formato do WhatsApp

- Usar `55` + DDD + telefone, somente dígitos, em uma string.
- Configuração recebida para o projeto: `5519989470259`.
- O número `19989470259`, sem o código 55, foi rejeitado no diagnóstico anterior.
- Não usar `+`, espaços, parênteses ou hífens nesse campo.
- O campo `telefone` é separado do campo `whatsapp`.
- Campos de cidade, UF e domínio não geram automaticamente SEO local ou metadados.
- Não armazenar senhas, tokens ou dados sigilosos nesse arquivo: configurações do navegador são públicas.

### Diagnóstico do botão desativado

Após salvar o arquivo e recarregar, abra o Console e consulte:

```js
window.SITE_CONFIG.whatsapp
```

Resultado esperado para a configuração atual:

```text
5519989470259
```

Para conferir a origem e o formato:

```js
console.log({
  paginaAberta: location.href,
  whatsappCarregado: window.SITE_CONFIG?.whatsapp,
  formatoAceito: /^55[1-9]\d{9,10}$/.test(window.SITE_CONFIG?.whatsapp || ""),
  scriptsExternos: [...document.scripts]
    .filter(script => script.src)
    .map(script => script.src)
});
```

A página deve apontar para o `index.html` correto, listar `js/config.js` e retornar `formatoAceito: true`. Depois abra o orçamento e clique novamente em “Revisar mensagem”.

Se o valor estiver vazio, confira o caminho do script e eventuais configurações duplicadas/embutidas no HTML. Se houver erros de carregamento ou sintaxe no Console, corrija-os antes de continuar. Não force a habilitação retirando `disabled`: isso não corrige o destinatário usado pelo site.

## 5. Manutenção de produtos

`dados/produtos.json` não alimenta automaticamente a interface. Ao alterar produtos, sincronize:

1. A referência editorial em `dados/produtos.json`.
2. O índice `window.CATALOG` em `index.html`.
3. Os cartões, categorias e filtros correspondentes no HTML.
4. A página própria em `produtos/`.
5. As referências de imagens, inclusive as embutidas.

Preserve IDs e URLs já aprovados. Não invente marca, preço, promoção, estoque, CA, certificação, material, tamanho ou aplicação técnica. Usar dados do fabricante e confirmar as linhas efetivamente vendidas.

Os exemplos atuais vão de `DEMO-001` a `DEMO-008`. As variações existentes são apenas “Confirmar com atendimento”; opções reais precisam ser cadastradas e implementadas antes de serem oferecidas ao visitante.

## 6. Imagens e identidade visual

- Preservar proporção, nome e identidade do logotipo.
- `img/logo-original.jpg` preserva a captura recebida.
- `img/logo.webp` é a versão recortada e otimizada.
- Os SVGs representam categorias/exemplos; não são fotos de modelos reais.
- Usar imagens próprias ou autorizadas ao substituir os exemplos.
- Algumas imagens estão embutidas no HTML: trocar o arquivo na pasta pode não atualizar todas as aparições.
- Paleta de referência: amarelo #FFB800, destaque #FFC928, grafite #242424, cinzas e branco; não é uma extração oficial das cores da marca.

## 7. Privacidade e armazenamento

A lista de orçamento pode persistir no navegador apenas IDs dos itens, quantidades e a opção genérica de variação. Cidade, CEP e observações são usados em memória para compor a mensagem e não devem ser gravados no armazenamento local pelo site.

A interface permite limpar os itens. Ao abrir o WhatsApp, o texto é encaminhado ao serviço por URL; o usuário precisa revisar a mensagem. Não solicitar dados de cartão, CPF ou dados pessoais desnecessários.

A política disponível é preliminar. Antes da operação comercial, revisar identificação do responsável, canal de privacidade, finalidades, bases legais, retenção e direitos aplicáveis. Registros técnicos do provedor e novas integrações também precisam ser considerados. Não adicionar ferramentas de análise ou marketing sem revisar o tratamento de dados.

## 8. Checklist de testes

- [ ] Abrir a página em 360, 768 e 1440 px e testar zoom de 200%.
- [ ] Conferir menu móvel, foco visível, teclado, contraste e leitura assistiva.
- [ ] Testar Tab, Shift+Tab, Enter e Escape nos controles e diálogos.
- [ ] Buscar nome, categoria, referência e termo inexistente; limpar filtros.
- [ ] Abrir as oito páginas de produtos e testar retorno ao catálogo.
- [ ] Adicionar itens repetidos, alterar quantidades entre 1 e 999 e testar valores inválidos.
- [ ] Remover itens e limpar a lista.
- [ ] Recarregar e conferir persistência somente dos dados previstos.
- [ ] Testar entrega e retirada; omitir cidade/CEP da mensagem quando a opção for retirada.
- [ ] Bloquear revisão quando não houver itens nem observações.
- [ ] Com WhatsApp vazio ou inválido, confirmar bloqueio do botão.
- [ ] Com a configuração válida, revisar mensagem e conferir destinatário antes de enviar.
- [ ] Testar armazenamento local indisponível e JavaScript desativado: conferir leitura e links de detalhes.
- [ ] Conferir ausência de erros no Console e de referências ausentes.
- [ ] Repetir os testes essenciais no endereço publicado.

Este checklist não registra aprovação automática. O diagnóstico anterior confirmou configuração inválida sem o código 55 e posterior correção do arquivo. O funcionamento final de todos os itens em navegador real ainda precisa ser registrado após os testes.

## 9. GitHub, Fontes e sincronização

Repositório de referência: https://github.com/JFLPinheiro/SiteABE

1. Trabalhar na pasta completa, mantendo a estrutura aprovada.
2. Antes de sobrescrever arquivos, conferir se a cópia local, as Fontes e o repositório estão na mesma revisão.
3. Se houver divergência, definir a versão de referência antes de mesclar mudanças.
4. Salvar os arquivos atualizados no repositório e substituir as cópias antigas nas Fontes, quando possível.
5. Consultar MAPA-DE-ARQUIVOS.md quando os arquivos aparecerem avulsos nas Fontes.
6. Conferir o diff antes de confirmar um commit.

Na consulta realizada em 09/11/2026 ao commit `194ba3d665be5aa24c3804ea70c572be9720cbec`, o README remoto estava vazio (1 byte). Este documento foi preparado para restaurar e atualizar as instruções. Isso não afirma que o arquivo já foi enviado ao GitHub.

Guardar código no GitHub e publicar pelo GitHub Pages são etapas distintas. A configuração de publicação não foi auditada nesta atualização. Se usar Pages, confirmar no painel Settings > Pages a origem de publicação e o resultado da execução/deploy, quando aplicável. Manter caminhos relativos compatíveis com `/SiteABE/` e testar no endereço final.

GitHub Pages pode servir documentação e outros arquivos do repositório publicado. Não confiar em nomes de arquivo ou em robots.txt para ocultar informações. Não colocar dados sensíveis no repositório nem no site público.

## 10. Publicação futura na Hostinger

A implementação estática não requer banco de dados, PHP ou WordPress. Verificar os recursos reais do plano antes de depender de upload, domínio, HTTPS, e-mail, backups ou WordPress.

Procedimento:
1. Fazer backup do site atualmente publicado.
2. Confirmar a pasta pública do domínio no painel; não presumir que seja a mesma para todos os domínios.
3. Enviar arquivos de execução preservando as pastas: index.html, js/, produtos/, imagens utilizadas e demais recursos efetivamente referenciados.
4. Manter documentação interna, originais e cópias de segurança fora da área pública quando não forem necessários ao funcionamento. O JSON editorial também não precisa ser publicado se continuar sem uso em runtime.
5. Conferir HTTPS e testar na URL final.
6. Manter acesso ao backup anterior para reversão.

## 11. SEO e bloqueios antes de produção

O protótipo possui `noindex,nofollow` e `robots.txt` com bloqueio de rastreamento. Esses mecanismos não são autenticação e não garantem sigilo ou remoção de URLs dos buscadores. Para conteúdo privado, usar restrição de acesso apropriada ou teste local.

Antes de liberar indexação:
- Confirmar domínio, cidade, UF, endereço, contatos e horários.
- Substituir produtos e imagens demonstrativos.
- Revisar textos, política de privacidade, condições de entrega e retirada.
- Revisar título, descrição, Open Graph, URL canônica e URLs absolutas reais.
- Criar sitemap.xml com páginas publicáveis e domínio confirmado.
- Adicionar dados estruturados somente com informações verdadeiras e pertinentes.
- Remover noindex das páginas publicáveis e ajustar robots.txt de forma coordenada.
- Não inventar ofertas, avaliações, estrelas ou disponibilidade.

Não há geração automática de sitemap ou LocalBusiness nesta implementação documentada. Preencher domínio e endereço em config.js não implementa essas funções.

## 12. Versionamento, backup e reversão

Para toda alteração de código, conteúdo, imagens, configuração ou documentação:
1. Identificar data e versão incremental; usar sequência quando houver várias entregas no mesmo dia.
2. Atualizar CHANGELOG.md com arquivos afetados, descrição, motivo, impacto e testes/publicação.
3. Salvar registro datado em versoes/ quando aplicável.
4. Atualizar DECISOES-DO-PROJETO.md se houver decisão nova.
5. Atualizar MAPA-DE-ARQUIVOS.md se mudar a estrutura.
6. Preservar os nomes públicos e URLs; não renomear index.html a cada versão.
7. Fazer backup completo ou preservar o commit anterior.

Para reverter, restaurar o backup ou reverter o commit correspondente, conferindo todos os arquivos afetados. Documentos em versoes/ são registros, não cópias completas do código.

### Entrada para acrescentar ao CHANGELOG.md

Inserir abaixo do título, sem remover o histórico existente:

```markdown
## [2026-11-09] — Versão 0.1.4
### Alterado
- README.md: restauração e atualização das instruções do projeto.
### Motivo
- Corrigir a ausência de conteúdo no README do GitHub e consolidar a manutenção.
### Impacto
- Somente documentação; nenhum código, configuração ou produto foi alterado.
### Testes e publicação
- Conferir a renderização do Markdown e os caminhos na raiz do projeto.
- Salvar a mesma versão no computador, nas Fontes e no GitHub.
- Publicação e testes funcionais não realizados por esta entrega.
### Reversão
- Restaurar a cópia anterior do README.md e registrar a reversão.
```

Sugestão de registro: `versoes/2026-11-09-v0.1.4.md`. Sugestão de commit: `docs: atualiza README e instruções de manutenção (v0.1.4)`.

As entradas anteriores 0.1.2 e 0.1.3 ainda precisam ser consolidadas no changelog se não tiverem sido adicionadas; não sobrescrever o histórico para corrigir essa pendência.

## 13. Etapa futura — WordPress

Planejar migração sem instalar WordPress nesta etapa. Preservar URLs aprovadas, textos, imagens, categorias e SEO. Separar campos editáveis pelo cliente de áreas técnicas e documentar a edição de contatos, produtos e banners.

Avaliar tema leve, hospedagem, segurança e plugins somente conforme necessidade. Um catálogo com orçamento não é checkout; pagamento online exige planejamento separado. Fazer backup completo antes de migrações ou atualizações de WordPress, temas e plugins.

## 14. Continuidade do trabalho

Consultar README.md, MAPA-DE-ARQUIVOS.md, CHANGELOG.md e DECISOES-DO-PROJETO.md antes de modificar o projeto. Reaproveitar padrões aprovados e registrar correções para evitar repetição de erros.

O acesso aos arquivos depende das fontes e ferramentas disponíveis. Não presumir memória permanente nem sincronização automática com computador, GitHub ou hospedagem. Escritas remotas exigem confirmação do destino e do conteúdo.

Salve esta atualização no projeto e faça backup antes de publicar, se aplicável.
