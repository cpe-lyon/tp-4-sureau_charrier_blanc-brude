# Compte Rendu  TP4
JURAND Baptiste / SUREAU Florian
## Exercice 1
---
1- On commence par créere deux groupes "groupe1" et "groupe2":
```sh
sudo addgroup groupe1
sudo addgroup groupe2
```
2- On créer ensuite quatre utilisateurs u1, u2, u3 et u4 avec la commande "useradd" (le -m permet la création du dossier personnel dans le /home)
```sh
sudo useradd u1 -m
sudo useradd u2 -m
sudo useradd u3 -m
sudo useradd u4 -m
```
3- On cherche maintenant à répartir les utilisateurs dans les deux groupes:
```sh
sudo usermod -a -g groupe1 u1
sudo usermod -a -g groupe1 u2
sudo usermod -a -g groupe1 u4
sudo usermod -a -g groupe2 u2
sudo usermod -a -g groupe2 u3
sudo usermod -a -g groupe2 u4
```

4- Pour afficher les membres d'un groupe on a deux possibilités:
```sh
cat/etc/groupe | grep nom_du_groupe
```
```sh
grep -w nom_du_groupe /etc/group
```

5- On fait de groupe1 le groupe propriétaire de /home/u1 et /home/u2 et de groupe2 le groupe propriétaire
de /home/u3 et /home/u4:
```sh
sudo usermod -m -d groupe1 u1
sudo usermod -m -d groupe1 u2
sudo usermod -m -d groupe2 u3
sudo usermod -m -d groupe2 u4
```

6- On fait de groupe1 le groupe primaire de u1 et u2 puis de groupe2 le groupe prioritaire de u3 et u4:
```sh
sudo usermod u1 -g groupe1
sudo usermod u2 -g groupe1
sudo usermod u3 -g groupe2
sudo usermod u4 -g groupe2
```
7- On se place dans le dossier home est on créer deux dossiers, "groupe1" et "groupe2":
```sh
sudo mkdir groupe1
sudo mkdir groupe2
```
Puis oun permets aux membres de chaque groupes d'écrire dans le dossier corespondant à son groupe:
```sh
sudo chmod 170 groupe1
sudo chmod 170 groupe2
```
- 1 autorise l'utilisateur à parcourir le dossier
- 7 donne tous (parcourir, visionner et executer) les droits aux membres du groupe
- 0 donne aucuns droits aux autres utilisateurs

8- Pour que seul le propriétaire d'un fichier ait le droit de renommer ou suprimer ce fichier on execute cette commande après s'etre placé dans le dossier du groupe en question:
```sh
sudo chmod go-rwx
```
Cette commande permet d'enlever tous les droits aux utilisateurs autres que le propriétaire. Cependant on veut quand meme laisser la lecture des fichiers par tous donc on execute cette commande juste après:
```sh
chmod a+r
```

9- On ne peut pas se connecter en tant qu'utilisateur. Cela est due au fait que lors de la création de nos différents utilisateurs nous n'avons pas défini les mot de passe. Or tout compte créé sans mot de passe est inactif, jusqu’à l’attribution d’un mot de
passe.

10- On définit le mot de passe de l'utilisateur u1 en executant cette commande: 
```sh
sudo passwd u1
```
Puis on écrit le mot de passe que l'on veut.
Pour vérifier que l'utilisateur u1 est bien activé on peut utiliser:
```sh
su u1
```

11- L'uid de u1 est 1001 et le gid de u1 est aussi 1001.

12- Pour nous l'utilisateur correspondant à l'uid 1003 est l'utilisateur u3.

13- L'id du groupe 1 est le gid : 1001.

14- Le groupe possédant le guid 1002 est le groupe 2.

15- On retire l'utilisateur u3 du groupe 2 avec:
```sh
sudo gpasswd -d u3 groupe2
```

17- On a pas vraiment compris la question....

18- L'utilisateur "nobody" est  un utilisateur n'appartenant à aucun groupe qui possède des droits très restraints. En effet il n'a accès qu'aux fichiers accessibles à tous les utilisateurs.


