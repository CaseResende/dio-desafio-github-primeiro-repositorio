# Git e GitHub

## Primeiros passos

- Para configurar o Git:
    Devemos entrar com o comando:


        `git config –global user.name “Carlos André"`

    Depois o email:

        git config –global user.email carlos_andre_resende@yahoo.com.br

- Alterar a Branch padrão:

        git config –global init.defaultBranch main

- Clonar um repositório:

        git clone URL

Ex:
        git clone `https://github.com/CaseResende/hello-world.git`

- Para salvar as credenciais e não ter que ficar inserindo toda hora, digite o seguinte comando:

        git config –global credential.helper store


## Criando e clonando repositórios:

Existem duas formas de obter um repositório Git na sua máquina:

1. Transformando um diretório local que não está sob controle de versão, em um repositório Git;

    - Para criar a pasta, devemos executar o seguinte comando:

            mkdir Nome-da-pasta

        Ex:
        
            mkdir repo-local

        Para abrir a pasta,

            cd repo-local/

    - Para transformar em um repositório git

            git init

    - Para verificar se o repositório está vinculado a um repositório remoto, devemos executar o comando:

            git remote -v

    - Para vincular o repositório local a um repositório remoto:

            git remote add nome-do-repositório URL

        Por padrão, o nome do repositório remoto é origin

            git remote add origin https://github.com/CaseResende/hello-world.git

2. Clonando um repositório Git existente.

    - Se quiser alterar o nome do repositório ao clonar, basta inserir o novo nome ao final do comando git clone.

            git clone URL novo-nome-da-pasta

            git clone https://github.com/CaseResende/hello-world.git novo-repositorio

    - Para selecionar apenas uma branch na clonagem do repositório, basta indicá-la no comando:

	        git clone URL –branch nome-da-branch –single-branch

            git clone https://github.com/CaseResende/hello-world.git –branch feature1 –single-branch

	    Se não passar o nome da branch, ela clona apenas a principal (master ou main)

## Salvar alterações no repositório

Com o repositório local criado e inicializado no git (comando git init), executamos o comando git status para verificar o status do repositório, sem tem algum arquivo na fila para dar commit, por exemplo.

- Para adicionar o arquivo a área de preparação:

        git add Nome-do-arquivo
        git add readme.md

- Assim o arquivo fica na área de preparação, ainda não está salvo.

        git commit -m”mensagem”
        git commit -m”commit inicial”

- Ele cria o commit, ou seja, salva o arquivo no repositório remoto, com a mensagem gravada no log, para saber qual versão e o porquê de ter sido salvo.

- Com o comando git log, conseguimos ver o commit realizado, por quem foi feito e qual a mensagem anexada.

- O git não reconhece pastas vazias. Sempre que for criar uma pasta vazia, devemos criar, também, um arquivo .gitkeep.

- Ignorar um diretório no commit: Adicionamos a pasta ao arquivo .gitignore.

- Para inserir todos os arquivos ou diretórios na fila do commit de uma só vez:

        git add .

- Para remover uma pasta do repositório git

    Devemos remover a pasta .gt dela, para isso é só executar o comando:

        rm -rf .git

- Para restaurar um arquivo da árvore de trabalho (voltar a versão que está armazenada no repositório remoto) usamos o comando:

        git restore Nome-do-arquivo
        git restore README.md

- Para alterar o nome do último commit:

        git commit –amend -m”Mensagem-nova”

- Para desfazer o último commit, devemos copiar o hash do commit que queremos desfazer (o código apresentado quando executamos o git log):

- Temos 4 opções para desfazer o commit:

    1. **Soft** - volta os arquivos dos commits posteriores para a área de preparação.

            git reset –soft hash-do-commit

    2. **Mixed** - forma padrão do comando git reset, ele tira os arquivos dos commits posteriores e também da área de preparação.

            git reset –mixed hash-do-commit

    3. **Hard** - Ele volta para o commit desejado ignorando todos os arquivos dos outros commits posteriores.

	        git reset –mixed hash-do-commit

    4. Remover os arquivos da área de preparação:

	        git reset nome-do-arquivo
	
	    ou
	
	        git restore –staged nome-do-arquivo

- Para enviar os arquivos do repositório local para o repositório remoto, devemos sincronizar com o repositório remoto:

        git remote add origin URL

    Depois devemos enviar os arquivos para o repositório remoto:

        git push -u origin main

- Para atualizar o repositório local com as alterações realizadas no repositório local, usamos o comando:

        git pull


## Branches

Branch é uma ramificação do projeto.
É um ponteiro móvel para um commit no histórico do repositório.
Quando você cria uma nova Branch a partir de outra existente, a nova se inicia apontando para o mesmo commit da Branch que estava quando foi criada.

- Para trocar a branch para uma nova branch, usamos o comando:

        git checkout -b nova-branch
        git checkout -b teste

- Para alterar para uma branch já existente:

        git checkout nome-da-branch
        git checkout main

- Para mesclar branches, devemos estar na branch que queremos manter os arquivos e executamos o comando:

        git merge nome-da-branch-que-desejamos-mesclar
        git merge teste

- Para excluir uma branch:

        git branch -d nome-da-branch
        git branch -d teste

