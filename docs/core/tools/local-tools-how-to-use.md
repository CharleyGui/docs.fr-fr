---
title: 'Tutorial: Installer et utiliser .NET Core outils locaux'
description: Apprenez à installer et à utiliser un outil .NET comme outil local.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156697"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

Ce tutoriel vous apprend à installer et à utiliser un outil local. Vous utilisez un outil que vous créez dans le [premier tutoriel de cette série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Conditions préalables requises

* Compléter le [premier tutoriel de cette série](global-tools-how-to-create.md).
* Installez le temps d’exécution .NET Core 2.1.

  Pour ce tutoriel, vous installez et utilisez un outil qui cible .NET Core 2.1, de sorte que vous devez avoir ce temps d’exécution installé sur votre machine. Pour installer l’heure d’exécution 2.1, rendez-vous sur la [page de téléchargement .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) et trouvez le lien d’installation runtime dans la colonne **Run apps - Runtime.**

## <a name="create-a-manifest-file"></a>Créer un fichier manifeste

Pour installer un outil d’accès local uniquement (pour l’annuaire actuel et les sous-directeurs), il doit être ajouté à un fichier manifeste.

Du dossier *microsoft.botsay,* naviguez jusqu’à un niveau au dossier *de dépôt* :

```console
cd ..
```

Créez un fichier manifeste en exécutant la nouvelle commande [dotnet](dotnet-new.md) :

```dotnetcli
dotnet new tool-manifest
```

La sortie indique la création réussie du fichier.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Le fichier *.config/dotnet-tools.json* n’a pas encore d’outils :

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Les outils énumérés dans un fichier manifeste sont mis à la disposition de l’annuaire et des sous-directeurs actuels. L’annuaire actuel est celui qui contient le répertoire *.config* avec le fichier manifeste.

Lorsque vous utilisez une commande CLI qui fait référence à un outil local, le SDK recherche un fichier manifeste dans l’annuaire actuel et les répertoires parent. S’il trouve un fichier manifeste, mais que le fichier n’inclut pas l’outil référencé, il poursuit la recherche à travers les répertoires parentaux. La recherche se termine lorsqu’elle trouve l’outil `isRoot` référencé ou qu’elle trouve un fichier manifeste avec l’ensemble `true`de .

## <a name="install-botsay-as-a-local-tool"></a>Installer botsay comme un outil local

Installez l’outil à partir du paquet que vous avez créé dans le premier tutoriel:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Cette commande ajoute l’outil au fichier manifeste que vous avez créé dans l’étape précédente. La sortie de commande indique dans quel fichier manifeste l’outil nouvellement installé est :

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Le fichier *.config/dotnet-tools.json* dispose désormais d’un outil :

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>Utiliser l’outil

Invoquez l’outil en exécutant la `dotnet tool run` commande à partir du dossier de *dépôt* :

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Restaurer un outil local installé par d’autres

Vous installez généralement un outil local dans le répertoire racine du référentiel. Après avoir vérifié le fichier manifeste au référentiel, d’autres développeurs peuvent obtenir le dernier fichier manifeste. Pour installer tous les outils énumérés dans le `dotnet tool restore` fichier manifeste, ils peuvent exécuter une seule commande.

1. Ouvrez le fichier *.config/dotnet-tools.json,* et remplacez le contenu par le JSON suivant :

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. Remplacez-vous `<name>` par le nom que vous avez utilisé pour créer le projet.

1. Enregistrez vos modifications.

   Faire ce changement est la même chose que d’obtenir la `dotnetsay` dernière version du référentiel après que quelqu’un d’autre a installé le paquet pour l’annuaire du projet.

1. Exécutez la commande `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   La commande produit la sortie comme l’exemple suivant :

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Vérifiez que les outils sont disponibles :

   ```dotnetcli
   dotnet tool list
   ```

   La sortie est une liste de paquets et de commandes, similaire à l’exemple suivant :

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Testez les outils :

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Mettre à jour un outil local

La version installée `dotnetsay` de l’outil local est 2.1.3.  La dernière version est 2.1.4. Utilisez la commande [de mise à jour de l’outil dotnet](dotnet-tool-update.md) pour mettre à jour l’outil de la dernière version.

```dotnetcli
dotnet tool update dotnetsay
```

La sortie indique le nouveau numéro de version :

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

La commande de mise à jour trouve le premier fichier manifeste qui contient l’ID du paquet et le met à jour. S’il n’y a pas d’id de paquet dans un fichier manifeste qui est dans la portée de la recherche, le SDK ajoute une nouvelle entrée au fichier manifeste le plus proche. La portée de recherche est en place `isRoot = true` à travers les répertoires des parents jusqu’à ce qu’un fichier manifeste avec est trouvé.

## <a name="remove-local-tools"></a>Supprimer les outils locaux

Retirez les outils installés en exécutant [l’outil dotnet désinstaller la](dotnet-tool-uninstall.md) commande :

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Dépanner

Si vous obtenez un message d’erreur tout en suivant le tutoriel, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations, voir [outils .NET Core](global-tools.md)
