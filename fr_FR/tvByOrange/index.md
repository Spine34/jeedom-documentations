# Plugin TV by Orange

Ce plugin permet de contrôler un décodeur Orange/Sosh.

> **IMPORTANT**
>
> L'API Orange n'est pas publique, les requêtes ont été sniffées à partir de l'application mobile et sont donc suseptibles de changer.
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

Les commandes suivantes sont les valeur brutes retournées par le décodeur :
- **Active Standby State** : inversé en base par défaut pour retourner 1 quand le décodeur est allumé car il s'agit de l'état de la veille et non de l'état du décodeur
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
> Il n'est pas possible de connaître les valeurs possibles, c'est donc à vous de voir ce que retourne ces commandes en fonction de ce que vous faîte sur votre décodeur.

> **NOTE**
>
> Le plugin a été développé avec un Décodeur TV 4, il possible que les décodeurs plus récents retournent plus d'informations. Pour le vérifier il faut passer le plugin en debug et voir si il y a des clés dans le JSON non présentes dans la liste de commandes ci-dessus. Si c'est le cas, il faut me le signaler sur Community pour que je puisse rajouter les commandes correspondantes. Si vous ne savez pas lire un JSON il suffit de me l'envoyer sur Community.

Les commandes suivantes sont déduites de votre liste de chaînes en fonction de la valeur de Played Media Id retournée par le décodeur, donc si votre liste est erronés ces commandes le seront aussi :
- **Channel Number**
- **Channel Text**

Cette commande (non affichées par défaut) est purement virtuelle et ne reflète absolument pas l'état réel du volume de votre décodeur, elle est destinée à la compatibilité avec les types génériques et les assistants vocaux :
- **Volume State**

### Commandes action

Les commandes suivantes sont mises à jour automatiquement lors de la sauvegarde de l'équipement :
- **Channel Select** : contient toutes les chaînes dans l'odre respectif de votre liste de châines
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

Une chaîne est identifiée à partir de son ID EGP (Played Media Id), si le plugin détecte un ID EGP non présent dans votre liste de chaînes, il générera une erreur en vous indiquant le numéro de l'ID EGP inconnu. Le problème est que si vous n'êtes pas présent au moment de l'erreur, il faudra retrouver quelle chaîne a été mise au moment de l'erreur, ce qui n'est pas évident je vous l'accorde, sinon il faudra attendre que l'erreur se reproduise et que vous puissiez identifier la chaîne en question. Vous pouvez bien sûr modifier manuellement les chaînes ou en ajouter de nouvelles mais l'idéal est de m'en informer sur Community pour que je puisse corriger les chaînes existantes et en ajouter de nouvelle pour tous les utilisateurs. Pour corriger ou ajouter une chaîne j'aurais besoin des trois informations suivantes : Nom - Numéro - ID EGP (Played Media Id).

> **NOTE**
>
> Les chaînes ne sont pas affichées par défaut mais ce sont des commandes action que vous pouvez afficher comme n'importe quelle autre commande action.