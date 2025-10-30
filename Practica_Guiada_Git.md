# 🧭 Práctica Guiada – Git e GitHub en Linux


---

## 1️⃣ Creación do directorio de práctica

Creamos un novo directorio e accedemos a el:

```bash
$ mkdir prueba_git
$ cd prueba_git
```

**Saída:**
```
$ mkdir prueba_git
$ cd prueba_git
```

---

## 2️⃣ Creación dos ficheiros iniciais

Creamos un arquivo de texto:

```bash
$ nano texto.txt
```

Contido:

```
uno
dos
tres
```

E outro script bash:

```bash
$ nano script.sh
```

Contido:

```bash
echo "Listado completo"
ls -l
```

Dámoslle permisos de execución e probámolo:

```bash
$ chmod a+x script.sh
$ ./script.sh
```

**Saída:**
```
Listado completo
total 8
-rwxrwxr-x 1 meu meu  41 out 30 18:45 script.sh
-rw-rw-r-- 1 meu meu  12 out 30 18:45 texto.txt
```

---

## 3️⃣ Inicialización do repositorio Git

Inicializamos o repositorio local:

```bash
$ git init
```

**Saída:**
```
Initialized empty Git repository in /home/meu/prueba_git/.git/
```

Comprobamos o estado:

```bash
$ git status
```

**Saída:**
```
On branch master
No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.sh
        texto.txt
```

---

## 4️⃣ Engadir e confirmar ficheiros

Engadimos o primeiro ficheiro e confirmamos:

```bash
$ git add script.sh
$ git commit -m "Confirmación inicial"
```

**Saída:**
```
[master (root-commit) 972303a] Confirmación inicial
 1 file changed, 2 insertions(+)
 create mode 100755 script.sh
```

Engadimos o segundo ficheiro e facemos outro commit:

```bash
$ git add texto.txt
$ git commit -m "Engadido arquivo texto.txt"
```

**Saída:**
```
[master b4f1e2c] Engadido arquivo texto.txt
 1 file changed, 3 insertions(+)
 create mode 100644 texto.txt
```

---

## 5️⃣ Modificación de ficheiros

Engadimos unha nova liña ao arquivo `texto.txt`:

```bash
$ echo "cuatro" >> texto.txt
$ git status
```

**Saída:**
```
modified:   texto.txt
```

Facemos o commit:

```bash
$ git add texto.txt
$ git commit -m "Ampliada a explicación do texto"
```

**Saída:**
```
[master e9a4d51] Ampliada a explicación do texto
 1 file changed, 1 insertion(+)
```

---

## 6️⃣ Ver historial e commits

```bash
$ git log --oneline
```

**Saída:**
```
e9a4d51 (HEAD -> master) Ampliada a explicación do texto
b4f1e2c Engadido arquivo texto.txt
972303a Confirmación inicial
```

---

## 7️⃣ Comprobar diferenzas entre versións

Editamos o arquivo `texto.txt` e eliminamos “tres”, engadindo “cinco”:

```bash
$ nano texto.txt
```

Contido modificado:
```
uno
dos
cuatro
cinco
```

Comprobamos as diferenzas:

```bash
$ git diff
```

**Saída:**
```
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,4 @@
 uno
 dos
-tres
+cuatro
+cinco
```

Facemos o commit:

```bash
$ git commit -a -m "Probando diff con cambios en texto.txt"
```

**Saída:**
```
[master 6292380] Probando diff con cambios en texto.txt
 1 file changed, 1 insertion(+), 1 deletion(-)
```

---

## 8️⃣ Ignorar ficheiros (.gitignore)

Creamos un arquivo `.gitignore`:

```bash
$ nano .gitignore
```

Contido:
```
*.class
*~
!importante~
```

Engadimos novos ficheiros:

```bash
$ echo "Welcome to the Java World" > Hola.java
$ touch importante~ temporal~
$ javac Hola.java
```

Comprobamos o contido:

```bash
$ ls -a
```

**Saída:**
```
.  ..  .git  .gitignore  Hola.class  Hola.java  importante~  temporal~  script.sh  texto.txt
```

Engadimos e confirmamos:

```bash
$ git add .
$ git commit -m "Engadido .gitignore, fontes Java e arquivos importantes"
```

**Saída:**
```
[master 83eb263] Engadido .gitignore, fontes Java e arquivos importantes
 4 files changed, 15 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Hola.java
 create mode 100644 importante~
```

---

## 9️⃣ Crear tags e ramas

Creamos unha etiqueta de versión:

```bash
$ git tag v0.7
$ git log --oneline
```

**Saída:**
```
83eb263 (HEAD -> master, tag: v0.7) Engadido .gitignore, fontes Java e arquivos importantes
6292380 Probando diff con cambios en texto.txt
e9a4d51 Ampliada a explicación do texto
b4f1e2c Engadido arquivo texto.txt
972303a Confirmación inicial
```

Creamos unha nova rama:

```bash
$ git branch Proba
$ git switch Proba
```

Engadimos unha liña a `Hola.java`:

```bash
$ echo 'System.out.println("Nova liña dende a rama Proba");' >> Hola.java
$ git commit -am "Engadida liña en Hola.java na rama Proba"
```

**Saída:**
```
[Proba c862211] Engadida liña en Hola.java na rama Proba
 1 file changed, 1 insertion(+)
```

Volvemos á rama principal e fusionamos:

```bash
$ git switch master
$ git merge Proba
```

**Saída:**
```
Updating 83eb263..c862211
Fast-forward
 Hola.java | 1 +
 1 file changed, 1 insertion(+)
```

---

## 🔟 Subida do proxecto a GitHub

*(Opcional, unha vez creado o repo remoto)*

```bash
$ git remote add origin https://github.com/meu/prueba_git.git
$ git branch -M main
$ git push -u origin main
```

**Saída:**
```
Enumerating objects: 20, done.
Writing objects: 100% (20/20), done.
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

---

## ✅ Conclusión

Completouse a práctica guiada:  
- Git instalado e configurado.  
- Repositorio local inicializado e versionado.  
- Uso de add, commit, diff, log, tag, ramas e merge.  
- Subida final a GitHub.  
