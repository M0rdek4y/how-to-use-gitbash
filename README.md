# Como usar git simples

<h2>Fluxo de trabalho</h2>

<p>Seus repositórios locais consistem em três "árvores" mantidas pelo git. a primeira delas é sua <code>Working Directory</code>que contém os arquivos vigentes. a segunda <code>Index</code> que funciona como uma área temporária e finalmente a <code>HEAD</code> que aponta para o último commit (confirmação) que você fez.</p>


## Após a instalação do git

<h2>Configurando o git</h2>

<p>Configure o seu email de acordo com o seu git</p>
<pre><code>git config --global user.email "seuemail@gmail.com"</code></pre>

<p>Configure o seu nome de usuário de acordo do seu git</p>
<pre><code>git config --global user.name "seunome"</code></pre>

<h3>Configurar qual editor usar no Git</h3>

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
<p>Lembrando que ao utilizar o comando:</p>
<pre><code>git remote add origin</code></pre>
<p>futuramente pode ser que tenha problemas com o controle remoto com a URL especificada que não encontrará o branch local main ao tentar rastrear o branch remoto main. Assim, quando você fizer git pull ou git push no branch local main, o Git não saberá automaticamente para onde buscar e enviar as alterações. caso isso aconteça poderá facilmente corrigir utilizando:</p>
<pre><code>git branch --set-upstream-to=origin/"branch" "branch"</code></pre>
<p>assim o Git saberá automaticamente para onde buscar e enviar as alterações.
caso durante a criação do repositório local queira evitar esse problema, bastar utilizar o comando:</p>
<pre><code>git remote add origin -t main</code></pre>
<p>Quando você utiliza o parâmetro -t main ou --track main, você está especificando que o branch local que você está criando (nesse caso, main) deve rastrear o branch remoto de mesmo nome (main). Isso significa que o Git configurará automaticamente a relação de rastreamento entre os dois branches. Quando você fizer git pull ou git push sem especificar um branch, o Git saberá para onde buscar e enviar as alterações com base na configuração de rastreamento.
Essencialmente, o uso do -t ou --track economiza tempo, evitando que você precise definir manualmente o rastreamento entre branches após adicionar o controle remoto.
Dessa forma o controle remoto com a URL especificada e definirá automaticamente o branch local main para rastrear o branch remoto main. Assim, quando você fizer git pull ou git push no branch local main, o Git saberá automaticamente para onde buscar e enviar as alterações.</p>
<p> Após criar o ponto de refência pode trazer os arquivos do repositório remoto, basta usar</p>
<pre><code>git pull origin main</code></pre>
<p>assim você está puxando o ramo(branch) main do repositório remoto origin e mesclando com o seu ramo(branch).</p>
<p>caso os comando ainda não funcionem e não deseja utilizar um comando de upstream pode tentar utilizaro seguinte comando:</p>
<pre><code>git push -u origin main</code></pre>
<p>Dessa forma o upstream é definido altomaticamente e de forma simplificada</p>
<p>Devemos nos lembrar que em repositórios já existêntes, sua criação ja está vinculada com o master por padrão, e caso ocorra de você ter excluido a branch e também não possa fazer um merge, podemos retirar essa limitação com o seguinte comando:</p>
<pre><code>git branch --unset-upstream</code></pre>
<p>dessa forma conseguimos desvincular qualquer branch vinculada ao upstream</p>

<p>Caso não funcione o pull e o push você pode tentar:</p>
<p>Adicione a origem remota ao repositório local (pule esta etapa caso ja tenha adicionado a origem remota no seu repositório local)</p>
<pre><code>git remote add origin https://github.com/seuusuario/seurepositorio.git</code></pre>
<p>use o</p>
<pre><code>git pull --set-upstream origin main</code></pre>
<p>para fazer o pull ja redirecionando pull para que nas proximas vezes possa usar somente o <code>git pull</code> adicione os arquivos que você deseja e após isso faça o commit normalmente
agora para fazer o <code>git push</code> provavelmente vai dar erro pois o Git detecta que os históricos da sua branch local e da remota não têm nada em comum ou seja as linhas do tempo de
commits do projeto local e remoto estão diferentes e para resolver isso pode fazer da seguinte maneira, se o projeto é novo apenas use o: </p>
<pre><code>git push origin main --force</code></pre>
<p>Dessa forma você irá sobrescrever o repositório remoto com o que está local e o problema estará resolvido caso o repositório seja mais antigo e ja o utlize a algum tempo, uma das maneira de solucionar é
Se você quer mesmo unir os dois históricos (ou só precisa puxar o que está no remoto), use a flag --allow-unrelated-histories:
unir os dois históricos (ou só precisa puxar o que está no remoto), use a flag <code>--allow-unrelated-histories</code></p>
<pre><code>git pull origin nome-da-branch --allow-unrelated-histories</code></pre>
<p>Exemplo comum:</p>
<pre><code>git pull origin main --allow-unrelated-histories</code></pre>
<p>Depois disso, resolva possíveis conflitos se houver, faça commit, e então você poderá dar <code>git push</code> normalmente com:</p>
<pre><code>git push origin main</code></pre>
<p>ou</p>
<pre><code>git push -u origin main</code></pre>


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

