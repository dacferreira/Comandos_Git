## Comandos do GIT, que são úteis pra o dia a dia

## [Configuração]
git config --global user.name "<Nome usuário>"
// Configurar globalmente o usuário para o git

git config --global user.email "<e-mail usuário>"
// Configurar globalmente o e-mail para o git

git config --global color.ui true 
// Para o git colorir as interações feitas por ele

git config --global core.editor "notepad" 
// Colocando o notepad para programa padrão para editar o git commit

git config --list --global 
// Mostrar as configurações globais do git

 git config --global credential.authority basic 
 // Para o git solicitar os dados de autenticação novamente
 
 
## [Trace]
export GIT_TRACE=1  
// Habilita o trace de funcionalidades (output) 

export GCM_TRACE=1 
// Git credentials manager
 
 
## [Repositório]
git –bare init
// Cria um repositório git para acesso remoto


## [Commits]

git add -A
// Adiciona todas as alterações, inclusive arquivos novos,  para commit

git commit -m "<Descrição do commit>"
// Consolida as alterações adicionadas ao commit, com uma descrição

git commit -a -m “<Descrição do commit>”
// Adiciona e consolidada as alterações, mas não adiciona novos arquivos


## [ Branchs ]

git branch name_branch
// cria um branch novo apartir do branch atual

git branch -m name_old_branch name_new_branch
// renomear um branch

git branch nomebranch -d
// Deleta um branch localmente atualizado

git branch nomebranch -D
// Deleta branch localmente independente da situação dele

git push origin :nome_do_branch
// Excluir branch remoto

git branch -a
// Lista branchs remotos

git push –force origin branchremoto
// realiza o push e sobrescreve o branch do servidor pelo seu branch local

git remote prune origin
// remove localmente todos os branches que já foram removidos remotamente - espécie de sync

git push origin branch_local:branch_remoto
// cria um branch remoto baseado em um branch local

git push -u origin branch_local:branch_remoto
// cria um branch remoto baseado em um branch local, mantendo os branches vinculados 

git branch –set-upstream meu_branch origin/meu_branch
// vincula um branch local a um branch remoto (caso ainda não exista esta vinculação)
git branch -m old_branch new_branch
// Para renomear branch


## [ Log ]

git log 
// mostra o log do git

git log -p 
// Mostra pra cada arquivo, a diferença, o diff dos arquivos

git log -p -2
// Mostra os dois ultimos commits e mostra pra cada arquivo, a diferença, o diff dos arquivos

git log - p nome_arquivo
// mostra o que foi alterado em cada commit em um arquivo

git log –author=Name Author
// mostra apenas commits e um autor específico

git log --stat 
// Mostra o git log, mais a statistica para cada arquivo

git log --pretty=oneline 
// Trás o log dos commits em uma linha ara cada um

git log --pretty=format:"%h - %an, %ar : %s" 
// Trás detalhado com o inicio do hash do commit, quem commitou, quando commitou e o comentário que usou

git log --since=2.days 
// Irá retornar os commits nos ultimos 2 dias até hoje

git blame nome_arquivo
// mostra quem foi o autor de cada linha de um arquivo


## [Reset]

git reset HEAD text2.txt 
// Voltar o arquivo que está no estagio para comitar, para untracked files

git checkout  ea7d41d16b9f24bfa61747fc030f29e3999fd726 
// Volta os arquivos para a versão do commit "ea7d41d16b9f24bfa61747fc030f29e3999fd726"

git reset HEAD~1 
// Volta um commit, podendo colocar quantos numero quiser

git reset HEAD~1 --soft 
// Remove os commits, mas deixa os arquivos com as alterações, caso queira alterar e mandar novamente

git reset –hard HEAD^
// desfaz as alterações consolidadas no último commit

git reset HEAD~1 --hard 
// Volta o commit e exclui os arquivos do ultimo commit " perde o commit"

git reset –hard SHA1DOCOMMIT
// desfaz as alterações consolidadas depois do commit específicado

## [ Whatchanged ]
git whatchanged
// mostra quais arquivos foram alterados em cada commit

git whatchanged –author=Name Author
// mostra quais arquivos foram alterados em cada commit de um autor específico


## [ Checkout ]

git checkout -f
// desfaz as alterações não consolidadas no branch atual

git checkout nome_arquivo
// desfaz as alterações não consolidadas em um arquivo

git checkout -b nomeDoBranch origin/nomeDoBranch
// limpa um branch e realiza o pull do servidor para um único branch

git checkout -b funcionalidade1 
// Cria o Branch com o nome funcionalidade1

git rebase funcionalidade1 
// Rodar dentro do master - reordena a ordem dos commits, mas trazendo o comit da funcionalidade1 para o master


## [ Ignore ]

git update-index –assume-unchanged <filename(s)>
//Para ignorar arquivos já existentes em seu projeto

git update-index –no-assume-unchanged <filename(s)>
//Para “designorar” arquivos ignorados em seu projeto

git ls-files -v | grep “h ”
####  atenção: esse espaçozinho depois do ‘h’ é obrigatório ####
//Para listar arquivos já ignorados em seu projeto


## [ Tags ]

git tag 0.0.1 
// Cria um tag com a versão

git tag -l 
// lista todas as tags

git push –tags
// realiza o push e envia as tags criadas para o remote

git tag -d tag_name
// remove uma tag localmente

git push origin :refs/tags/tag_name
// remove tag já enviada ao servidor - 12345 é a tag

git push origin tag_name
//envia uma tag criada localmente para o remote

git push origin master --tags 
// Irá criar um release com a tag


## [Revert ]

git checkout SHA1^ — <filename>
//Para reverter um arquivo para uma determinada versão

git revert SHA1
//Para reverter para um determinado commit criando um novo commit


## [ Reset ]

git reset –hard SHA1
//Para reverter para um determinado commit

git reset –hard HEAD^
//Para reverter o último commit


## [ Stash ]

git stash
// move as alterações não adicionadas ao commit para memoria tempoária e limpa o branch das alterações.
// comando deve ser usada quando precisarmos mudar de branch sem commitar as mudanças atuais.

git stash list
// mostra os stashs criados, exemplo:
/*
 *   stash@{0}: WIP on branch_name
 *   stash@{1}: WIP on branch_name
**/

git stash apply stash@{1}
// retorna as alterações do stash 1
