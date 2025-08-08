
## configuração do GIT (atualizado na web)

O arquivo oculto ~/.gitconfig armazena as informações de configuração do usuario atual na raiz do seu HOMEDIR

-- configurando informações básicas do usuário
git config --global user.name "alasantos"
git config --global user.email aluiz.santos@gmail.com

git config init.defaultBranch - retorna a branch padrão
git config init.defaultBranch [nome novo da branch padrao] - altera a branch padrão

git config --global  => lista os comandos de configuração
git config --global [--list] => lista as configurações atuais 


- uma conta possui um nome de usuario e senha, contudo para determinadas operações, por exemplo: git push, é necessario informar também um token gerado a partir das suas credenciais básicas (user e senha) do site.


## Autenticação via Token

    O token é gerado através da conta do usuario no github, na configuração Developer settings (tokens classic).

    Consiste de uma string longa apresentada na pagina apenas uma vez durante o processo de criação.

    O token gerado valida as credenciais do usuario (login).

    O processo de criação define um escopo de atividades que o usuário poderá realizar.
    
    Exemplo: 
            git clone <url do repositorio> [pasta]
            Username <sera solicitado o login do usuario>
            Password for <url do repositório>: é aqui que colamos o token

    Para que o token fique armazenado de forma segura temos, na configuração do usuario git, a possibilidade de armazená-lo de forma transitória *cache* ou de forma permanente *store*.

    Exemplo: 
        git config --global credential.helper [cache|store]

        git config --global --show-origin credential.helper : exibe o caminho para o armazenamento de parametros globais de configuração. Neste exemplo temos o local onde estão armazenadas as credenciais

-- Autenticação via SSH

    chaves SSH ficam na pasta oculta _.ssh_ abaixo da pasta home

    Diferentemente do token, a chave SSH é gerada na máquina do usuario. 

    Primeiro instale o cliente do GIT se não tiver feito isso ainda

    IMPORTANTE: utilize o guia em https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys para verificar a existência de chaves preexistentes. Um indicador é a existência da pasta oculta _.ssh_ abaixo da pasta HOME do usuario e a existência de arquivos nela

    ## Criação da chave ##

        O acesso via protocolo SSH consiste na geração de uma chave privada e uma chave pública - a chave pública ainda conta com uma senha.

        Crie a chave de acesso SSH: ssh-keygen -t ed25519 -C "your_email@example.com"
        Será solicitado um nome de arquivo para a chave. Esse arquivo será criado na pasta _.ssh_ e caso a pasta não exista, será criada.

        Ao final da geraçao será solicitada uma senha para o arquivo. Digite ENTER caso não queira senha.

        - inserção da chave privada no computador

            Primeiro precisamos carregar o agente SSH com o comando

                eval "$(ssh-agent -s)"

            Finalmente inseriremos a chave privada com o comando

                ssh-add ~/.ssh/<id_ed25519> | <nome do arquivo com a priv. key>

        - inserção da chave privada no https://github.com/settings/ssh/new

            Inserir uma descricao, key type (Authentication Key) e o _conteudo do arquivo com a chave privada_ _*todo*_

            


- git init 

    Inicializa um repositorio local, cria uma pasta de nome _.git_ (invisível) que contém as estruturas de controle de versão

    o repositório local ainda não está vinculado a um repositorio remoto

    arquivo _.git/config_ 
        arquivo de controle principal do repositorio local

    inicia o versionamento conforme o nome do branch inicial configurado em _git config init.defaultBranch_ 


- git clone <URL> [nome da pasta local]

    um repositorio remoto, já existente no git, possui um nome e está acessivel, se público, através de sua URL

    quando clonamos um repositório remoto, a pasta que será criada terá o nome do repositorio e, para dar outro nome da pasta
    

- git remote -v 

    informa quais os repositorios vinculados à pasta GIT atual


* um repositorio local pode ja ser vinculado a 

- git remote add origin <URL do repositorio remoto>

    Apenas vincula o repositório local com o remoto




