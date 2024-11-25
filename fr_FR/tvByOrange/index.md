# Plugin TV by Orange

Ce plugin permet de contrôler un décodeur Orange/Sosh.

> **IMPORTANT**
>
> L'API Orange n'est pas publique, les requêtes ont été sniffées à partir de l'application mobile et sont donc suseptibles de changer.
> Le plugin est donc théoriquement compatible avec tous les décodeurs qui sont compatibles avec l'application mobile.

## Configuration du plugin

Ce plugin ne nécessite pas de configuration particulière et doit simplement être activé après l’installation.

## Configuration des équipements

- **Nom de l’équipement** : permet de donner un nom de votre équipement
- **Objet parent** : permet d'indiquer l’objet parent auquel appartient l’équipement
- **Catégorie** : permet de choisir les catégories de l’équipement (il peut appartenir à plusieurs catégories)
- **Activer** : permet de rendre votre équipement actif
- **Visible** : permet de rendre votre équipement visible
- **Adresse IP du décodeur** : permet de choisir l'adresse IP du décodeur à contrôler
- **Description de l’équipement** : permet de donner une description à votre équipement

## Configuration des commandes

### Commandes info

Les commandes suivantes sont les valeur brutes retournées par le décodeur :
- **Active Standby State** : inversé en base par défaut pour retourné 1 quand le décodeur est allumé car il s'agit de l'état de la veille et non de l'état du décodeur
- **OSD Context**
- **Played Media Type**
- **Played Media State**
- **Played Media Id** : correspond à l'ID EPG de votre liste de chaînes
- **Played Media Context**
- **Played Media Position**
- **Time Shifting State**
- **MAC Address**
- **Friendly Name**

> **NOTE**
>
> Le retour d'état s'effectue toutes les 5 secondes.

> **NOTE**
>
> Il n'est pas possible de connaître les valeurs possibles, c'est donc à vous de voir ce que retourne ces commandes en fonction de ce que vous faîte sur le décodeur.

> **NOTE**
>
> Le plugin a été développé avec un Décodeur TV 4, il possible que les décodeurs plus récents retournent plus d'information, pour le vérifier il faut passer le plugin en debug et voir si il y a des clé dans le JSON non présentent dans la liste de commande ci-dessus. Si c'est le cas, il faut me contacter sur Community pour que je puisse rajouter les commandes correspondantes.

Les commandes suivantes sont déduites de votre liste de chaînes en fonction de la valeur de Played Media Id retourné par le décodeur, donc si votre liste est erronés ces commandes le seront aussi :
- **Channel Number**
- **Channel Text**

Cette commande (non affichées par défaut) est purement virtuel et ne reflète absolument l'état réel du volume de votre décodeur, elle est destinée à la compatibilité avec les types génériques et les assistants vocaux :
- **Volume State**

### Commandes action

Les commandes suivantes sont mises à jour automatiquement lors de la sauvegarde de l'équipement :
- **Channel Select** : contient toutes les chaînes dans l'odre respectif de votre liste de châines
- **Channel Select Custom** : à venir

Les commandes suivantes correspondent aux touches de la télécommande dans l'application mobile :
- **Vod**
- **Up**
- **onOff**
- **Left**
- **OK**
- **Right**
- **Back**
- **Down**
- **Menu**
- **Volume Up**
- **1**
- **2**
- **3**
- **Channel Up**
- **Volume Down**
- **4**
- **5**
- **6**
- **Mute**
- **7**
- **8**
- **9**
- **0**
- **Stop**
- **Rec**
- **Fbwd**
- **Play Pause**
- **Ffwd**

Les commandes suivantes (non affichées par défaut) sont des doublons des commandes ci-dessus et sont destinées à la compatibilité avec les types génériques et les assistants vocaux :
- **Off**
- **Unmute**
- **Pause**

## Configuration des chaînes

