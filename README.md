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

## Les fonctions spécials
<code>
    <pre>
       #!/bin/bash 
       message='coucou'
       echo ${#message} # afficher la taille de la chaine
       echo ${message^^} # affiche la chaine en majuscule
       echo ${message,,} # affiche la chaine en miniscule
       echo ${message/o/at} # remplacer la première occurence de o par at
       echo ${message:4:2} # pour extraire deux caractères à partir la position 4 
    </pre>
</code>

## Les calculs arithmétiques en bash
les calcules arithmétiques se font se font à l'aide de deux opérateurs en bash **$(())** &amp; **let**

<code>
    <pre>
        #!/bin/bash
        un=1
        deux=2
        trois=$((un + deux))
        echo trois # affiche 3
        let six=$trois*$deux ou let "six=$trois * $deux"
    </pre>
</code>

## Les paramètres en bash
avant de rentrer dans le scripting, nous allons présenter quelques paramètres spéciaux:
1. **$0** retourne le nom du script
2. **$1** retourne le premier paramètre du script
3. **$2** retourne le deuxième paramètre du script etc jusqu'à \$9
4. à partir de 10 il faut utiliser cette notation ${10}
5. **$#** retourne le nombre de paramètre d'un script
6. **$@** retourne tous les paramètre sous forme d'une liste
7. **$\*** retourne tous les paramètre sous forme d'une chaine de caractère.
8. **shift** permet de supprimer le premier paramètre.
   
<code>
    <pre>
        #!/bin/bash
        echo "Le script s'appelle: $0"
        echo "Le premier paramètre: $1"
        echo "Le deuxième paramètre: $2"
        echo "Le troisième paramètre: $3"
        echo "Le dixième paramètre: ${10}"
        echo "Nous avons $# paramètre(s) passé à ce script"
        echo "Voici la liste des paramètres: $@"
    </pre>
</code>

## Les tests en bash
Les tests sont réalisés en bash à l'aide de deux symbols à savoir le symbols: **test** ou **[  ]** pour faire la comparaison avec le signe égal, il faut entrourer le signe de deux espaces un avant et un après.

Pour vérifier le succès ou l'echec de l'exécution d'un script, on evalue la valeur de la variable spéciale **$?**, si le contenu de cette variable est égal à 0 cela signifie que le script est exécuté avec succès sinon toute autre valeur signifie l'echec.

<code>
    <pre>
        machin='truc'
        echo $? # afficher 0 car la variable a bien  été affectée
        # on peut comparer le contenu de deux variables avec <br />
        test $machin = 'truc' # ou bien<br>
        [ $machin = 'truc' ]
    </pre>
</code>

## Les  Opérateurs de comparaisons et logiques
Pour les opérateurs, je vous dirige vers ces documents très riche.
1. [Les opérateurs de comparaison](https://abs.traduc.org/abs-fr/ch07s03.html)
2. [Les opérateurs de test de fichiers](https://abs.traduc.org/abs-fr/ch07s02.html)
3. [Les tests if/then imbriqués](https://abs.traduc.org/abs-fr/ch07s04.html)
4. [Les Opérations et sujets connexes 1](https://abs.traduc.org/abs-fr/ch08.html)
5. [Opérations et sujets connexes 2](https://abs.traduc.org/abs-fr/ch08s02.html)
6. [Les expressions entre doubles parenthèses](https://abs.traduc.org/abs-fr/ch08s03.html)
7. [Opérations et sujets connexes 3](https://abs.traduc.org/abs-fr/ch08s04.html)
8. [Une exploration en profondeur de l'art de la programmation shell](https://abs.traduc.org/abs-fr/pt03.html)
   
## Les conditions en bash
Les conditions en bash se ressemblent beaucoup aux conditions rapport d'autres langages la syntaxe
à la difference on remplace les parenthèses par le clé **test** ou **[   ]**

<code>
    <pre>
        if test 18 -eq 18; then
            echo "Vous êtes majeurs"
        else
            echo "Vous êtes mineurs"
        fi
        # ou
        if [ 18 -eq 18 ]; then
            echo "Vous êtes majeurs"
        elif test 18 -lt 40; then
            echo "Vous êtes vieux"
        else
            echo "Vous êtes mineurs"
        fi
    </pre>
</code>

<u>**NB:**</u>
Lorsque vous utilisez les crochets, il ne faut surtout pas oublier de mettre un espace avant et après à l'intérieur avant de mettre les conditions

## Les Switch en bash
la condition selon ou **switch** est exprimé en bash avec les expressions suivantes: **case ->switch; )->case; ;;->break; *)->default**.
<code>
    <pre>
        case $1 in
        "Camara")
            echo "Bonjour Camara";;
        "Laby")
            echo "Bonjour Laby";;
        "Damaro")
            echo "Bonjour Damaro";;
        *)
            echo "Bonjour tout le monde";;
        esac
    </pre>
</code>

## Les tableaux en bash
On crée un tableau ou une liste avec la parathèse et en mettant un espace entre chaque élement de la liste.
1. Pour récupérer un élément dans la liste **${nomlist[1]}**
2.  Pour remplacer un élément de la liste **nomlist[1]='Damaro'**
3.  Pour récupérer la taille de la liste **${#nomliste}**
4.  Pour récupérer touts les éléments de la liste: **${nomliste[\*]}**

## Les boucles en bash
les boucles fonctionnent à peu de la même manière en bash que les autres langages

<code>
    <pre>
        liste=(Laby Damaro Camara Etudiant en Mastère pro Business Intelligence à l'ISET Radès)
        for item in ${liste[*]}; do
            echo $item
        done
        # ou bien avec la boucle while
        i=0
        while test "${#liste[@]} -gt $i; do
            echo ${liste[i]}
            i=$((i+1))
        done

        until test "${#liste[@]} -lt $i; do
            echo ${liste[i]}
            i=$((i+1))
        done
    </pre>
</code>

**Note:**
A note que la boucle **until** et **while** fonctionnent en sens inverse, c'est à dire avec **while** **-gt** pour dire tant que la taille est supérieur i alors que avec **until** j'ai utilisé **-lt** pour dire la taille n'est pas inférieur à i on continue