## Após atualizações do GITHUB estão ocorrendo implementações e alterações na branch que comumente era main e está sendo alterada para main.

<h2>Alterando a branch de main para main</h2>
<p>Utilize o comando</p>
<pre><code>git checkout "nome_da_branch"</code></pre>
<p>Dessa forma você troca para uma nova branch</p>
<p>Caso não tenha uma nova branch, você pode utilizar o comando</p>
<pre><code>git checkout -b "nome da nova branch"</code></pre>
<p>a utilização do parametro "-b" verifica se a branch existe e caso não exista ela cria e depois faz a troca para a nova branch</p>
<p>Dessa forma alteramos a branch de main para main</p>
<p>Caso queira apenas criar uma nova branch pode utilizar do comando:<p>
<pre><code>git branch "nome_da_branch"</code></pre>
<p>Caso queira excluir uma branch do repositório (maquina virtual) remoto utilize de:</p>
<pre><code>git push origin :"nome_da_branch"</code></pre>
<p>Mas também pode ser utilizado o comando abaixo:</p>
<pre><code>git push origin --delete "nome_da_branch"</code></pre>
<p>Caso queira excluir uma branch do repositorio local (sua maquina) utilize de:</p>
<pre><code>git branch :"nome_da_branch"</code></pre>
<p>Mas também pode ser utilizado o comando abaixo:</p>
<pre><code>git branch -d "nome_da_branch"</code></pre>
<p>Caso queira ver se a branch está no repositório local, ou na sua maquina local use:</p>
<pre><code>git branch</code></pre>
<p>Caso queira ver se a branch está no repositório remoto, ou na sua maquina remoto:</p>
<pre><code>git branch -a</code></pre>

## Devemos utilizar o fetch

<h2>utilizando o fetch</h2>
<p>Utilize o comando</p>
<pre><code>git fetch --prune --all</code></pre>
<p>Os parâmetros utlizados servem para atualizar o repositório remoto para o local, retire os branchs apagados e outros dados inválidos</p>

## Agora que você criou seu repositório e adicionou seus arquivos devemos subir o arquivo para seu para a área de preparação "staging area".

<h2>Adicionando os arquivos para o index</h2>

<p>Utilize</p>
<pre><code>git add "nome-do-arquivo"</code></pre>+
<p>ou adicione todos os arquivos com</p>
<pre><code>git add .</code></pre>
<p>Dessa forma os arquivos ja estarão no index.</p>

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

<p>Caso você queira editar a mensagem do último commit, utilize o comando <code>git commit --amend</code>.<br>Isso vai abrir o seu editor de texto mostrando o último commit e, assim, é possível editar a mensagem.<hr>
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
<p>Faça as mudanças que quer adicionar ao commit mais recente, adicione essas mudanças usando <code>git add</code><br>e então utilize <code>git commit --amend</code>.<br>Como citado na seção anterior, isso vai abrir o editor de texto, possibilitando que também edite a mensagem do commit.</p>
<p>Caso queira apenas adicionar mais mudanças ao commit, sem editar a mensagem, é possível fazer isso com</p>
<pre><code>git commit --amend --no-edit</code></pre>

## Baixando arquivos do repositório remoto para o repositório local

<h2>Usando o comando de <code>pull</code> simples do git</h2>

<p>O comando</p>
<pre><code>git pull</code></pre>
<p>é usado para mesclar o repositório remoto com o repositório local e atualizar o ramo(branch) atual com as alterações remotas.<br>Ele combina os comandos <code>git fetch</code> e <code>git merge</code>.</p>

<h2>Download & Integração com <code>pull</code> do git</h2>

