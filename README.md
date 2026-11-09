# Araújo Brasílio — site estático
Versão 0.1.0 — 2026-11-02. Primeira implementação entregue, não publicada.

## Abrir e testar
Abra index.html no navegador. No pacote ZIP, extraia todos os arquivos mantendo as pastas. A página HTML avulsa também é autossuficiente; nela, os detalhes abrem em janelas acessíveis via JavaScript, e os links de fallback para arquivos só existem no pacote completo.
Opcional para teste HTTP local: execute `python -m http.server 8000` na pasta e acesse http://localhost:8000. Não deixe o servidor de teste exposto na internet.

## Dados reais e configuração
Edite js/config.js: whatsapp deve conter 55 + DDD + telefone, somente números. Campos vazios são intencionais. Não use telefone fictício. Configurar o número habilita a abertura do WhatsApp; a mensagem permanece demonstrativa até a revisão completa do catálogo e de modoDemonstracao.
Não desative modoDemonstracao antes de substituir todos os produtos e revisar avisos demonstrativos no HTML.
No HTML avulso, edite o bloco window.SITE_CONFIG dentro do próprio documento.
Dados de domínio/cidade/UF estão reservados, mas não geram SEO automaticamente nesta versão.

## Produtos e manutenção
A primeira versão renderiza as informações no HTML e utiliza window.CATALOG como índice do JavaScript. dados/produtos.json é a fonte editorial de referência, não é carregada automaticamente. Ao editar produtos, sincronize esse JSON, o bloco window.CATALOG, os cartões/categorias em index.html e as respectivas páginas em produtos/. Preserve IDs e URLs. Mudanças apenas no JSON não alteram o site.
As variações existentes são somente “Confirmar com atendimento”; implemente opções reais após receber o catálogo. Não invente tamanho, CA, marca ou proteção.
As ilustrações SVG foram criadas para este protótipo; não representam modelos reais. Substitua-as por fotos próprias ou autorizadas. O logo foi recortado da captura enviada; o original está em img/logo-original.jpg.

## Testes manuais obrigatórios
1. Teste largura de 360, 768 e 1440 px e zoom de 200%.
2. Navegue com Tab/Shift+Tab, Enter e Escape; confira menus e diálogos.
3. Busque por nome, categoria, DEMO-001 e um termo inexistente; limpe filtros.
4. Adicione itens repetidos, altere quantidades 1–999, remova e limpe itens.
5. Recarregue: apenas IDs/quantidades/variação genérica devem persistir; cidade/CEP/observações não.
6. Selecione entrega e retirada; confira mensagem e omissão dos campos de entrega na retirada.
7. Teste revisão sem itens e sem observações: deve ser bloqueada.
8. WhatsApp vazio: botão de envio deve ficar desabilitado. Com número real confirmado: confira destinatário e texto antes de enviar.
9. Abra cada URL em produtos/ e confira retorno ao catálogo.
10. Teste com armazenamento local bloqueado e sem JavaScript: leitura e páginas de detalhes devem continuar disponíveis.
11. Verifique foco, contraste, leitor de tela e acessibilidade em navegador real.
Os testes interativos em navegador ainda precisam ser realizados; a entrega recebeu somente verificações estruturais automatizadas.

## Publicação na Hostinger — somente após revisão
Este pacote usa apenas arquivos estáticos e não requer PHP, banco de dados ou WordPress. Verifique se o plano contratado permite upload de arquivos, domínio e HTTPS. Não pressupomos esses recursos disponíveis.
Faça backup do site atual. Extraia o ZIP localmente. Após revisar tudo, envie o conteúdo da pasta para a raiz pública correspondente ao domínio no painel da hospedagem (frequentemente public_html; confirme a pasta correta). Não envie documentação interna ou backups para a área pública: mantenha README.md, CHANGELOG.md, DECISOES-DO-PROJETO.md, versoes/ e logo-original.jpg fora do site público.
Ative/verifique HTTPS no painel conforme os recursos do plano. Teste na URL final.

## Bloqueios antes de produção
Há meta noindex,nofollow em todas as páginas e robots.txt bloqueando rastreamento. São precauções de protótipo, NÃO controle de acesso. Se o material precisar ser privado, restrinja acesso por autenticação na hospedagem ou teste localmente.
Antes de liberar indexação: preencher dados reais e política definitiva; remover exemplos e avisos; cadastrar páginas verdadeiras; configurar domínio e canonicals; revisar títulos/descrições/OG (incluir imagem e URL absolutas reais); gerar sitemap.xml com URLs reais; permitir rastreamento no robots.txt; remover noindex apenas nas páginas publicáveis. Não há sitemap nem LocalBusiness nesta versão porque domínio, endereço e contatos estão pendentes. Não cadastrar avaliações/ofertas fictícias.
Não adicione analytics, cookies de marketing ou integrações sem revisar privacidade.

## Reversão e WordPress
Antes de substituir qualquer site, exporte uma cópia completa da pasta atual. Para reverter, restaure esse backup. Para retornar a este protótipo, extraia este ZIP original em ambiente de teste.
Na futura migração preserve URLs de produtos, categorias, textos, imagens e metadados aprovados. Orçamento não é checkout; avaliar e-commerce separadamente. Cliente poderá editar conteúdo; configuração técnica, segurança e backups precisam de processo próprio.

Salve esta atualização no projeto e faça backup antes de publicar, se aplicável.
