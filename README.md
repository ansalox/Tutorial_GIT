# Crear repositorio y subir proyecto

git init

git remote add origin "URL repo"

cambiar url remota
git remote set-url origin -url-

eliminar url remota
git remote rm -url-

git status

verificar cambios
git fetch origin main

trae ambios y hacer merge
git pull origin main

git status
git status s

git add .

desacer los git add
git reset .

git status

muestra archivos que no se han enviado para cambios
git diff

modificar los git commit 
git commit --amend

git commit -m "Fist Commit"

git push -u origin main

crear rama y ubicarse
git checkout -b -rama-

git branch -D -rama a eliminar-


hacer rebase 
git rebase -ramra-

si salen conflictos toca resolverlos y continuar el rebase
git reabase --continue

adiciona.:
descartar un rebase
git rebase --skip
devolver todo rebase al principio
fit rebase --abort

ver remotos repositorios
git remote -v

ver ramas remotas
git remote show origin

limpiar todas las ramas eliminadas que aun siguen saliendo
git remote prune origin


mostrar listado de commits
git log --graph --oneline --decorate

remover archivos
git rm -nombre archivo-



crear tags
git tag v0.0.1 -m "primera version"

lista de todos los tags
git tag

ver repositorio en cada estado
git show v0.0.1

enviar el repositorio en github
git push tags





