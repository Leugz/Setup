# Ambiente de Desenvolvimento

Este repositório contém um tutorial resumido para minha configuração de ambiente de desenvolvimento com WSL, Chocolatey, Zsh, Oh My Zsh, NVM (Node Version Manager) e várias ferramentas úteis para produtividade. Abaixo estão os passos detalhados para configurar o ambiente e as extensões recomendadas para o VSCode.

## Índice

1. [Requisitos](#requisitos)
2. [Instalação do WSL](#instalação-do-wsl)
3. [Instalar Chocolatey](#instalar-chocolatey)
4. [Instalar o Hyper](#instalar-o-hyper)
5. [Atualizar o Sistema Linux (WSL)](#atualizar-o-sistema-linux-wsl)
6. [Instalar Zsh e Oh My Zsh](#instalar-zsh-e-oh-my-zsh)
7. [Instalar e Configurar NVM](#instalar-e-configurar-nvm-node-version-manager)
8. [Instalar o Tema Powerlevel10k](#instalar-o-tema-powerlevel10k)
9. [Extensões do VSCode](#extensões-do-vscode)

## Requisitos

Antes de começar a configuração, certifique-se de ter os seguintes itens:

- **Windows 10 ou 11** (para usar o WSL)
- **Hyper** (terminal recomendado para WSL)
- **Git**
- **VSCode**
- **WSL 2** (Windows Subsystem for Linux)

## Instalação do WSL

1. **Ativar WSL e Virtual Machine Platform:**

    No PowerShell (como Administrador), execute:

    ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
    ```

    Reinicie o computador após executar esses comandos.

2. **Instalar uma Distribuição Linux:**

    - Após a instalação do WSL, você pode instalar uma distribuição Linux a partir da Microsoft Store (ex: Ubuntu).

3. **Atualizar o WSL para versão 2 (caso não tenha feito automaticamente):**

    Execute o comando:

    ```bash
    wsl --set-default-version 2
    ```

4. **Configuração inicial:**

    - Após a instalação, abra sua distribuição Linux e configure-a conforme necessário (nome de usuário, senha, etc.).

## Instalar Chocolatey

No PowerShell (como Administrador), execute:

```powershell
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## Instalar o Hyper

O **Hyper** é o terminal recomendado para usar com o WSL. Para instalá-lo, siga os passos abaixo:

1. **Baixar e instalar o Hyper:**

    - Acesse o site oficial do [Hyper](https://hyper.is/) e baixe o instalador para o seu sistema.
    - Após o download, siga o processo de instalação.

2. **Configurar o Hyper para usar o WSL:**

    - O Hyper já vem configurado para usar o WSL por padrão, mas você pode personalizar o arquivo de configuração `.hyper.js`. Para configurar a fonte e o shell, siga os passos abaixo:

    1. Abra o arquivo de configuração do Hyper, localizado em `~/.hyper.js`. Se você não sabe onde está o arquivo, ele geralmente fica na pasta do usuário, como `C:\Users\<Seu Nome>\AppData\Roaming\Hyper\`.

    2. Modifique o arquivo `.hyper.js` para incluir a fonte **FiraCode Nerd Font** e ajustar o shell para o **WSL**. Adicione ou modifique as seguintes linhas:

    ```javascript
    module.exports = {
      config: {
        // Fonte para o terminal
        fontFamily: 'FiraCode Nerd Font',

        // Configuração do shell para o WSL
        shell: 'C:\\Windows\\System32\\wsl.exe',
        shellArgs: ['~'],

        // Outras configurações que você pode querer adicionar
        // Exemplo de cores ou ajustes adicionais
      }
    };
    ```

    3. Salve o arquivo e reinicie o **Hyper** para que as configurações sejam aplicadas.

### Fontes no Hyper:

Para garantir que a **FiraCode Nerd Font** esteja disponível, você precisará instalá-la primeiro. Se você ainda não tem a fonte instalada, siga os seguintes passos:

- **Instalar a FiraCode Nerd Font**:
  1. Acesse o site [Nerd Fonts](https://www.nerdfonts.com/) e baixe a fonte **FiraCode Nerd Font**.
  2. Após o download, extraia o arquivo e instale as fontes no seu sistema.

Com essas configurações, o **Hyper** estará pronto para usar o **FiraCode Nerd Font** e o shell do **WSL**, criando um ambiente mais confortável para trabalhar com desenvolvimento no terminal.

## Atualizar o Sistema Linux (WSL)

No terminal do WSL (Linux), execute:

```bash
sudo apt update && sudo apt upgrade -y
```

## Instalar Zsh e Oh My Zsh

Para um shell mais poderoso e personalizável, instale o **Zsh** e o **Oh My Zsh**.

1. **Instalar o Zsh:**

    No terminal do WSL (Linux), execute:

    ```bash
    sudo apt install zsh -y
    ```

2. **Instalar o Oh My Zsh:**

    No terminal do WSL (Linux), execute:

    ```bash
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    ```

## Instalar e Configurar NVM (Node Version Manager)

O **NVM** é uma ferramenta essencial para gerenciar diferentes versões do Node.js. Para instalá-lo e configurá-lo, siga os passos abaixo:

1. **Instalar NVM:**

    No terminal do WSL (Linux), execute:

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.0/install.sh | bash
    ```

2. **Configurar o NVM no Zsh:**

    Após a instalação, adicione as configurações do NVM ao arquivo `~/.zshrc`:

    ```bash
    echo "export NVM_DIR=\"$HOME/.nvm\"\n[ -s \"$NVM_DIR/nvm.sh\" ] && . \"$NVM_DIR/nvm.sh\"\n[ -s \"$NVM_DIR/bash_completion\" ] && . \"$NVM_DIR/bash_completion\"" >> ~/.zshrc
    source ~/.zshrc
    ```

## Instalar o Tema Powerlevel10k

Para melhorar a aparência do terminal, instale o **Powerlevel10k**.

1. **Instalar Powerlevel10k:**

    No terminal do WSL (Linux), execute:

    ```bash
    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
    ```

2. **Alterar o tema no Zsh:**

    Edite o arquivo `~/.zshrc` e defina o tema como `powerlevel10k/powerlevel10k`:

    ```bash
    ZSH_THEME="powerlevel10k/powerlevel10k"
    ```

3. **Aplicar as mudanças:**

    Para aplicar as mudanças, recarregue o Zsh:

    ```bash
    source ~/.zshrc
    ```

## Extensões do VSCode

Aqui estão as extensões recomendadas para o VSCode, organizadas por funções:

### Necessários

- **Apc Customize UI++**: Personalização avançada da interface do VSCode.
- **WSL**: Suporte para integrar o WSL diretamente no VSCode.

### Tema/Decoração

- **Houston** (modificado): Este tema foi personalizado para melhor atender à minha preferência visual. Você pode conferir o arquivo modificado [aqui](https://github.com/Leugz/Setup/blob/main/houston.json) para detalhes das mudanças.

- **Symbols**: Para ícones personalizados e melhorias visuais.

### Funções Importantes

- **Auto Close Tag**: Fecha automaticamente as tags HTML/JSX.
- **Auto Rename Tag**: Renomeia automaticamente as tags de abertura/fechamento HTML/JSX.
- **Highlight Matching Tag**: Destaca a tag correspondente enquanto edita.
- **Auto Import**: Adiciona automaticamente importações de módulos e pacotes.
- **Auto Prefixer**: Adiciona automaticamente prefixos CSS.
- **Color Highlight**: Destaca cores no código.

### Gerais

- **Discord Presence**: Exibe sua atividade no Discord.
- **GitLens — Git supercharged**: Melhora a integração do Git com o VSCode.
- **ESLint**: Linter para JavaScript e TypeScript.
- **Prettier**: Formatação automática de código.
- **Pretty TypeScript Errors**: Melhora a leitura de erros no TypeScript.

### Suporte

- **HTML CSS Support**: Suporte completo para HTML e CSS.
- **JavaScript and TypeScript Nightly**: Versões mais recentes do JavaScript/TypeScript.

---

Além das extensões, o arquivo `settings.json` do VSCode também contém as minhas configurações pessoais. Você pode conferir esse arquivo [aqui](https://github.com/Leugz/Setup/blob/main/settings.json) para aplicá-las no seu editor.
