# alura-git-controle

## 01 Controle de versão, Git, Github: o que são?

### Problemática
* o projeto esteja armazenado em um local que seja acessível a todos os membros da equipe, 
* permita ainda a atribuição de permissões para que os membros dessa equipe possam alterar os arquivos existentes, 
* permitir que novos arquivos sejam criados e 
* que arquivos existentes possam ser excluídos.

### Repositório de código

Local para armazenar os arquivos do projeto em um servidor, com redundância de dispositivos de armazenamento e backups constantes. Uma pasta compartilhada na rede em uma máquina mais segura do que uma estação de trabalho torna-se uma opção melhor.
* Controle de versão do arquivo (log)

### Instalação

`yum install git`


### Autocomplete do Git

`sudo apt-get install git bash-completion`

add to .bashrc
`
  if [ -f /usr/local/share/bash-completion/bash_completion ]; then
    . /usr/local/share/bash-completion/bash_completion
  fi
`

### GitHub

1. Open Git Bash.

2. Paste the text below, substituting in your GitHub email address.

`$ ssh-keygen -t rsa -b 4096 -C "antonioc.bessa@gmail.com" `

3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

4. At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

5. Vá em "Settings" --> "SSH and GPG keysa" --> "New SSH key"  --> COLAR conteúdo  "cat /home/antoniocbf/.ssh/id_rsa.pub"

### Clonando repositório

`git clone https://github.com/jcfonsecagit/repositorio.git `

### Controle geral de versões (tag)

`git tag`
`git checkout v0.1`


### O que mudou nos arquivos? (diff)
`git diff v0.1 v0.2`
adfas


### Quem realizou as alterações em um arquivo linha a linha (blame --> culpa)
`git blame index.html

## 02 Ciclo básico do GIT

### 1. O ciclo básico do GIT

mkdir curso-git
cd curso-git
git init #  inicia um novo repositório

### Adicionando arquivos ao repositório
git ls-files
git status # lista o estado atual de cada arquivo, caso tenha sido modificado
git add index.html # desejamos rastrear determinado arquivo, incluindo-o no controle de versão
git status
git config user.name "João Carlos Fonseca"
git config user.email "jcfonsecagit@gmail.com"
git config --global user.name "João Carlos Fonseca"
git config --global user.email "jcfonsecagit@gmail.com"
git commit -m "Início do projeto"


### Alterando o projeto
vim index.html
git status
git add index.html
git commit -m "Conteúdo da página index.html"

### Adicionando múltiplos arquivos
git add arquivo1 arquivo2
git add caminhoDeUmDiretorio
git add .

### Recapitulação do processo
* 3 estágios:
	* Working Directory: sistema de arquivos atual, alterações do momento. (limpo / sujo - dif do repo)
	* Staging Area (Index): estágio transitório, arquivo pode ser alterado, remover, adicionar (git add) 
	* HEAD: estado persistido (commitado) --- (git comiit)

### Marcando alterações interativamente
git add -i

### Commit sem criar um index
git commit -a


## 03 Sincronização dos dados com o repositório

### Criação de repositórios no github para guardar arquivso

### Configuração do repositório remoto

git remote add [alias_do_repositorio] [uri_do_repositorio]

* Uma convenção adotada é a utilização do nome do repositório remoto como "origin".
* git remote add origin https://github.com/[seu_nome_de_usuario]/curso-git

### Envio dos commits locais para o repositório
git push origin master


### Lab

`
antoniocbf@ubuntuvm:~/Projects/curso-git$ git status # estado atual do repositório - untracked (não rastreado)
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	index.html

nothing added to commit but untracked files present (use "git add" to track)
antoniocbf@ubuntuvm:~/Projects/curso-git$ git add index.html # monitore o index.html
antoniocbf@ubuntuvm:~/Projects/curso-git$ git status # temos um arquivo para ser commitado (enviada)
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   index.html

antoniocbf@ubuntuvm:~/Projects/curso-git$ # git commit -m "Criando Projeto" # gravar informações no repositório -m (passar mensagem)
antoniocbf@ubuntuvm:~/Projects/curso-git$ git config --global user.name "Antonio Bessa"
antoniocbf@ubuntuvm:~/Projects/curso-git$ git config --global user.email "antonioc.bessa@gmail.com" # configura nome e email (global - todo pc)
antoniocbf@ubuntuvm:~/Projects/curso-git$  git commit -m "Criando Projeto" # gravar informações no repositório -m (passar mensagem)
[master (root-commit) 6ef5430] Criando Projeto
 1 file changed, 6 insertions(+)
 create mode 100644 index.html
antoniocbf@ubuntuvm:~/Projects/curso-git$ git status
On branch master
nothing to commit, working tree clean


antoniocbf@ubuntuvm:~/Projects/alura-git-controle$ vim README.md 
antoniocbf@ubuntuvm:~/Projects/alura-git-controle$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
antoniocbf@ubuntuvm:~/Projects/alura-git-controle$ git log
commit 152beb2885fcc2ab43c4059ab007278b416307a5 (HEAD -> master, origin/master, origin/HEAD)
Author: antoniocbf <antoniobessa@ymail.com>
Date:   Thu Sep 26 15:01:40 2019 -0300

    Initial commit
`
