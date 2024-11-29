# Plugin TV by Orange

Ce plugin permet de contrôler un décodeur Orange/Sosh.

> **IMPORTANT**
>
> L'API Orange n'est pas publique, les requêtes ont été sniffées à partir de l'application mobile et sont donc suseptibles de changer à tout moment.  
> Le plugin est donc théoriquement compatible avec tous les décodeurs qui sont compatibles avec l'application mobile.

## Configuration du plugin

Ce plugin ne nécessite pas de configuration particulière et doit simplement être activé après l’installation.

## Configuration des équipements

- **Nom de l’équipement** : permet de donner un nom à votre équipement
- **Objet parent** : permet d'indiquer l’objet parent auquel appartient l’équipement
- **Catégorie** : permet de choisir les catégories de l’équipement (il peut appartenir à plusieurs catégories)
- **Activer** : permet de rendre votre équipement actif
- **Visible** : permet de rendre votre équipement visible
- **Adresse IP du décodeur** : permet de choisir l'adresse IP du décodeur à contrôler
- **Description de l’équipement** : permet de donner une description à votre équipement

## Configuration des commandes

### Commandes info

Cette commande passe à 0 si le décodeur n'est pas joignable :
- **Online**

Les commandes suivantes correspondent aux valeur brutes retournées par votre décodeur :
- **Active Standby State** : inversé en base par défaut pour retourner 1 quand votre décodeur est allumé car il s'agit de l'état de la veille et non de l'état du décodeur
- **OSD Context**
- **Played Media Type**
- **Played Media State**
- **Played Media Id** : correspond à l'ID EPG de votre liste de chaînes
- **Played Media Context**
- **Played Media Position**
- **Time Shifting State**
- **MAC Address**
- **Friendly Name**
- **Npvr Support**

> **NOTE**
>
> Les commandes info sont mise à jour toutes les 5 secondes.  
> Il est impossible de déterminer à l'avance les valeurs possibles. Vous devrez donc vérifier les valeurs des commandes info en fonction de l'utilisation que vous faites de votre décodeur.  
> Le plugin a été développé avec un Décodeur TV 4, il est possible que les décodeurs plus récents retournent plus d'informations.  
> Pour vérifier cela, il faut passer le niveau de log du plugin en debug et examiner le JSON retourné par votre décodeur pour repérer s'il contient des clés qui ne figurent pas dans la liste de commandes ci-dessus.  
> Si c'est le cas, veuillez me le signaler sur Community afin que je puisse rajouter les commandes correspondantes.  
> Si vous ne savez pas lire un JSON, envoyez-le-moi simplement sur Community.

Les commandes suivantes sont déduites de votre liste de chaînes en fonction de la valeur de Played Media Id retournée par votre décodeur, donc si votre liste de chaînes est erronée ces commandes le seront aussi :
- **Channel Number**
- **Channel Text**

Cette commande (non affichées par défaut) est purement virtuelle et ne reflète absolument pas l'état réel du volume de votre décodeur, elle est destinée à la compatibilité avec les types génériques et les assistants vocaux :
- **Volume State**

### Commandes action

Les commandes suivantes sont mises à jour automatiquement lors de la sauvegarde de l'équipement :
- **Channel Select** : contient toutes les chaînes dans l'ordre respectif de votre liste de chaînes
- **Channel Select Custom** : à venir

Les commandes suivantes correspondent aux touches de la télécommande dans l'application mobile :
- **Vod**
- **Up**
- **On Off**
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

Les commandes suivantes (non affichées par défaut) sont destinées à la compatibilité avec les types génériques et les assistants vocaux :
- **Channel Slider**
- **Volume Slider**

## Configuration des chaînes

Une chaîne est identifiée à partir de son ID EGP (Played Media Id), si le plugin détecte un ID EGP non présent dans votre liste de chaînes, il générera une erreur en vous indiquant le numéro de l'ID EGP inconnu. Le problème est que si vous n'êtes pas présent au moment de l'erreur, il faudra retrouver quelle chaîne a été mise au moment de l'erreur, ce qui n'est pas évident je vous l'accorde, sinon il faudra attendre que l'erreur se reproduise et que vous puissiez identifier la chaîne en question. Vous pouvez bien sûr modifier manuellement les chaînes ou en ajouter de nouvelles mais l'idéal est de m'en informer sur Community pour que je puisse corriger les chaînes existantes et en ajouter de nouvelles pour tous les utilisateurs. Pour corriger ou ajouter une chaîne j'aurais besoin des trois informations suivantes : Nom - Numéro - ID EGP (Played Media Id).

> **NOTE**
>
> Les chaînes ne sont pas affichées par défaut mais ce sont des commandes action que vous pouvez afficher comme n'importe quelle autre commande action.