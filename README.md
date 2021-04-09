# Découvrir l'écriture de scripts en Bash

Le Bash est un interpréteur de commandes très connu en Linux, mais il est également un puissant langage de script. Si vous êtes administrateur Linux et si vous voulez automatiser vos tâches et réaliser des scripts puissants, cette formation est faite pour vous. Avec Rudi Bruchez, découvrez comment recevoir et traiter les paramètres envoyés à vos scripts, et comment manipuler des variables. Vous apprendrez à maîtriser ce langage de programmation et à créer des boucles et des branchements.
## Variable en bash
Les nom des variables en bash peuvent contenir des caractères accentués, mais il serait mieux de les éviter au miximum et de se conformer aux règle de nommages traditionnelles dans les autres language.<br />
**NB:** pour assigner des valeurs aux variables en bash, il faut surtout mettre de l'espace avant et après l'affectation<br />
exemple: <br />Erreur: <code><strike>message = 'Hello, World'</strike></code><br/>
Bon: <code>message = 'Hello, World'</code><br/>
Pour utiliser une variable il faut préceder son nom par le signe **$**<br />
<code>echo $message</code>

## Interpolation des variables en bash
L'interpolation de variable consiste à interpréter une variable au sein d'une chaine de caractère.
elle fait en bash via le signe **""** et non **''**
soit le fichier **ex1.sh**<br/>
Exemple:
<code>
<pre>
    #!/bin/bash #Cette ligne est le shebang
    message='coucou' #declaration et affectation de de variable
    echo '$message salut mon ami' # cette ligne va afficher $message suivi du reste
    echo "$message salut mon ami" # celle là va afficher la valeur de message suivi du reste
    echo ${message}cou # cette va afficher coucoucou
</pre>
</code>