<p>Utilizando o comando</p>
<pre><code>git pull origin main</code></pre>
<p>podemos atualizar o repositório local com as últimas alterações do repositório remoto, especificamente da branch "main" do repositório "origin".<br> Ele realiza dois passos em sequência: primeiro, faz um git fetch para buscar as atualizações mais recentes do repositório remoto, e depois faz um git merge para aplicar essas atualizações no branch atual do repositório local.<br> Isso garante que o repositório local esteja atualizado com as alterações mais recentes do repositório remoto.</p>
<p>mas também podemos utilizar o comando</p>
<pre><code>git pull origin main --rebase</code></pre>
<p>assim realizando um rebase das alterações trazidas do repositório remoto com a branch local, reescrevendo o histórico de commits da branch local para que as alterações<br> mais recentes do repositório remoto fiquem em primeiro lugar. Isso pode evitar a criação de um novo commit de merge e manter um histórico de commits mais linear e limpo.</p>

## Enviando arquivos do repositório local para o repositório remoto

<h2>Upload com push</h2>

<h3>Após fazer o commit dos arquivos, eles estarão na staging area, e para enviar os arquivos para o repositório remoto basta usar o comando</h3>
<pre><code>git push origin main</code></pre>
<p>envia as alterações da branch local <code>main</code> para a branch <code>main</code> no repositório remoto <code>origin</code>. Esse comando é útil quando você deseja enviar suas alterações para a branch <code>main</code> do repositório remoto.</p>
<p>É importante ressaltar que, para usar o comando <code>git push</code>, você precisa ter permissão de escrita no repositório remoto correspondente.<br>Além disso, é recomendado verificar se o repositório remoto está atualizado antes de enviar suas alterações, para evitar conflitos com outras alterações que possam ter sido feitas no repositório remoto desde a última vez que você o atualizou localmente.</p>
<p>Agora se não deseja ficar utilizando o <code>git push origin main</code> e quer usar comando simples <code>git push</code> basta utilizar o comando</p>
<pre><code> git push --set-upstream origin main</code></pre>
<p>com isso o git irá sincronizar a branch local com a branch do repositório e dessa forma das proximas vezes que for utilizar o comando, basta utlizar o <code>git push</code>
<pre><code>git push</code></pre>
<p>para enviar as alterações locais para um repositório remoto. Quando usado sem argumentos adicionais, ele envia as alterações da branch atual para a branch correspondente no repositório remoto.</p>
<p>Por exemplo, se você está atualmente na branch <code>feature</code> e deseja enviar suas alterações para a branch <code>feature</code> no repositório remoto chamado <code>origin</code>, você pode executar o comando <code>git push origin feature</code>.</p>

### EXTRA

<h2>Comandos <code>git fetch</code> e <code>git merge</code></h2>

<p>O comando</p>
<pre><code>git fetch</code></pre>
<p>é usado para buscar as atualizações mais recentes dos branches e tags de um repositório remoto,<br>mas não mescla as alterações em seus arquivos locais. Ele apenas atualiza as referências locais para os branches e tags remotos. Resumindo,<br>o git fetch busca atualizações de todos os repositórios remotos configurados.</p>
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
<p>significa "forçar", o que significa que o comando não solicitará confirmação antes de remover os arquivos ou diretórios.<br>Portanto, é importante ter cuidado ao usar o comando rm <code>-rf</code>,pois ele pode apagar permanentemente arquivos importantes sem a possibilidade de recuperação.</p>

<h2>Gerenciando arquivos grandes</h2>

<p>Se você estiver usando o Windows e o Git estiver configurado para não aceitar caminhos longos, voce pode enfrentar problemas como </p>
<code>error: could not lock config file C:/Program Files/Git/etc/gitconfig: Permission denied</code>
<p> ao tentar manipular os arquivos, como fazer um <code>git pull</code> para baixar as alterações de um repositório ou um <code>git clone</code> para clonar um repositório seu sistema e os ao ser baixado ele vem sem os arquivos grandes, ou até mesmo quando você der um <code>git push</code> para enviar os arquivos para o repositório, e você ter erros ou até mesmo os arquivos irem para o repositório porém os arquivos grandes não serem adicionados ao repositório</p>
<p>e para resolver isso  podemos abrir o <a href="https://git-scm.com/downloads">Git</a> com permissões de adminstrador e utilizar o comando:</p>
<pre><code>git config --system core.longpaths true</code></pre>
<p>dessa forma você habilita o suporte a caminhos longos, e permite que o Git manipule caminhos longos.</p>