## Exercice 2
---

1- On créer un dossier nommé "test" contenant un fichier nommé "fichier" avec les commandes suivantes:
```sh
sudo mkdir test
sudo nano fichier (Puis on écrit "Bonsoir !"" dans le fichier)
```
On utilise la comande suivante pour regarder les droits:
```
sudo ls -l 
```
- Pour le dossier les droits sont:  -rw-r--r-- 1 root root.
- Pour le fichier les droits sont : drwxr-xr-x root root

2- Pour retirere tous les droits sur le fichier "fichier" on utilise la comande suivante:
```sh
sudo chmod 000 fichier
```
En essayant de l'ouvrir avec l'un des utilisateurs créé dans l'exercice 1 le fichier ne s'ouvre pas et le message d'erreur suivant apparait:
```
sh: 0: Can't open cat
```
Par contre on arrive toujours à ouvrir le fichier avec le root. On peut donc en conclure qu'il est impossible d'empecher à root l'accès à un fichier.

3- On se redonne les droits avec la commande:
```
sudo chmod 700 fichier
```
Puis on execute la commande :
```
echo "echo Hello" > fichier
```
En réouvrant le fichier on s'apperçoit que le texte a bien été remplacé par "echo Hello" 

4- On execute le fichier à l'aide de cette commande:
```
bash fichier
```
 Elle nous renvoie "Hello" ce qui est logique car c'est ce que doit faire la commande écrite dans le fichier "fichier".
 Lorsque nous utilisons sudo devant la commande on obtien le meme résultat mais il faut juste remettre son mot de passe juste avant l'affichage.
 
 5- On se retire les droits d'accès au dossier test avec la commande suivante:
 ```
 sudo chmod 000 /home/test
 ```
 En essayant de lister le contenu du répertoire avec la commande ls, le listage ne se fait pas et le message d'erreur suivant s'affiche
 ```
 ls: cannot open directory '.': Permission denied
 ```
 Il nous est impossible d'executer le fichier "fichier"
 On peut donc en déduire qu'il ne suffit pas d'etre dans le dossier pour executer ce qu'il contient si on ne possède pas les droits.
 
 6- On créer dans test un fichier nouveau ainsi qu’un répertoire sstest puis on retire au fichier nouveau et au répertoire test le droit en écriture:
 ```
 sudo mkdir sstest
 sudo touch nouveau
 sudo chmod 500 sstest nouveau
 ```
On ne peut pas modifier le fichier nouveau. On retablit le droit en écriture sur le repertoir test avec:
```
sudo chmod 700 test
```
Meme apres cela on arrive toujours mas à modifier ou supprimer le fichier.
On peut donc en déduire que changer les droits d'un dossier à laquelle on a accès ne peut pas nous permettre d'acceder aux fichiers auxquels on n'a pas accès, qu'il contient.
 
7- 

8-

9-

10- On définit un umask très restrictif:
```
umask 077
```
11- On définit un umask très permissif:
```
umask 022
```
12- On définit un umask équilibré:
```
umask 037
```
13-Pour : chmod u=rx,g=wx,o=r fic, la transcription en notations octale est:
```
chmod 534 fic
```
Pour :chmod uo+w,g-rx fic en sachant que les droits initiaux de fic sont r--r-x---, la transcription en notations octale est:
```
chmod 620 fic
```
Pour : chmod 653 fic en sachant que les droits initiaux de fic sont 711, la transcription en notations octale est:
```
chmod u-x,g+r,o+w fic
```
Pour : chmod u+x,g=w,o-r fic en sachant que les droits initiaux de fic sont r--r-x---, la transcription en notations octale est:
```
chmod 520 fic
```
14- Pour afficher les droits sur le programme passwd on utilise cette commande:
```
ls -l passwd
```
On remarque que tout le monde a le droit de lecture dessus mais seul l'utilisateur a le droit d'écriture. Aussi, personne n'a le droit d'execution.













