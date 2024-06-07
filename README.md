# Como configurar/instalar/usar o `Python 3.8 como padrão` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar/usar o `Python 3.8 como padrão` no `Linux Ubuntu`.

## _Abstract_

_In this document are contained the main commands and settings to set up/install the `Python 3.8 como padrão` on `Linux Ubuntu`._


## Revisão(ões)/Versão(ões)

| Revisão número | Data da revisão | Descrição da revisão                                    | Autor da revisão                                |
|:--------------:|:---------------:|:--------------------------------------------------------|:------------------------------------------------|
| 0              | 13/03/2024      | <ul><li>Revisão inicial/criação do documento.</li></ul> | <ul><li>Eden Denis F. da S. L. Santos</ul></li> |


## Controle de configuração/instalação nos Sistemas Operacionais (SO) vs. Computador

| Numero | Computador          | Sistema Operacional (SO) | Tipo de sistema | Status da configuração/instalação |
|:------:|:-------------------:|:------------------------:|:---------------:|:---------------------------------:|
| 1      | Dell Precision 7520 | Kali Linux               | Debian          | OK                                |
| 2      | Dell Precision 7520 | Linux Ubuntu             | Ubuntu          | Pendente                          |
| 3      | Dell Precision 7520 | Linux Xubuntu            | Ubuntu          | Pendente                          |
| 4      | Dell Precision 7520 | Windows 10               | Windows         | OK                                |
| 5      | Asus                | Kali Linux               | Debian          | Pendente                          |
| 6      | Asus                | Linux Ubuntu             | Ubuntu          | Pendente                          |
| 7      | Asus                | Linux Xubuntu            | Ubuntu          | OK                                |
| 8      | Asus                | Windows 10               | Windows         | Pendente                          |

### Legenda

