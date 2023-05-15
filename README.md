# Como usar git simples

<h2>Fluxo de trabalho</h2>

<p>Seus repositórios locais consistem em três "árvores" mantidas pelo git. a primeira delas é sua <code>Working Directory</code>que contém os arquivos vigentes. a segunda <code>Index</code> que funciona como uma área temporária e finalmente a <code>HEAD</code> que aponta para o último commit (confirmação) que você fez.</p>

## Após a instalação do git

<h2>Configurando o git</h2>

<p>Configure o seu email de acordo com o seu git</p>
<pre><code>git config --global user.email "seuemail@gmail.com"</code></pre>

<p>Configure o seu nome de usuário de acordo do seu git</p>
<pre><code>git config --global user.name "seunome"</code><pre>

## Agora podemos  começar a utilizar o git. A primeira coisa a se fazer caso você não possua um repositório é criar um.

<h3>Criando um novo repositório</h3>

<p>crie uma nova pasta, abra-a e execute o comando</p>
<pre><code>git init</code></pre>
<p>para criar um novo repositório.</p>

## Agora que você criou seu repositório e adicionou seus arquivos devemos subir o arquivo para seu para a área de preparação "staging area".

<h3>Adicionando os arquivos para a staging area</h3>

<p>Utilize</p>
<pre><code>git add &lt;"nome-do-arquivo"&gt;</code></pre>
<p>ou adicione todos os arquivos com</p>
<pre><code>git add .</code></pre>
<p>Dessa forma os arquivos ja estarão na staging area.

## Caso você tenha enviado um arquivo para a staging area por engano pode retiralo

<h3>Removendo os arquivos para a staging area</h3>

<p>Utilize</p>
<pre><code>git reset &lt;"nome-do-arquivo"&gt;</code></pre>
<p>ou remova todos os arquivos com</p>
<pre><code>git reset .</code></pre>
<p>Dessa forma os arquivos já estarão removidos da staging area.

## Agora podemos que os arquivos estão na staging area, podemos confirmar que realmente que forma adicionados fazendo o commit.

<p>Para fazer o commit basta utilizar o comando a seguir</p>
<pre><code>git commit -m "comentários das alterações"</code></pre>
<p>e caso deseje alterar o commit basta </p>

<h3>Clonando um repositório</h3>

<p>Crie uma cópia de trabalho em um repositório local executando o comando</p>
<pre><code>git clone /caminho/para/o/repositório</code></pre>
<p>quando usar um servidor remoto, seu comando será</p>
<pre><code>git clone https:/caminho/para/o/repositório</code></pre>

<h3>Adicionar & confirmar</h3>

<p>Você pode propor mudanças (adicioná-las ao Index) usando</p>
<pre><code>git add &lt;arquivo&gt;</code></pre>
<p>ou adicione todas as alterações</p>
<pre><code>git add .</code></pre>
<p>Este é o primeiro passo no fluxo de trabalho básico do git. Para realmente confirmar estas mudanças (isto é, fazer um commit), use</p>
<pre><code>git commit -m "comentários das alterações"</code></pre>
<p>Agora o arquivo é enviado para o HEAD, mas ainda não para o repositório remoto.</p>

<h3>Download & Integração com <code>pull</code> git</h3>

<p>O uso (e não é exceção) não apenas baixará novas alterações do repositório remoto. Ele também irá integrá-los diretamente em sua filial local HEAD. Por padrão, essa integração acontecerá através de uma "fusão", mas você também pode escolher uma "rebase":git pull origin master</p>
<pre><code>git pull origin master</code></pre><p>ou</p><pre><code>git pull origin master --rebase</code></pre>
<p>Se você não quiser integrar novas alterações diretamente, então você pode usar : isso só vai baixar novas alterações, mas deixar sua filial HEAD e arquivos de cópia de trabalho intocados.git fetch</p>
<pre><code>git fetch origin</code></pre>

<h3>Usando o comando de <code>pull</code> simples do git</h3>

<p>Na maioria dos casos, sua filial HEAD local já terá uma conexão de rastreamento adequada configurada com um ramo remoto. Esta configuração fornece valores padrão para que o comando pull já saiba de onde puxar sem opções adicionais. Isso significa que, se uma conexão de rastreamento tiver sido configurada, você pode simplesmente omitir nomear o repositório remoto e o ramo:</p>
<pre><code>git pull</code></pre>

<h3>Editar mensagem do último commit<h3>

<p>Caso você queira editar a mensagem do último commit, utilize o comando <code>git commit --amend</code>. Isso vai abrir o seu editor de texto mostrando o último commit e, assim, é possível editar a mensagem.<hr>
Se não for necessário editar o corpo da mensagem, isso pode ser feito usando:</p>
<pre><code>git commit --ammend -m "Nova mensagem para o commit"</code></pre>

<h3>Adicionar mais arquivos ao último commit</h3>

<p>Para isso, também podemos usar o comando <code>git commit --amend</code>.</p>
<p>Faça as mudanças que quer adicionar ao commit mais recente, adicione essas mudanças usando <code>git add</code> e então utilize <code>git commit --amend</code>. Como citado na seção anterior, isso vai abrir o editor de texto, possibilitando que também edite a mensagem do commit.</p>
<p>Caso queira apenas adicionar mais mudanças ao commit, sem editar a mensagem, é possível fazer isso com <code>git commit --amend --no-edit</code>.</p>


<h6>Início de aside</h6>

<h2>Dicas finais</h2>
<h3>Configurar qual editor usar no Git<h3>
<p>Por padrão, o git utiliza o editor de texto do padrão do sistema (que em muitos casos é o vi) para editar mensagens de commits. Para utilizar algum outro editor é necessário alterar a configuração core.editor. Por exemplo, executando o seguinte comando:<br>
<pre><code>git config --global core.editor atom</code></pre>
<br>O Git agora vai utilizar o Atom como editor padrão. Isso vale para mensagens de commit e para outras operações do Git, como rebase interativo.</p>


<h6>Final de aside</h6>



<p>FIM!</p>