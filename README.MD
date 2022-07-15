
<h1 align="center">Landing page originals</h1>
<p align="center"><img src=".md_files\logo_originals.png" /></p> <br/>
<p><strong>Essa documentação serve de guia para que sua compreensão sobre o projeto seja total. Por favor, faça a leitura completa e com atenção, afinal, o que está descrito nesse documento será primordial para um desenvolvimento limpo, alinhado e que siga os nossos padrões. Além de ser um apoio à erros e correções já conhecidos</strong></p>


<h2>Indice</h2> 
<ol> 
<li><a href="#overview">Overview</a></li>
<li><a href="#tecnologias">Tecnologias utilizadas</a></li>
<li><a href="#dependencias">Dependências</a></li>
<li><a href="#iniciando">Iniciando o desenvolvimento</a></li>
<li><a href="#docker">Docker</a></li>
<li><a href="#correcoes">Correções conhecidas</a></li>
</ol>


<h2 id="overview">Overview</h2> 
<p>A landing page dos originals tem como foco, apresentar o programa para novos usuários. Na página é possível encontrar informações crucias que despertam  interesse nos visitantes. Além disso, há também, um formulário para que os interessados possam preencher e receber mais informações diretamente em sua caixa de entrada do seu melhor email.</p>

<h2 id="tecnologias">Tecnologias utilizadas</h2>

<img src="https://img.shields.io/badge/VUE-CLI@5.0.8-41B883"/>
<img src="https://img.shields.io/badge/LUMEN-9-F05340"/>
<img src="https://img.shields.io/badge/MYSQL/MARIADB-15.1/10.8.3-00758F"/>
<img src="https://img.shields.io/badge/DOCKER-20.10.16-2393e7"/> <br/>
<span><i>As tecnologias lumen e banco de dados foram dockerizadas, para  mais referências sobre as imagens docker <a href="#docker">clique aqui</a></i></span> <br><br>

> <h3 id="dependencias">Dependências de desenvolvimento</h3>
> <ul>
> <li>node: v16.15^</li>
> <li>npm: v8.10^</li>
> <li>vue/cli: v5.0.8^</li>
> </ul>
>
>> <h4>Dependências do vue</h4>
>> <img src=".md_files\vue_deps.png"/>

<h2 id="iniciando">Iniciando o desenvolvimento</h2>

<h3>Passo-a-passo</h3>
<ol>
<li>Você deverá clonar esse repositório <a href="https://github.com/TroyanLock/landing-page-originals">link</a></li>
<li>Com um terminal dentro da raíz desse projeto execute o comando <code>$ docker compose up --build -d</code></li>
<li>Para realizar a conectividade entre a API e o banco de dados, não se esqueça de configurar com arquivo <i>.env</i> que está dentro da pasta API de acordo com as mesma configurações encontradas no arquivo <i>.env.example</i></li>
<li>Você poderá acessar o uma tela no link: <a href="http://localhost:8000">localhost:8000</a> <br> <img src=".md_files\screen_success.png"></li>
<li>Com o terminal ainda ativo, você deverá rodar os seguintes comandos:
<code>$ cd src/client</code> <code>$ npm install</code></li> e quando a instalação estiver completa, você pode iniciar o servidor de desenvolvimento com  <code>$ npm run serve</code>
</ol>
<li>Com o editor de textos da sua escolha abra a pasta src e pronto. Seu ambiente deve estar pronto para o uso.</li>

<h2 id="docker">Docker</h2>
<p>O docker está sendo utilizado para agilizar o processo de ínicio no desenvolvimentodo projeto e evitar erros de dependências, ou de diferenças na hora da execução. Um breve resumo das imagens utilizadas abaixo.</p>
<h3>PHP</h3>
<p>Utilizamos uma imagem php dentro de um servidor apache para hospedarmos nossa API lúmen no localhost e exibir no navegador, para maior referência sobre a imagem <a href="https://hub.docker.com/_/php">segue o link para o dockerhub</a></p>

<h3>MARIADB</h3>
<p>para banco de dados utilizamos o MARIADB, um client MYSQL, leve e confiável, onde armazenaremos os dados do formulário, <a href="https://hub.docker.com/_/mariadb">maiores informações aqui</a></p>

<h2 id="correcoes">Correções conhecidas</h2>

> <h4>Ao iniciar o lúmen no navegador, erros de permissão de usuário aparecem</h4>
>
>> Para resolver isso precisamos estar dentro do terminal linux do container e acessar a pasta do projeto, para fazer isso siga os passos: 
>>> <pre>
>>> <code>$ docker compose exec api bash</code>
>>> <code>$ cd api</code>
>>> </pre>
>> E por fim execute todos esses comandos:
>>> <pre>
>>> <code>$ chown -R $USER:www-data storage</code>
>>> <code>$ chown -R $USER:www-data bootstrap/cache</code>
>>> <code>$ chmod -R 775 storage</code>
>>> <code>$ chmod -R 775 bootstrap/cache</code>
>>> <code>$ ps aux | egrep '(apache|httpd)'</code>
>>> </pre>