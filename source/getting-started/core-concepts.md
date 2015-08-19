Para começar com Ember.js, existem alguns conceitos chave que você precisa entender;

## Templates (Moldes)

Templates, eles são escritos na linguagem "Handlebars", descrevem a user interface da 
sua aplicação. 
your application. Além de simples HTML, templates podem conter expressões,
como `{{title}}` ou `{{author}}`, que leva informações criadas pelo seu componente
ou controle e colocam no HTML. Essas expressões tambem podem ser helpers como
`{{#if isAdmin}}30 people have viewed your blog today.{{/if}}`. E elas tambem 
podem ser conter components, como se um template listasse todos os posts e um
componente listasse cada um deles.

## Components (Componentes)

componentes são o jeito principal que a interface é organizada no ember. Eles
consistem de duas partes: um template, e um arquivo escrito em JavaScript que 
determina o comportamento desse componente. Por exemplo, um blog talvez tenha
um componente para mostrar uma lista de post chamada `all-posts`, e outro 
componente para renderizar cada post individualmente chamado `view-post`. Supondo
que o usuario possa votar nos posts desse blog, o  `view-post` componente talvez 
defina um comportamento do tipo _quando o usuario clicar no botão de votar, 
incremente a propriedade 'votos' pelo valor 1_.

## Controllers (Controladores)

Controllers são bem parecidos com componentes, tão parecidos que em futuras 
versões do Ember, controllers serão totalmente substituidos por componentes. 
Agora componentes não podem fazer parte do "routes" (veja abaixo), mas quando 
mudar, será recomendado trocar todos os controllers por componentes.

## Models (Modelos)

Models representão _persistent state_. Por exemplo, um sistema de blog, ele 
iria precisar salvar o conteudo de um post para ser publicado, então o essa 
aplicação precisaria de um model definindo isso, ele provavelmente seria chamado
de `Post` model, normalmente informações ficam guardadas em um servidor, porem 
o model pode ser configurado para salvar em qualquer lugar, como no Local Storage
do browser.

## Routes (Rotas)

Routes são responsaveis por carregar seu controller e template. 
Eles tambem podem ser responsaveis por gerenciar um ou mais models,
por exemplo, uma route `all-posts` pode ser responsavel pelo `Posts` model,
carregar o  `all-posts` controller e renderizar o `all-posts` template.
Do mesmo jeito a rota `view-posts` pode ser responsavel pelo model que controla 
qual post mostrar, carregar o `view-post` controller, e renderizar o `view-post` template.

## The Router

The router mapeia a URL para as rotas. Por exemplo, quando um usuario visita a URL `/posts`
O router talvez carregue a rota `all-posts`. O router tambem pode carregar 
'rotas aninhadas' (nested routes). Por exemplo, se sua aplicação de blog tem uma lista de posts 
no lado esquerdo da tela que mostra o proximo post à direita, nos podemos dizer que a rota do `view-post`
esta aninhada com a do `all-posts`.

Talvez a parte mais importante para se lembrar sobre o Ember é que ele é
a URL gerencia o estado da aplicação. A URL determina qual route carregar, 
e assim a route se encarrega dos controllers, models e templates.