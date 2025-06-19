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
- **Ajouter un message** : Permet d'ajouter un message dans le Centre de Messages lorqu'une chaîne qui n'existe pas dans la liste des chaînes est détectée
- **Description de l’équipement** : permet de donner une description à votre équipement

## Configuration des commandes

### Commandes info

Cette commande passe à 0 si le décodeur n'est pas joignable :
- **Online**

Les commandes suivantes correspondent aux valeurs brutes retournées par votre décodeur :
- **Active Standby State** : inversé en base par défaut pour retourner 1 quand votre décodeur est allumé car il s'agit de l'état de la veille et non de l'état du décodeur
- **OSD Context**
- **Played Media Type**
- **Played Media State**
- **Played Media Id** : correspond à l'ID EPG de votre liste de chaînes
- **Played Media Context Id**
- **Played Media Position**
- **Time Shifting State** : décalage avec le direct (passe à 1 quand on utilise le contrôle du direct)
- **MAC Address**
- **WoL Support**
- **Friendly Name**
- **Npvr Support**

Les commandes suivantes sont déduites de votre liste de chaînes en fonction de la valeur de la commande **Played Media Id** retournée par votre décodeur, donc si votre liste de chaînes est erronée les valeurs de ces commandes le seront aussi :
- **Channel Number**
- **Channel Text**

Cette commande (non affichée par défaut) est purement virtuelle et ne reflète absolument pas l'état réel du volume de votre décodeur, elle est destinée à la compatibilité avec les types génériques et les assistants vocaux :
- **Volume State**

> **IMPORTANT**
>
> Certains décodeurs ne répondent pas aux requêtes lorsqu'ils sont en veille, notamment quand le mode Economie d'énergie est activé.

> **NOTE**
>
> Les commandes info sont mises à jour toutes les 5 secondes.

### Commandes action

Les commandes suivantes sont mises à jour automatiquement lors de la sauvegarde de l'équipement :
- **Channel Select** : contient toutes les chaînes dans l'ordre respectif de votre liste de chaînes
- **Custom Channel Select** : contient toutes les chaînes sélectionnées dans l'ordre respectif de votre liste de chaînes

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
- **Mute Unmute**
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

Une chaîne est identifiée par son ID EGP (Played Media ID). Les numéros de chaînes sont indiqués à titre informatif, mais ne sont pas utilisés dans les requêtes.
Vous pouvez modifier manuellement les chaînes ou en ajouter de nouvelles, mais l’idéal est de m’en informer afin que je puisse corriger les chaînes existantes et en ajouter de nouvelles pour tous les utilisateurs.
Pour corriger ou ajouter une chaîne, j’aurai besoin des trois informations suivantes : Nom – Numéro – ID EGP (Played Media ID).


> **NOTE**
>
> Les chaînes ne sont pas affichées par défaut mais ce sont des commandes action que vous pouvez afficher comme n'importe quelle autre commande action.