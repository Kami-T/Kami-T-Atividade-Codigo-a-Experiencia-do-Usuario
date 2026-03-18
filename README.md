# Projeto MVC — Pagina Inicial

Projeto desenvolvido seguindo o padrao de arquitetura **MVC** (_Model-View-Controller_).
A pagina inicial serve como ponto de entrada da aplicacao e disponibiliza uma _navbar_ de navegacao entre as views.

## Estrutura do Projeto

### Pastas principais

- `src/views/` — telas HTML da aplicacao
- `src/views/css/` — folhas de estilo externas
- `src/views/js/` — scripts JavaScript
- `src/controllers/` — logica de controle
- `src/models/` — camada de dados

### Paginas disponíveis

1. `index.html` — Pagina inicial
2. `cadastro.html` — Formulario de cadastro
3. `contatos.html` — Lista de contatos
4. `produto.html` — Exibicao de produtos
5. `login.html` — Autenticacao do usuario

## Como funciona a Pagina Inicial

A tela `index.html` carrega o arquivo **`css/style.css`** de forma externa e exibe uma navbar com os links de navegacao.

### Fluxo de navegacao

1. O usuario acessa `index.html` no navegador.
2. Visualiza o menu superior com os links das paginas.
3. Clica no item desejado e e redirecionado para a view correspondente.

## Checklist de Implementacao

- [x] Criar estrutura base do `index.html`
- [x] Adicionar navbar com links para as outras paginas
- [x] Mover CSS inline para `css/style.css`
- [x] Remover o link de Login da pagina principal
- [ ] Adicionar conteudo nas demais views
- [ ] Conectar views aos controllers

## Trecho de Codigo — Navbar

Estrutura HTML da navbar na `index.html`:

```html
<nav>
  <ul>
    <li><a href="index.html">Inicio</a></li>
    <li><a href="cadastro.html">Cadastro</a></li>
    <li><a href="contatos.html">Contatos</a></li>
    <li><a href="produto.html">Produto</a></li>
  </ul>
</nav>
```

Vinculo do CSS externo no `<head>`:

```html
<link rel="stylesheet" href="css/style.css" />
```

## Links Uteis

- [Pagina Inicial do Projeto](src/views/index.html)
- [Guia de Markdown](https://www.markdownguide.org)

## Progresso do Desenvolvimento

### Status das Rotas
- Ao clicar no botão principal (`Realizar Ação`) em [src/views/index.html](src/views/index.html), o script `src/views/js/main.js` registra uma requisição para o `NavigationController` (console), e exibe imediatamente a mensagem "Processando sua solicitação..." em azul. O `NavigationController` (arquivo `src/controllers/NavigationController.js`) contém a função `gerenciarRota(acao)` que decide a rota — por exemplo, retorna "Exibindo tela de Sucesso" quando a ação é `FINALIZAR_CADASTRO`, caso contrário permanece na página atual.

### Feedback ao Usuário
- No fluxo atual, o usuário recebe feedback por meio de uma mensagem de texto no elemento `#feedback-mensagem` que muda para "Processando sua solicitação..." com alteração de cor (azul). Não há modal de sucesso nem redirecionamento automático implementado; confirmações adicionais precisam ser ligadas ao retorno do controller.

### Dificuldades Técnicas
- Desafio: separar a lógica (JS/PHP) da estrutura (HTML) quando o código atual manipula diretamente o DOM e simula o controller no cliente. Para uma separação limpa seria necessário expor uma API (endpoints) e usar chamadas assíncronas (fetch/AJAX) para que a lógica de negócios (por exemplo em PHP) retorne respostas padronizadas, evitando mistura de responsabilidades entre view e controller.
