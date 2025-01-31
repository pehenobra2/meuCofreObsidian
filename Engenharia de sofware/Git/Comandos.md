
## 1. Configuração do Usuário

Definir informações do usuário que serão utilizadas entre os repositórios

```
# Define o nome do usuário globalmente
$ git config --global user.name "[Seu Nome]"

# Define o e-mail do usuário globalmente
$ git config --global user.email "[seu-email@exemplo.com]"

# Habilita a coloração dos comandos Git no terminal
$ git config --global color.ui auto
```

---

## 2. Inicialização e Clonagem

Configuração inicial de um repositório Git e clonar repositórios existentes.

```
# Inicializa um novo repositório Git na pasta atual
$ git init

# Clona um repositório remoto para o diretório atual
$ git clone [URL-do-Repositorio]
```

---

## 3. Trabalhando com Arquivos

Gerenciamento de arquivos dentro do repositório Git.

```
# Adiciona um arquivo ao staging (prepara para commit)
$ git add [arquivo]

# Adiciona todos os arquivos modificados ao staging
$ git add .

# Verifica o status atual do repositório
$ git status

# Remove um arquivo do staging
$ git reset [arquivo]
```

---

## 4. Commits

Salvar alterações no repositório.

```
# Realiza um commit com uma mensagem descritiva
$ git commit -m "Mensagem do commit"

# Altera o último commit (se ainda não foi enviado ao repositório remoto)
$ git commit --amend -m "Nova mensagem do commit"
```

---

## 5. Histórico de Commits

Visualização do histórico do repositório.

```
# Exibe o histórico de commits do repositório
$ git log

# Exibe um histórico resumido (uma linha por commit)
$ git log --oneline

# Exibe um histórico com branchs e estrutura visual
$ git log --graph --oneline --all
```

---

## 6. Trabalhando com Branches

Gerenciamento de branches para desenvolvimento paralelo.

```
# Lista todas as branches locais
$ git branch

# Cria uma nova branch
$ git branch [nome-da-branch]

# Alterna para outra branch
$ git checkout [nome-da-branch]

# Cria e muda para uma nova branch imediatamente
$ git checkout -b [nome-da-branch]

# Deleta uma branch localmente
$ git branch -d [nome-da-branch]
```

---

## 7. Sincronização com Repositórios Remotos

Enviando e recebendo alterações para um repositório remoto.

```
# Exibe os repositórios remotos configurados
$ git remote -v

# Adiciona um repositório remoto
$ git remote add origin [URL-do-Repositorio]

# Envia alterações para o repositório remoto
$ git push origin [branch]

# Envia todas as branches para o repositório remoto
$ git push --all origin

# Baixa alterações do repositório remoto
$ git pull origin [branch]
```

---

## 8. Mesclagem e Resolução de Conflitos

Juntando alterações de diferentes branches e resolvendo conflitos.

```
# Junta outra branch na branch atual
$ git merge [nome-da-branch]

# Exibe os arquivos com conflitos
$ git diff --name-only --diff-filter=U

# Depois de resolver os conflitos, adiciona os arquivos corrigidos
$ git add .

# Finaliza o merge
$ git commit -m "Resolvendo conflitos"
```

---

## 9. Revertendo Alterações

Desfazendo alterações e restaurando estados anteriores.

```
# Remove arquivos do staging (mantém as modificações no diretório de trabalho)
$ git reset [arquivo]

# Reverte um commit mantendo as alterações
$ git reset --soft HEAD~1

# Reverte um commit descartando as alterações
$ git reset --hard HEAD~1

# Cria um novo commit que desfaz alterações anteriores
$ git revert [commit-hash]
```

---

## 10. Git Stash

Salvando temporariamente alterações sem fazer commit.

```
# Salva as alterações atuais sem commit
$ git stash

# Lista os stashes salvos
$ git stash list

# Restaura o stash mais recente
$ git stash pop

# Restaura um stash específico
$ git stash apply [stash@{n}]
```

---

## 11. Removendo e Restaurando Arquivos

Gerenciando arquivos dentro do repositório.

```
# Remove um arquivo e adiciona a remoção ao staging
$ git rm [arquivo]

# Restaura um arquivo deletado
$ git checkout -- [arquivo]
```

---

## 12. Submódulos

Trabalhando com submódulos dentro de um repositório Git.

```
# Adiciona um submódulo ao repositório
$ git submodule add [URL-do-Repositorio]

# Inicializa e clona submódulos
$ git submodule update --init --recursive
```

---

## 13. Comando de Ajuda

Para obter mais informações sobre qualquer comando Git.

```
# Exibe a documentação oficial de um comando específico
$ git help [comando]

# Exibe uma versão resumida da ajuda no terminal
$ git [comando] --help
```

---