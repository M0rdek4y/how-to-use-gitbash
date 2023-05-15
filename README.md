# Como usar git simples

<h2>Fluxo de trabalho</h2>

<p>Seus repositórios locais consistem em três "árvores" mantidas pelo git. a primeira delas é sua <code>Working Directory</code>que contém os arquivos vigentes. a segunda <code>Index</code> que funciona como uma área temporária e finalmente a <code>HEAD</code> que aponta para o último commit (confirmação) que você fez.</p>


## Após a instalação do git

<h2>Configurando o git</h2>

<p>Configure o seu email de acordo com o seu git</p>
<pre><code>git config --global user.email "seuemail@gmail.com"</code></pre>

<p>Configure o seu nome de usuário de acordo do seu git</p>
<pre><code>git config --global user.name "seunome"</code><pre>

<h3>Configurar qual editor usar no Git<h3>

<p>Por padrão, o git utiliza o editor de texto do padrão do sistema (que em muitos casos é o vi) para editar mensagens de commits. Para utilizar algum outro editor é necessário alterar a configuração core.editor. Por exemplo, executando o seguinte comando:</p>
<pre><code>git config --global core.editor atom</code></pre>
<p>O Git agora vai utilizar o Atom como editor padrão. Isso vale para mensagens de commit e para outras operações do Git, como rebase interativo.</p>

## Agora podemos  começar a utilizar o git. A primeira coisa a se fazer caso você não possua um repositório é criar um.

<h2>Criando um novo repositório</h2>

<p>crie uma nova pasta, abra-a e execute o comando</p>
<pre><code>git init</code></pre>
<p>para criar um novo repositório.</p>

## Você pode já possuir um repositório

<h2>Adicionando um repositório remoto</h2>

<p>Podemos utilizar o</p>
<pre><code>git remote add origin</code></pre>
<p>O comando git remote add origin é usado para adicionar um repositório remoto existente como uma referência no seu repositório local. Isso permite que você se conecte e interaja com o repositório remoto usando comandos como git push e git pull. Em resumo é usado para adicionar um repositório remoto como um ponto de referência no seu repositório local.</p>
<p> Após criar o ponto de refência pode trazer os arquivos do repositório remoto, basta usar</p>
<pre><code>git pull origin master</code></pre>
<p>assim você está puxando o ramo(branch) master do repositório remoto origin e mesclando com o seu ramo(branch).</p>


<h2>Clonando um repositório</h2>

<p>Crie uma cópia de trabalho em um repositório local executando o comando</p>
<pre><code>git clone /caminho/para/o/repositório</code></pre>
<p>quando usar um servidor remoto, seu comando será</p>
<pre><code>git clone https:/caminho/para/o/repositório</code></pre>
<p>esses são usados para clonar um repositório existente, criando uma cópia local completa do repositório com todo o histórico de commits, branches e tags.</p>

## Caso deseje remover algum arquivo do seu repositório local

<h2>Apagando arquivos do repositório local</h2>

<p>Para remove um arquivo do seu repositório local basta usar</p>
<pre><code>rm -r "nome do arquivo"</code></pre>
<p>caso sejam vários arquivos especificos</p>
<pre><code>rm -r arquivo1.txt arquivo2.txt arquivo3.txt</code></pre>
<p>e caso queira excluir todos use</p>
<pre><code>rm -r .</code></pre>

## Agora que você criou seu repositório e adicionou seus arquivos devemos subir o arquivo para seu para a área de preparação "staging area".

<h2>Adicionando os arquivos para o index</h2>

<p>Utilize</p>
<pre><code>git add "nome-do-arquivo"</code></pre>
<p>ou adicione todos os arquivos com</p>
<pre><code>git add .</code></pre>
<p>Dessa forma os arquivos ja estarão no index.

## Caso você tenha enviado um arquivo para a index por engano pode retiralo

<h2>Removendo os arquivos do index</h2>

<p>Utilize</p>
<pre><code>git reset "seuarquivo.txt"</code></pre>
<p>ou remova todos os arquivos com</p>
<pre><code>git reset .</code></pre>
<p>Dessa forma os arquivos já estarão removidos da staging area.

## Agora podemos confirmar o envio do index para a staging area fazendo o commit.

<h2>Fazendo e desfazendo commits</h2>

<p>Para fazer o commit basta utilizar o comando:</p>
<pre><code>git commit -m "comentários das alterações"</code></pre>

<p>e caso deseje alterar o commit basta utilizar o comando:</p>

<h4>Editar mensagem do último commit<h4>

<p>Caso você queira editar a mensagem do último commit, utilize o comando <code>git commit --amend</code>. Isso vai abrir o seu editor de texto mostrando o último commit e, assim, é possível editar a mensagem.<hr>
Se não for necessário editar o corpo da mensagem, isso pode ser feito usando:</p>
<pre><code>git commit --ammend -m "Nova mensagem para o commit"</code></pre>

<p>caso tenha ja tenha feito o commit e deseja remove-lo, basta utilizar</p>
<pre><code>git reset HEAD~</code></pre>
<p>dessa forma o arquivo irá removerá o commit porém as alterações do arquivo irão permanecer.</p>
<p>Caso queira remover o arquivo da staging area e manter a cópia local do arquivo intacta ulilize:</p>
<pre><code>git rm --cached "seuarquivo.txt"</code></pre>
<p>ou para remover todos</p>
<pre><code>git rm --cached -r .</code></pre>