- **N/A:** **NOT** apllicable/**NÃO** aplicável
- **OK:** Zero killed

## Descrição [2]

### `Python`

Python é uma linguagem de programação de alto nível, interpretada e multiparadigma, conhecida por sua simplicidade e legibilidade. Criada por Guido van Rossum e lançada em 1991, Python oferece uma sintaxe clara e concisa, tornando-a ideal para iniciantes e experientes. Sua ampla biblioteca padrão e vasta comunidade de desenvolvedores facilitam a criação de uma variedade de aplicativos, desde scripts simples até aplicativos web complexos, aprendizado de máquina e ciência de dados. Python é valorizado por sua portabilidade, interoperabilidade e escalabilidade, sendo uma escolha popular em muitas áreas da computação e além.

### `shell`

Um `shell` é uma interface de linha de comando que permite aos usuários interagir com um sistema operacional por meio de comandos de texto. Ele interpreta os comandos do usuário e os executa, fornecendo acesso a recursos do sistema, como arquivos, processos e dispositivos. Os shells variam em funcionalidades e complexidade, com exemplos comuns incluindo o Bash (Bourne Again Shell), PowerShell, Zsh (Z Shell) e o `shell` padrão do Unix. Eles são essenciais para administradores de sistemas, desenvolvedores e usuários avançados que precisam de controle direto sobre seus sistemas operacionais.


## 1. Como configurar/instalar/usar o `Python 3.8 com padrão` no `Linux Ubuntu` [1]

Para configurar/instalar/usar o `Python 3.8 como padrão` no `Linux Ubuntu`, você pode seguir estes passos:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes APT. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo APT e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando: `sudo apt clean` 
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: `sudo apt update -y`

    2.5 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  `sudo apt list --upgradable`

    2.6 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update -y`. Digite o seguinte comando e pressione `Enter`: `sudo apt full-upgrade -y`

    2.7 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.8 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

Para configurar o `Python 3.8` como padrão no Linux Ubuntu, você pode usar o update-alternatives para gerenciar diferentes versões do Python. Primeiro, você precisa garantir que o `Python 3.8` esteja instalado no seu sistema. Aqui está o passo a passo:

1. **Instalar o `Python 3.8`:** Se o `Python 3.8` não estiver instalado, você pode instalá-lo usando o apt ou compilando-o a partir do código-fonte. Verifique se o `Python 3.8` já está instalado executando `python3.8` no terminal. Se não estiver instalado, você pode procurar um PPA apropriado ou compilar a partir do código-fonte.

2. Primeiramente, vamos verificar a localização exata das instalações do Python. Vamos começar verificando onde o `Python 3.8` está instalado (se estiver). Você pode encontrar o caminho exato usando o comando `which` para versões específicas do Python. Por exemplo: `which python3.8`

    2.1 Se esse comando não retornar um caminho, significa que o `Python 3.8` não está instalado ou não está disponível no `PATH`. Se você tiver certeza de que instalou o `Python 3.8`, você pode tentar localizá-lo usando o comando `find`: `sudo find / -name 'python3.8'`

    Esse comando procura em todo o sistema de arquivos o executável `python3.8`. Se você encontrar o caminho para o `Python 3.8`, você deverá usar esse caminho ao configurar o `update-alternatives` a seguir.

    2.1 **Configurar o `update-alternatives`:** O `update-alternatives` permite gerenciar diferentes versões de um comando através de links simbólicos. Primeiro, você deve adicionar o `Python 3.8` ao `update-alternatives` e depois configurá-lo como a versão padrão. Aqui estão os comandos que você pode usar:

        ```
        sudo update-alternatives --install /usr/bin/python python /usr/local/bin/python3.8 1
        sudo update-alternatives --install /usr/bin/python python /usr/local/bin/python3.11 2
        sudo update-alternatives --config python
        ```

    Durante o uso do `update-alternatives --config python`, um prompt aparecerá para que você selecione a versão do `Python` desejada. Selecione a opção correspondente ao `Python 3.8`.

3. **Verificar a configuração:** Depois de configurar o `update-alternatives`, você pode verificar se o `Python 3.8` está configurado corretamente como padrão usando o comando: `python --version`

    Se tudo estiver correto, a saída deve mostrar `Python 3.8`. Se você encontrar algum problema, certifique-se de que todos os caminhos e versões estão corretos nos comandos do `update-alternatives`.


```python
Se você já configurou o `update-alternatives` para usar o `Python 3.8`, mas ainda assim o comando python aponta para o `Python 3.11.5`, isso pode estar acontecendo porque o `shell` pode estar usando um `cache` dos caminhos dos executáveis. Para resolver isso, você pode tentar as seguintes abordagens:

4. **Reiniciar o Shell:** Às vezes, simplesmente fechar e abrir um novo terminal pode resolver o problema, pois isso limpa o `cache` do `shell`.

```

5. **Verificar o `alias`:** Confira se existe algum `alias` configurado para o comando `Python` que está apontando para a versão `3.11`. Você pode verificar isso com o comando: `alias`

    Se houver um `alias` para o `Python`, você pode removê-lo adicionando uma linha no seu arquivo de configuração do `shell` (como `.bashrc` ou `.zshrc`): `unalias python`
    
    Depois, aplique as alterações com o comando `source ~/.bashrc` ou  `source ~/.zshrc`, dependendo do seu `shell`.

6. **Pesquisar onde o `Python 3.8`está:** Digite o comando:  `which python3.8`

7. **Modificar diretamente a chamada para Python:** Se nenhuma das opções acima resolver, você pode forçar a versão desejada do Python criando um alias em seu arquivo de perfil do `shell` (`~/.bashrc`, `~/.zshrc` etc.): `alias python='/usr/local/bin/python3.8'`

    Depois, aplique a alteração com `source ~/.bashrc` ou o arquivo correspondente do seu `shell`.

7. Após realizar essas etapas, abra um novo terminal e digite `python --version` para verificar se agora aponta para a versão correta, `Python 3.8`.



## 2. Código completo para configurar/instalar/usar

Para configurar/instalar/usar o `Python 3.8` no `Linux Ubuntu`sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Digite o seguinte comando e pressione `Enter`:

    ```
    NÂO há.
    ```


## 3. Configurar o ambiente virtual `base` para ser o `Python 3.8` no `Anaconda3`

Para verificar se você tem o Anaconda instalado no seu computador e, especificamente, se é uma versão que inclui o `Python 3.8`, você pode seguir estes passos:

1. **Verificar a Versão do Anaconda:** Abra um terminal e digite o seguinte comando: `conda --version`

    Este comando retornará a versão do conda instalada, se o `Anaconda` ou `Miniconda` estiver instalado no seu sistema.

2. **Verificar a Lista de Ambientes do `Conda`:** Para ver uma lista de todos os ambientes do conda criados, que podem incluir um ambiente com o `Python 3.8`, use: `conda env list`

Para definir o `Python 3.8` como a versão do `Python` no ambiente `base` do seu `Anaconda`, você precisará atualizar o `Python` nesse ambiente. Este processo substituirá a versão atual do `Python` (`3.11.5`, por exemplo) pela versão `3.8` no ambiente `base`. Aqui está como você pode fazer isso:

1. **Abra um Terminal:** Certifique-se de que você está no ambiente `base` do `Anaconda`. Se não estiver, você pode ativar o ambiente `base` com o comando: `conda activate base`

2. **Atualizar o `Python` para a Versão `3.8`:** Use o comando `conda install` para especificar a versão do `Python` que deseja instalar no ambiente `base`. Execute o seguinte comando: `conda install python=3.8`

    Esse comando solicitará que o `Conda` atualize o `Python` e possivelmente alguns pacotes dependentes para garantir compatibilidade com o `Python 3.8`. Siga as instruções na tela para confirmar a instalação.

3. **Verificar a Versão do `Python`:** Após a conclusão da instalação, verifique a versão do `Python` para garantir que a atualização foi bem-sucedida: `python --version`

    A saída deve mostrar `Python 3.8.x`, confirmando que o ambiente `base` agora está usando o `Python 3.8`.

## 4. Desinstalar o `Python 3.11`

    Para desinstalar o `Python 3.11` no `Linux Ubuntu` através do `Terminal`, é importante considerar se o `Python 3.11` foi instalado manualmente (por exemplo, compilado a partir do código-fonte) ou através do gerenciador de pacotes do sistema (`apt`). A abordagem para desinstalação pode variar dependendo disso. É essencial ter cautela ao desinstalar versões do `Python`, pois isso pode afetar a estabilidade do sistema, especialmente se o `Python` em questão for usado por aplicativos do sistema.

### 4.1 Se o `Python 3.11` foi instalado via `apt`

1. **Verificar o Pacote a Ser Removido**: Primeiro, você precisa encontrar o nome exato do pacote `Python 3.11` instalado. Você pode usar o comando a seguir para listar os pacotes relacionados ao `Python 3.11`: `apt list --installed | grep python3.11`

2. **Desinstalar o Pacote**: Uma vez que você sabe o nome do pacote, você pode desinstalá-lo usando sudo `apt remove`. Por exemplo:

    ```
    sudo apt remove python3.11
    sudo apt autoremove
    ```

    O comando `autoremove` é usado para remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que agora não são mais necessários.

### 4.2 Se o Python 3.11 foi instalado manualmente (por exemplo, compilado a partir do código-fonte):

    Se você instalou o `Python 3.11` compilando-o a partir do código-fonte, o processo de desinstalação envolve a remoção manual dos diretórios e arquivos associados. Se você seguiu o procedimento padrão de instalação (`./configure`, `make`, `sudo make altinstall`), o Python provavelmente está instalado em `/usr/local`.

1. **Remover os Arquivos Binários**: Você precisa remover o executável do `Python` e outros arquivos relacionados manualmente. Se você usou `make altinstall`, o Python deve estar instalado como `python3.11` em `/usr/local/bin`. Você pode remover o binário com: `sudo rm /usr/local/bin/python3.11`

2. **Remover os Diretórios de Instalação**: Além disso, você terá que encontrar e remover os diretórios associados à instalação do `Python 3.11`, como bibliotecas e compartilhamentos. Esses diretórios podem incluir:

    ```
    sudo rm -r /usr/local/lib/python3.11
    sudo rm -r /usr/local/include/python3.11
    ```

E qualquer outro diretório específico para a versão `3.11` que você possa ter instalado.

**Precauções:**

- **Tenha Cuidado ao Remover Pacotes**: Remover pacotes essenciais pode comprometer o sistema. Antes de desinstalar, confirme se o pacote que você está prestes a remover não é uma dependência crítica do sistema.

- **Backup**: Considere fazer backup de arquivos importantes antes de realizar essas operações.
Alternativa: Usar Ambientes Virtuais:
Em vez de desinstalar o `Python 3.11`, considere o uso de ambientes virtuais (por exemplo, com `venv` ou `conda`) para gerenciar versões diferentes do `Python`. Isso permite que você use múltiplas versões do `Python` em projetos separados sem a necessidade de alterar a instalação do `Python` no sistema.

## Referências

[3] OPENAI. ***Python 3.8.10 como padrão.*** Disponível em: <https://chat.openai.com/c/14954993-8694-4c0e-b1ec-44fe5eccf0e7> (texto adaptado). Acessado em: 13/03/2024 13:47.

[2] OPENAI. ***Vs code: editor popular.*** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). Acessado em: 13/03/2024 13:48.


