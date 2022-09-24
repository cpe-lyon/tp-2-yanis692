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

![image](https://user-images.githubusercontent.com/77662970/190355814-79235c66-7f20-430b-824d-704228b8073b.png)


![image](https://user-images.githubusercontent.com/77662970/190355958-8d388945-132a-483f-a743-a6a6743accbd.png)


## Exercice 5. Factorielle


![image](https://user-images.githubusercontent.com/77662970/190897766-bbba2828-1981-420e-8378-52258cbc9031.png)


![image](https://user-images.githubusercontent.com/77662970/190897787-39278698-be2f-481a-b6da-3d432d67dd6f.png)


## Exercice 6. Le juste prix


![image](https://user-images.githubusercontent.com/77662970/190899126-aec6980d-1282-40a2-9e3f-8aff24569cfa.png)



![image](https://user-images.githubusercontent.com/77662970/190899088-7de91e65-98eb-4117-86e9-273cb85d3d85.png)


## Exercice 7. Statistiques

2.
![image](https://user-images.githubusercontent.com/77662970/190920012-81edd3fe-827d-4053-a943-d3334f06257e.png)


![image](https://user-images.githubusercontent.com/77662970/190920055-e802ee2a-011a-41b5-8e8e-945492393e03.png)

