Aplicacao web Node.js/Express chamada NodeGoat-DevSec, acessada por navegador via HTTP na porta 4000. O servidor Express renderiza paginas HTML com Swig, serve arquivos estaticos e expoe rotas para login, cadastro, dashboard, perfil, beneficios, contribuicoes, alocacoes, memorandos, pesquisa e tutorial.

A autenticacao usa usuario/senha e sessoes por cookie com express-session. Requisicoes de formulario e JSON sao processadas por body-parser. Apos login, o servidor grava o ID do usuario na sessao e usa o cookie para controlar acesso a paginas protegidas.

A aplicacao possui uma camada de rotas/handlers e uma camada DAO que acessa MongoDB pelo driver nativo mongodb. O banco armazena usuarios, sessoes/dados relacionados, perfil, beneficios, contribuicoes, alocacoes e memorandos.

Em Docker Compose ha dois servicos: web, com a aplicacao Node.js, e mongo, com MongoDB. O servico web conecta no banco por mongodb://mongo:27017/nodegoat. Fora do Docker, a aplicacao pode usar MongoDB local ou remoto via MONGODB_URI.

Principais limites de confianca: navegador para servidor Express, servidor Express para MongoDB, cookie de sessao no navegador para validacao no backend, entrada de usuario para templates HTML, entrada de usuario para consultas MongoDB e aplicacao para URLs externas em redirecionamentos.
