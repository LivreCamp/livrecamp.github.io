# LivreCamp Page

Aqui se encontra o código da página do projeto. Ela foi escrita em Jade/Less
e compilada para HTML/CSS usando o gerador de páginas estáticas [**harpjs**](https://harpjs.com). 
O conteúdo modificável da página é escrito em JSON e Markdown. 

Todos são livres e encorajados a copiar, modificar, contribuir, mandar sugestões e reportar bugs. (:

## Pré-requisitos

- npm
- git

## Subindo o servidor

O código do site é compilado com o gerador de páginas estáticas [**harpjs**](https://harpjs.com). Ele é instalado através do **npm**.

    npm install -g harpjs

Após a instalação, clonamos o repositório git

    git clone https://github.com/LivreCamp/livrecamp.github.io.git

E iniciamos o servidor **harp**

    cd livrecamp.github.io
    harp server _harp

Agora é só acessar a página em http://0.0.0.0:9000.

## Estrutura

Com o harp, o HTML é compilado do código fonte que se encontra em **_harp**. Dessa forma, a pasta **_harp** é a única que deverá ser modificada.

````
_harp
├── 404.jade
├── articles
│   ├── _data.json
│   ├── index.jade
│   ├── _layout.jade
│   └── reuniao-01-mar.md
├── background.png
├── DejaVuSansMono-Bold.ttf
├── DejaVuSansMono.ttf
├── events
│   └── _data.json
├── footer.png
├── header.png
├── index.jade
├── _layout.jade
├── logo.png
├── main.less
├── _mixins
│   ├── article.jade
│   └── event.jade
└── _partials
    ├── footer.jade
    ├── header.jade
    ├── scripts.jade
    └── styles.jade
````

### _harp

Os arquivos **.jade** são os arquivos que posteriormente serão compilados para HTML. O arquivo base de todas as páginas dentro de **_harp** é **_layout.jade**. O arquivo **index.jade** é chamado ao acessar a página principal. 

O arquivo **main.less** é o arquivo de estilo da página. Ele será compilado para css.

### articles

É onde se encontram os artigos que aparecem na sessão de *notícias* da página. O arquivo **_data.json** é o arquivo de metadata e ele é usado para indexar os arquivos markdown dentro da pasta. O arquivo **_layout.jade** é o esqueleto base para todas as páginas acessadas dentro de **articles**, incluindo o **index.jade**, que é chamado ao acessar **/articles**.

### events

Possui apenas um **_data.json** que, análogo ao de **articles**, serve apenas metadata para a sessão de *eventos* da página inicial. 


## Administração da página

### Como adicionar eventos?

Para adicionar um novo evento é necessário editar o arquivo ````events/_data.json```` que se encontra em **_harp**. A estrutura do evento deve seguir o modelo:

````
{
    "0" : { // Deve ser um ID válido e único
         "title" : "Título do Evento",
         "date" : "07/03",
         "past": false, // Se o evento já aconteceu ou não
         "place" : "Sala 302/IC3"
    },
    ...
}
````

### Como adicionar uma nova notícia?

Para adicionar uma nova notícia, deve-se editar o arquivo metadata ````articles/_data.json```` que se encontra em **_harp** e deve seguir o seguinte modelo:

````
{
	"noticia-interna" : {
		"date": "01/03",
		"title": "Notícia Local",
		"url": "/articles/noticia-local"
	},

	"noticia-externa" : {
		"date": "01/03",
		"title": "Noticia de fora",
		"url": "http://noticia.com"	
	}
		
}
````

Ao postar uma notícia interna, o endereço URL da notícia deve ter o mesmo endereço do arquivo markdown localizado dentro de **articles**. Com a configuração acima, por exemplo, existiria um arquivo **articles/noticia-local.md**.

## Mandando as modificações

Depois que alterar os arquivos de **_harp** e testar as modificações no servidor local, podemos compilar o código

    harp compile _harp ./

Adicionar os arquivos e mandar um commit

    git commit -am "Minhas modificações"
    git push origin master

E pronto (:

## Contato

Qualquer duvida ou sugestão, você pode abrir uma issue no nosso repositório do Github ou entrar em contato através do nosso canal no [Telegram](https://t.me/livrecamp).

## Licença

O conteúdo deste projeto é licenciado pela [Creative Commons 3.0](https//creativecommons.org/licenses/by/3.0/br/) e seu código licenciado pela [General Public License 3.0](www.gnu.org/licenses/gpl-3.0.html)