<h4>Adicionar mais arquivos ao último commit</h4>

<p>Para isso, também podemos usar o comando <code>git commit --amend</code>.</p>
<p>Faça as mudanças que quer adicionar ao commit mais recente, adicione essas mudanças usando <code>git add</code> e então utilize <code>git commit --amend</code>. Como citado na seção anterior, isso vai abrir o editor de texto, possibilitando que também edite a mensagem do commit.</p>
<p>Caso queira apenas adicionar mais mudanças ao commit, sem editar a mensagem, é possível fazer isso com</p>
<pre><code>git commit --amend --no-edit</code></pre>

## Baixando arquivos do repositório remoto para o repositório local

<h2>Usando o comando de <code>pull</code> simples do git</h2>

<p>O comando</p>
<pre><code>git pull</code></pre>
<p>é usado para mesclar o repositório remoto com o repositório local e atualizar o ramo(branch) atual com as alterações remotas.Ele combina os comandos <code>git fetch</code> e <code>git merge</code>.</p>

<h2>Download & Integração com <code>pull</code> do git</h2>

<p>Utilizando o comando</p>
<pre><code>git pull origin master</code></pre>
<p>podemos atualizar o repositório local com as últimas alterações do repositório remoto, especificamente da branch "master" do repositório "origin". Ele realiza dois passos em sequência: primeiro, faz um git fetch para buscar as atualizações mais recentes do repositório remoto, e depois faz um git merge para aplicar essas atualizações no branch atual do repositório local. Isso garante que o repositório local esteja atualizado com as alterações mais recentes do repositório remoto.</p>
<p>mas também podemos utilizar o comando</p>
<pre><code>git pull origin master --rebase</code></pre>
<p>assim realizando um rebase das alterações trazidas do repositório remoto com a branch local, reescrevendo o histórico de commits da branch local para que as alterações mais recentes do repositório remoto fiquem em primeiro lugar. Isso pode evitar a criação de um novo commit de merge e manter um histórico de commits mais linear e limpo.</p>

## Enviando arquivos do repositório local para o repositório remoto

<h2>Upload com push</h2>

<h3>Após fazer o commit dos arquivos, eles estarão na staging area, e para enviar os arquivos para o repositório remoto basta usar o comando</h3>
<pre><code>git push</code></pre>
<p>para enviar as alterações locais para um repositório remoto. Quando usado sem argumentos adicionais, ele envia as alterações da branch atual para a branch correspondente no repositório remoto.</p>
<p>Por exemplo, se você está atualmente na branch <code>feature</code> e deseja enviar suas alterações para a branch <code>feature</code> no repositório remoto chamado <code>origin</code>, você pode executar o comando <code>git push origin feature</code>.</p>
<p>Já o comando</p>
<pre><code>git push origin master</code></pre>
<p>envia as alterações da branch local <code>master</code> para a branch <code>master</code> no repositório remoto <code>origin</code>. Esse comando é útil quando você deseja enviar suas alterações para a branch <code>master</code> do repositório remoto.</p>
<p>É importante ressaltar que, para usar o comando <code>git push</code>, você precisa ter permissão de escrita no repositório remoto correspondente. Além disso, é recomendado verificar se o repositório remoto está atualizado antes de enviar suas alterações, para evitar conflitos com outras alterações que possam ter sido feitas no repositório remoto desde a última vez que você o atualizou localmente.</p>

### EXTRA

<h2>Comandos <code>git fetch</code> e <code>git merge</code></h2>

<p>O comando</p>
<pre><code>git fetch</code></pre>
<p>é usado para buscar as atualizações mais recentes dos branches e tags de um repositório remoto, mas não mescla as alterações em seus arquivos locais. Ele apenas atualiza as referências locais para os branches e tags remotos. Resumindo, o git fetch busca atualizações de todos os repositórios remotos configurados.</p>
<p>por outro lado</p>
<pre><code>git merge</code></pre>
<p>é usado para mesclar mudanças de uma branch para outra. Quando você executa git merge, o Git mescla as mudanças da branch atual com a branch especificada.</p>
<p>Por exemplo, se você estiver trabalhando em uma branch chamada feature, e quiser mesclar as mudanças da branch develop, você executaria o comando:</p>
<pre><code>git merge develop</code></pre>

<h2>Comandos <code>rm -r</code> e <code>rm -rf</code></h2>

<p>O comando </p>
<pre><code>rm -r</code></pre>
<p>é usado para remover diretórios e seus conteúdos recursivamente, enquanto o comando rm <code>-rf</code> é usado para forçar a remoção de diretórios e seus conteúdos recursivamente, sem fazer perguntas.</p>
<p>A opção <code>-f</code> em</p> 
<pre><code>rm -rf</code></pre> 
<p>significa "forçar", o que significa que o comando não solicitará confirmação antes de remover os arquivos ou diretórios. Portanto, é importante ter cuidado ao usar o comando rm <code>-rf</code>, pois ele pode apagar permanentemente arquivos importantes sem a possibilidade de recuperação.</p>
