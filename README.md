# 🧩 Aula Prática – Git Local (sem GitHub)

## 🎯 Objetivo
Aprender a utilizar o **Git** localmente para versionar projetos, criando commits, branches e manipulando o histórico de forma segura.

---

## 🧱 1. Configuração inicial

Esses comandos configuram o nome e o e-mail do usuário (necessário para registrar os commits).

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@exemplo.com"
```
Eles server para você ter uma identidade no git. isso é muito importante porque cada commit usa esta informação, e ela é carimbada de forma imutável nos commits que você começa criar.
com a opção do comando *--global* , você só faz isso uma vez, porque então o Git usará esta informção para qualquer coisa que você fizer naquele sistema.Se você quiser subustituir essa informação com nome diferente para um projeto específico, basta rodar o comando sem a opção de *--global* dentro do projeto.

```
git config --global core.editor "code --wait"   # Define o VS Code como editor padrão (opcional)
```
Agora que a sua identidade está configurada, você pode escolher o editor de texto padrão que será chamado quando Git precisar que você entre uma mensagem, que pode ser escolhida como editor padrão, configurado , etc...
```
git config --list                                # Verifica as configurações atuais
```
Se você quiser testar as suas configurações, você pode usar o comando git config --list para listar todas as configurações que o Git conseguir encontrar naquele momento:
<img width="672" height="154" alt="Captura de tela 2025-10-28 104207" src="https://github.com/user-attachments/assets/74b4adfd-297b-440c-ad97-d1f512019c23" />



## 📂 2. Criar e iniciar um repositório

```bash
mkdir meu_projeto
```
isso criará a pasta na sua máquina, no entanto, não funciona caso :

- A permissão for negada 

- o arquivo nomeado for existente

```
cd meu_projeto
```
usasse quando quer ir para  um diretório específico seguido pelo nome desejado . 

ex:cd Documentos/Projetos (entra na pasta "Projetos" que está dentro de "Documentos").

```
git init
```

Ele inicializa um novo repositório Git vazio onde as alterações do projeto podem ser controladas.
O comando git init é usado para iniciar o controle de versão de um projeto, criando um novo repositório Git na pasta atual. Ele também pode ser usado para reativar um projeto já existente, tornando-o um repositório Git. Porém, se o projeto já estiver hospedado em um servidor remoto e você quiser apenas copiar para sua máquina.

---

## 🏷️ 3. Alterar a branch padrão de `master` para `main`

Por padrão, o Git pode criar a branch inicial como **master**.  
Para padronizar e seguir boas práticas, altere para **main**:

```bash
git branch -m master main
```
Esse comando renomeia a branch principal do repositório de master para main.
Hoje em dia, o GitHub usa main como nome padrão, então esse comando serve para deixar seu repositório atualizado com o padrão moderno.


Se quiser definir **main** como padrão para novos repositórios:

Para definir main como a branch padrão em novos repositórios, é possível configurar isso tanto no Git local quanto nas plataformas de hospedagem.

No Git, basta executar:

```
git config --global init.defaultBranch main
```
Esse comando faz com que todo novo repositório criado com git init use main como branch inicial.
É uma configuração global, ou seja, vale para todos os projetos
---

## 📄 4. Criar arquivos e verificar status

```bash
echo "Meu primeiro arquivo" > readme.txt
git status
```
O comando echo cria um arquivo de texto chamado readme.txt com o conteúdo escrito.
git status mostra o que mudou no repositório: arquivos novos, modificados, ou prontos para commit.
Após criar o arquivo, git status vai exibir algo como:

```
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	readme.txt
```



---

## 🧺 5. Adicionar arquivos à área de staging

```bash
git add readme.txt       # adiciona um arquivo específico
git add .                # adiciona todos os arquivos do diretório
git status
```

O comando git add é responsável por preparar os arquivos que serão incluídos no próximo commit.
Quando fazemos mudanças em um projeto, o Git não salva tudo automaticamente — ele precisa saber quais arquivos queremos registrar no histórico.
É aí que entra a chamada área de staging (ou “área de preparação”).

git add readme.txt: adiciona apenas um arquivo específico.

git add .: adiciona todos os arquivos novos e modificados no diretório atual.

git status: mostra o que está pronto para commit e o que ainda não foi adicionado.





> A área de staging é onde os arquivos ficam “preparados” antes do commit.

---

## 💾 6. Fazer o primeiro commit

```bash
git commit -m "Primeiro commit - adiciona readme.txt"
```
Um commit é o momento em que o Git salva oficialmente as alterações que estavam na área de staging.
Cada commit recebe uma mensagem (-m) que descreve o que foi alterado, facilitando o rastreamento no futuro.

---

## 🔍 7. Ver histórico e detalhes

```bash
git log
```
exibe a lista completa de commits com autor, data e mensagem.
```
git log --oneline
```
mostra o histórico resumido, ideal para consultas rápidas.

```
git show
```
detalha as mudanças feitas em um commit específico.



> Use `--oneline` para visualizar um resumo simplificado.

---

## ✏️ 8. Editar arquivos e registrar mudanças

```bash
echo "Adicionando nova linha" >> readme.txt
git status
git diff
git add readme.txt
git commit -m "Atualiza readme.txt com nova linha"
```

> `git diff` mostra as diferenças entre a versão atual e a anterior.

---

## ♻️ 9. Desfazer mudanças

```bash
git restore readme.txt              # descarta mudanças não adicionadas
git restore --staged readme.txt     # remove da área de staging
```

> Ideal para corrigir erros antes de um commit.

---

## 🌿 10. Criar e alternar entre branches

```bash
git branch                         # lista branches
git branch nova_funcionalidade     # cria nova branch
git switch nova_funcionalidade     # muda para ela
```

> Cada branch é uma linha independente de desenvolvimento.

---

## 🧬 11. Fazer commits em outra branch

```bash
echo "Nova feature" > feature.txt
git add feature.txt
git commit -m "Adiciona nova feature"
```

---

## 🔀 12. Voltar e mesclar mudanças

```bash
git switch main
git merge nova_funcionalidade
```

> Junta as alterações da branch `nova_funcionalidade` na `main`.

---

## 🗑️ 13. Excluir branches locais

```bash
git branch -d nova_funcionalidade
```

---

## 🧹 14. Ignorar arquivos com `.gitignore`

Crie um arquivo chamado `.gitignore` e adicione:

```
*.log
*.tmp
node_modules/
```

Depois:

```bash
git add .gitignore
git commit -m "Adiciona arquivo .gitignore"
```

---

## 🧠 15. Visualizar informações úteis

```bash
git status
git log --oneline --graph --decorate
git diff
git show HEAD
```

> `--graph` mostra o histórico com ramificações visualmente.

---

## 💡 16. Exemplo de fluxo completo

```bash
git init
echo "Aula prática Git local" > readme.txt
git add .
git commit -m "Primeiro commit"
git branch dev
git switch dev
echo "Nova versão em desenvolvimento" >> readme.txt
git add .
git commit -m "Atualiza versão dev"
git switch main
git merge dev
git log --oneline --graph
```

---

## 📘 Créditos

Material criado para fins educacionais na aula prática de **Git Local**,  
ministrada por *Anderson R. M. Gomes* 🧑‍🏫

---

**🚀 Próximos passos:**  
Na próxima aula, você aprenderá a conectar este repositório local ao GitHub com os comandos `git remote`, `git push` e `git pull`.
