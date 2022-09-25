[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8465525&assignment_repo_type=AssignmentRepo)

# TP 2:
1.
```
printenv PATH
```
![image](https://user-images.githubusercontent.com/77662970/189591857-7fc5429b-3861-4470-ab75-0f3547f84e5b.png)

2. La variable $HOME nous raméne directement dans notre répertoire avec la commande cd $HOME.

3. La variable LANG permet de voir la langue utilisé par le système, la variable pwd permet de lister le répertoire de travail courant dans l'interpréteur de commande, OLDPWD permet d'accéder a l'ancien repertoire graxce au chemin enregistrer et SHELL est l'interpreteur de commande de l'utilisateur.

4.  Pour créer une variable locale, on utilise la commande ```nomVariable="contenu"```.                                 Ici, nous utilisons 
```
MY_VAR"test"
```

. Pour vérifier son existence, il faut taper
```
echo "$MY_VAR"
```
et le système devrait retourner Test.

![image](https://user-images.githubusercontent.com/77662970/192110618-ae4eb7ba-6659-4fdd-9346-b1fafdae5975.png)


5.La commande bash nous emmenne dans un nouveau interpréteur de commande. La variable MY_Var n'existe car nous l'avons crée  dans un autre interpreteur. 

6. En la transformant en variable d'environement la variable est disponible a partir de tous les shell ou interpréteur.

8. 
```
echo "Bonjour à vous, $NOM"
```

![image](https://user-images.githubusercontent.com/77662970/192109908-f9327558-7f05-40d4-8365-a8af1cb9faeb.png)


9.La commande unset va supprimer la variable dans sa totalité et alors mettre 0 commentaire la variable existera toujours.

10. 
```
echo "$HOME"
```

![image](https://user-images.githubusercontent.com/77662970/192109874-6eae28f2-2509-4bac-bb27-fbfaa7459725.png)


# Programmation BASH

## Exercice 2. Contrôle de mot de passe


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


## Exercice 3. Expressions rationnelles

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

## Exercice 4. Contrôle d’utilisateur
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


## Exercice 5. Factorielle

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


## Exercice 6. Le juste prix
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


## Exercice 7. Statistiques
1.
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

2.
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

