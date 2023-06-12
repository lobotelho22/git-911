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

<br />

## git log

O comando `git log` exibe informações sobre os commits anteriores. Ele exibe uma lista com os nomes dos autores, as datas de realização, os comentários de identificação e apronta qual é o commit `HEAD` do processo.
