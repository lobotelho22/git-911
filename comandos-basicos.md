# Comandos Básicos

## git --help

O comando `git --help` é um bom princípio para se buscar comandos para realizar as mais diversas ações com o hit. Seu retorno é o seguinte:

``` bash
usage: git [--version] [--help] [-C <path>] [-c name=value]
       [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
       [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
       [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
       <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Forward-port local commits to the updated upstream head
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
```

Podemos consultar um guia de ajuda de um comando específico, digitando: `$ git <comando> --help`.

<br />

## git status

Talvez um dos comandos que mais iremos utilizar. `git status` exibe o estado atual da árvore de trabalho. Isso possibilita que se confira as alterações que estão sendo monitoradas pelo git.

Seu retorno é algo como:

``` bash
No ramo starting

No commits yet

Arquivos não monitorados:
  (utilize "git add <arquivo>..." para incluir o que será submetido)
    README.md
    comandos-basicos.md

nada adicionado ao envio mas arquivos não registrados estão presentes (use "git add" to registrar)
```

<br />

## git add

O comando `git add` é utilizado para adicionar os arquivos que irão fazer parte de um *commit*. Muitas vezes utilizamos o comando `$ git add .` para adicionarmos todos os arquivos do nosso projeto.

<br />

## git commit

Com esse comando, nós fazemos o instantâneo do estado atual dos nossos arquivos. Além do estado atual da aplicação, o commit armazena dados do autor do commit, a data da realização e os comentários feitos. Para fazer o commit acompanhado de comentários, utilizamos a flag `-m`. Exemplo: `$ git commit -m 'configuração inicial`.

Um comportamento de padronização de mensagens de commit sugere que a primeira linha de um commit seja a breve descrição da alteração realizada. Essa linha não deve ter mais que 50 caracteres. Ela deve ser seguida por uma linha em branco e, caso o commit tenha mais linhas, elas não devem ultrapassar os 72 caracteres.

O ideal é sempre realizar pequenos commits, para registrar as alterações realizadas e facilitar a recuperação de estados anteriores.

<br />

### Corrigindo um commit

Utilizamos a opção `--amend` para corrigirmos um commit.Caso, por exemplo tenhamos feito um commit com um arquivo que tenha um pequeno erro. Podemos corrigir esse erro e *reutilizar* o último commit feito.

Se utilizarmos a opção `--no-edit`, indicamos que manteremos a mesma mensagem de commit. Podemos com o *amend* editar também a mensagem do commit.

``` bash
git commit --amend --no-edit
```

<br />

## git log

O comando `git log` exibe informações sobre os commits anteriores. Ele exibe uma lista com os nomes dos autores, as datas de realização, os comentários de identificação e apronta qual é o commit `HEAD` do processo.

<br />

## git diff

Esse comando exibe as diferenças, se houverem, entre os arquivos da árvore de trabalho e os arquivos das últimas adições preparadas no último `git add`. Para comparar essas alterações com o último commit, use `$  git diff HEAD`.

<br />

## git checkout

O `git checkout` é um comando de vários usos. Um deles é o de recuperação de arquivos excluídos por acidente. Podemos fazê-lo da seguinte forma:

``` bash
git checkout -- <nome_do_arquivo>
```

O sinal `--` é necessário para que o git evite uma possível confusão com uma branch de mesmo nome.

<br />

## git reset

Esse comando remove o preparo de alterações em uma branch ou arquivo. No caso de um arquivo que tenha sido exlcuído do disco e do git, com um comando `git rm <nome_do_arquivo>`, por exemlo, podemos recuperar o arquivo da seguinte forma:

``` bash
git reset HEAD <nome_do_arquivo>
git checkout -- <nome_do_arquivo>
```

Na sequência dos comando acima, removemos o preparo da exclusão do arquivo, feita com o `git rm` e recuperamos a versão dele excluída do git. Na sequência, o `checkout` faz a recuperação da última versão do arquivo para o disco.

Podemos, também, utilizar esse comando para removermos um commit. Se for o caso de excluir o commit mais recente, executamos:

``` bash
git reset --hard HEAD^
```

Há alguns padrões para essa operação. O default é o `--mixed`, que redefine o índice sem alterar a árvore de trabalho e que também pode mover o `HEAD` para um commit escpecificado pelo usuário. Podemos utilizar a opção `--sort` para movermos o `HEAD`, deixando tudo intacto, com status de alterações pendentes de um commit. A opção `--hard` utilizada no exemplo acima altera índice e árvore de trabalho, para que correspondam ao commit esfecificado e tudo o mais é descartado.

<br />

## git revert

O comando `git revert` faz a reversão de commits. Ele funciona fazendo um *novo commit* que *cancela* as alterações do último commit realizado. Para isso, executamos o comando:

``` bash
git reset HEAD
```

## git clone

Esse comando realiza a cópia do conteúdo de um repositório git para armazená-lo em uma outra máquina. O git clone precisa de um caminho para os arquivos, que pode ser uma URL ou um SSH

## git pull

Ao clonar um repositório remoto, o git cria uma referência a ele, utilizando o nome `origin`. A operação do `git pull` é atualizar o repositório local com o repositório de origem. É uma operação que aponta do remoto até a origem.

## git request-pull

O comando efetua uma solicitação para realizar o pull de uma branch indicada. Por exemplo:

``` bash
git request-pull -p origin/main
```

É uma linha de código muito utilizada quando trabalhamos em grupo em um projeto git de terceiros. Nela estamos solicitando permissão de atualização na branch `main` no repositório remoto (`origin`), copiando a árvore de trabalho alterada por nós.

<br />

## git remote

Esse comando é utilizado para configurar um repositório como repositório remoto. Esse repositório é que será utilizado por uma equipe, para ser clonado e atualizado via `git pull` ou `git request-pull`.
