# Padrão de commit


Para usar o padrão de commits usando a IDE Webstorm, é necessário instalar o plugin 
`Commit Message Template` e as dependências `@commitlint/{cli, config-conventional}` junto ao `husky` para garantir 
que a mensagem de commit seja comitado seguindo o padrão definido pela Conventional Commits (https://www.conventionalcommits.org/).

1. `yarn init -y`
2. `git init`
3. `yarn add husky -D`
4. `husky install`
5. `yarn add @commitlint/{config-conventional,cli} -D`
6. `echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js`
7. `Ctl+Alt+Shit > Settings > Plugins > Search by (Commit Message Template)`
8. `Tente commitar`

_Obs: Um erro comum com a execução do git hooks via husky, é a não identificação do node via script quando se usa nvm. Pode-se alterar o caminho do node para a execução do script com o seguinte código:_
```shell
export NVM_DIR="$HOME/.nvm/nvm.sh"
. "$(dirname $NVM_DIR)/nvm.sh"

export NVM_DIR="$HOME/.nvm"
a=$(nvm ls | grep 'node')
b=${a#*(-> }
v=${b%%[)| ]*}

export PATH="$NVM_DIR/versions/node/$v/bin:$PATH"
```
Você pode adicionar esse trecho do script no arquivo gerado pelo husky na pasta `.husky/commit-msg`
