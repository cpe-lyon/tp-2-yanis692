

# TP 2- Bash

# Exercice 1. Variables d’environnement
## 1. Dans quels dossiers bash trouve-t-il les commandes tapées par l’utilisateur ?
```
printenv PATH
```
![image](https://user-images.githubusercontent.com/77662970/189591857-7fc5429b-3861-4470-ab75-0f3547f84e5b.png)
## 2. Quelle variable d’environnement permet à la commande cd tapée sans argument de vous ramener dans votre répertoire personnel ?
La variable $HOME nous raméne directement dans notre répertoire avec la commande cd $HOME.
## 3. Explicitez le rôle des variables LANG, PWD, OLDPWD, SHELL.
La variable LANG permet de voir la langue utilisé par le système, la variable pwd permet de lister le répertoire de travail courant dans l'interpréteur de commande, OLDPWD permet d'accéder a l'ancien repertoire graxce au chemin enregistrer et SHELL est l'interpreteur de commande de l'utilisateur.
## 4. Créez une variable locale MY_VAR (le contenu n’a pas d’importance). Vérifiez que la variable existe
Pour créer une variable locale, on utilise la commande ```nomVariable="contenu"```.                                          Ici, nous utilisons 
```
MY_VAR"test"
```
Pour vérifier son existence, il faut taper
```
echo "$MY_VAR"
```
et le système devrait retourner Test.

![image](https://user-images.githubusercontent.com/77662970/192110618-ae4eb7ba-6659-4fdd-9346-b1fafdae5975.png)
## 5. Tapez ensuite la commande bash. Que fait-elle ? La variable MY_VAR existe-t-elle ? Expliquez. A la fin de cette question, tapez la commande exit pour revenir dans votre session initiale.
La commande bash nous emmenne dans un nouveau interpréteur de commande. La variable MY_Var n'existe car nous l'avons crée  dans un autre interpreteur. 
## 6. Transformez MY_VAR en une variable d’environnement et recommencez la question précédente. Expliquez.
En la transformant en variable d'environement la variable est disponible a partir de tous les shell ou interpréteur.
## 8. Ecrivez une commande qui affiche ”Bonjour à vous, prenom nom !” en utilisant la variable NOM.
```
echo "Bonjour à vous, $NOM"
```
![image](https://user-images.githubusercontent.com/77662970/192109908-f9327558-7f05-40d4-8365-a8af1cb9faeb.png)
## 9. Quelle différence y a-t-il entre donner une valeur vide à une variable d’environnement et l’utilisation de la commande unset ?
La commande unset va supprimer la variable dans sa totalité et alors mettre 0 commentaire la variable existera toujours.
## 10. Utilisez la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre dossier personnel d’après bash)
```
echo "$HOME"
```
![image](https://user-images.githubusercontent.com/77662970/192109874-6eae28f2-2509-4bac-bb27-fbfaa7459725.png)

# Programmation BASH

# Exercice 2. Contrôle de mot de passe
Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au
contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par
l’utilisateur ne doit pas s’afficher.


![image](https://user-images.githubusercontent.com/77662970/189850690-81648897-a0a6-487d-b417-aae1a9d6f2f0.png)

```
#!/bin/bash
mdp=moi
read -p 'Saisissez le mot de passe : ' -s psw
if [ $psw = $mdp ]; then
        echo "Le mot de passe est bon !"
else
        echo "Le mot de passe est pas bon !"
fi

```


# Exercice 3. Expressions rationnelles
Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre
est un nombre réel :

![image](https://user-images.githubusercontent.com/77662970/189872006-505193e3-07dd-4c50-b32e-9e39d315fddf.png)

``` 
#!/bin/bash

function is_number()
{
re='^[+-]?[0-9]+([.][0-9]+)?$'
if ! [[ $1 =~ $re ]] ; then
        return 1
else
        return 0
fi
}
is_number $1
echo "Le code erreur est : $?"
```

# Exercice 4. Contrôle d’utilisateur
Écrivez un script qui vérifie l’existence d’un utilisateur dont le nom est donné en paramètre du script. Si le
script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation : nom_du_script nom_utilisateur”,
où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre
script, le message doit changer automatiquement)

```
#!/bin/bash
if [ -z $1 ]; then
    echo "Utilsation : $0 nom-utilisateur"
elif grep -w $1 /etc/passwd ›/dev/null; then
       echo "L'utilisateur existe"
else
      echo "L'utilisateur n'existe pas"
fi
```

![image](https://user-images.githubusercontent.com/77662970/190355958-8d388945-132a-483f-a743-a6a6743accbd.png)


# Exercice 5. Factorielle
Écrivez un programme qui calcule la factorielle d’un entier naturel passé en paramètre (on supposera que
l’utilisateur saisit toujours un entier naturel).


```
#!/bin/bash
fact=1
for i in $(seq 1 $1)
do 
   res=$(( $fact * $i ))
   fact=$res
done
echo "$res"
```

![image](https://user-images.githubusercontent.com/77662970/190897787-39278698-be2f-481a-b6da-3d432d67dd6f.png)


# Exercice 6. Le juste prix
Écrivez un script qui génère un nombre aléatoire entre 1 et 1000 et demande à l’utilisateur de le deviner.
Le programme écrira ”C’est plus !”, ”C’est moins !” ou ”Gagné !” selon les cas (vous utiliserez $RANDOM).

```
#!/bin/bash
nbr=$(( $RANDOM % 1001 ))
read -p "Entrez un chiffre : " chiffre
while [ $chiffre != $nbr ]
do
    if [ $chiffre -gt $nbr ]; then
        echo "C'est moins"
    fi    
    if [ $chiffre -lt $nbr ]; then
        echo "C'est plus"
    fi
     read -p "Entrez un chiffre : " chiffre
done

echo "C'est gagné !"
```

![image](https://user-images.githubusercontent.com/77662970/190899088-7de91e65-98eb-4117-86e9-273cb85d3d85.png)


# Exercice 7. Statistiques
## 1. Écrivez un script qui prend en paramètres trois entiers (entre -100 et +100) et affiche le min, le max
et la moyenne. Vous pouvez réutiliser la fonction de l’exercice 3 pour vous assurer que les paramètres
sont bien des entiers.

```
#!/bin/bash
error=0
max=0
min=0
moyenne=0

function is_number()
{
re='^[+-]?[0-9]+([.][0-9]+)?$'
if ! [[ $1 =~ $re ]] ; then
        return 1
else
        return 0
fi
}

function max(){
        if { $1 -gt $2}; then
                max=$1
        elif { $3 -gt $1 }; then
                max=$3
        else
                max=$2
        fi
}

function min(){
        if [ $1 -lt $2 ]; then
                min=$1
        elif [ $3 -gt $1 ]; then
                min=$3
        else
                min=$2
        fi
}

function moyenne(){
        moyenne=$((( $1 + $2 + $3 ) / 3 ))
}

min $1 $2 $3
max $1 $2 $3
moyenne $1 $2 $3

while (("$#"));
do
        is_number $1
        if [ $? = 1 ] || [ $1 -gt 100 ] || [ $1 -lt -100 ]; then
                echo "Veuillez saisir des nombres compris entre 100 et -100"
                exit
        fi
        shift
done

echo "Le minimum est $min"
echo "Le maximum est $max"
echo "La moyenne est $moyenne"
```
![image](https://user-images.githubusercontent.com/77662970/192146447-cdf1c568-389c-42c6-b9fc-2abfc204dfbd.png)
## 2. Généralisez le programme à un nombre quelconque de paramètres (pensez à SHIFT)
```
#!/bin/bash
min=$1
max=0
count=0
Sum=0
function is_number()
{
re="^(+-]?[0-9]+([.][0-9]+)?$"

if ! [[ $1 =~ $re ]] ; then
    return 1
else
   return 0
fi
}
is_number
while [ "$*" ]; do
if [ $? = 1 ] || ($1 -gt 100 ] || [ $1 -lt -100 ]; then
   echo "Entrez des nombres compris entre -100 et 100"
   exit
fi
if【 ＄1 -le $min ]; then
    min=$1
fi
if [ $1 -ge smax ]; then
    max=＄1
fi
count=$(( $count +1 ))
sum=$(( $1 + sum ) )
moyenne=$(( $sum / Scount ))
shift
done

echo "Le minimum est $min"
echo "Le maximum est $max"
echo "La moyenne est $moyenne"
```

![image](https://user-images.githubusercontent.com/77662970/190920055-e802ee2a-011a-41b5-8e8e-945492393e03.png)
## 3. Modifiez votre programme pour que les notes ne soient plus données en paramètres, mais saisies et
stockées au fur et à mesure dans un tableau.
```
#!/bin/bash
function is_number ()
{
re="^[+-]?[0-9]+([.][0-9]+)?$'

if ! [[ $1 =~ $re ]] ; then
    return 1
else
    return O
fi
}

read -p "Combien de notes allez-vous entrer ? " note
for i in $(seq 1 $note)
{
read -p "Entrez une note" tab[$i]
}

echo ${tab[@]}
if (( $note > O )); then
        MAX=200
        MIN=200
else
        echo "Entrez minimum 2 notes"
        exit
fi

function print_stat ()
{
for VAR in "$@"
 do
   is_number $VAR
   if [[ $? -ne 0 ]]; then
        echo "Entrez des nombres compris entre -100 et 100"
fi
if (( $VAR > $MAX )); then
        MAX=$VAR
fi
if (( $VAR < $MIN )); then
        MIN=$VAR
fi
moy=$(( $moy + $VAR ))
done
moy=$(( $moy / $# ))

echo "Le minimum est $MIN"
echo "Le maximul est $MAX"
echo "La moyenne est $moy"
}

print_stat $[tab[@]}
```
![image](https://user-images.githubusercontent.com/77662970/193452429-03099f4e-5518-4b97-86b1-b826edfac27b.png)

