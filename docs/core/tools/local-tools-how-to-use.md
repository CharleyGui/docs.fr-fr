---
title: 'Didacticiel : installer et utiliser les outils locaux .NET Core'
description: Découvrez comment installer et utiliser un outil .NET comme un outil local.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 555497a71d54713e62e54f8f293afdf74ead1743
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062673"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Didacticiel : installer et utiliser un outil local .NET Core à l’aide de l’CLI .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

Ce didacticiel vous apprend à installer et à utiliser un outil local. Vous utilisez un outil que vous créez dans le [premier didacticiel de cette série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Prérequis

* Effectuez le [premier didacticiel de cette série](global-tools-how-to-create.md).
* Installez le Runtime .NET Core 2,1.

  Pour ce didacticiel, vous installez et utilisez un outil qui cible .NET Core 2,1. vous devez donc installer ce Runtime sur votre ordinateur. Pour installer le runtime 2,1, accédez à la [page de téléchargement de .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) et recherchez le lien d’installation du runtime dans la colonne **exécuter des applications-Runtime** .

## <a name="create-a-manifest-file"></a>Créer un fichier manifeste

Pour installer un outil pour un accès local uniquement (pour le répertoire et les sous-répertoires actifs), il doit être ajouté à un fichier manifeste.

Dans le dossier *Microsoft. botsay* , accédez à un niveau vers le dossier du *référentiel* :

```console
cd ..
```

Créez un fichier manifeste en exécutant la commande [dotnet New](dotnet-new.md) :

```dotnetcli
dotnet new tool-manifest
```

La sortie indique que la création du fichier a réussi.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Le fichier *. config/dotnet-tools.jssur* le fichier n’a pas encore d’outils :

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Les outils répertoriés dans un fichier manifeste sont disponibles dans le répertoire et les sous-répertoires actifs. Le répertoire actif est celui qui contient le répertoire *. config* avec le fichier manifeste.

Lorsque vous utilisez une commande CLI qui fait référence à un outil local, le kit de développement logiciel (SDK) recherche un fichier manifeste dans le répertoire actif et les répertoires parents. S’il trouve un fichier manifeste, mais que le fichier n’inclut pas l’outil référencé, il continue la recherche dans les répertoires parents. La recherche se termine lorsqu’elle trouve l’outil référencé ou lorsqu’elle trouve un fichier manifeste ayant la `isRoot` valeur `true` .

## <a name="install-botsay-as-a-local-tool"></a>Installer botsay en tant qu’outil local

Installez l’outil à partir du package que vous avez créé dans le premier didacticiel :

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Cette commande ajoute l’outil au fichier manifeste que vous avez créé à l’étape précédente. La sortie de la commande indique le fichier manifeste dans lequel se trouve l’outil qui vient d’être installé :

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Le fichier *. config/dotnet-tools.js* est désormais doté d’un outil :

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

Appelez l’outil en exécutant la `dotnet tool run` commande à partir du dossier du *référentiel* :

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Restaurer un outil local installé par d’autres

En général, vous installez un outil local dans le répertoire racine du référentiel. Une fois que vous avez vérifié le fichier manifeste dans le référentiel, d’autres développeurs peuvent récupérer le dernier fichier manifeste. Pour installer tous les outils listés dans le fichier manifeste, ils peuvent exécuter une seule `dotnet tool restore` commande.

1. Ouvrez le fichier *. config/dotnet-tools.jssur* le fichier, puis remplacez le contenu par le code JSON suivant :

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

1. Remplacez `<name>` par le nom que vous avez utilisé pour créer le projet.

1. Enregistrez vos modifications.

   Cette modification est identique à l’obtention de la version la plus récente à partir du référentiel après que quelqu’un d’autre a installé le package `dotnetsay` pour le répertoire du projet.

1. Exécutez la commande `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   La commande produit une sortie similaire à l’exemple suivant :

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Vérifiez que les outils sont disponibles :

   ```dotnetcli
   dotnet tool list
   ```

   La sortie est une liste de packages et de commandes, similaire à l’exemple suivant :

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Testez les outils :

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Mettre à jour un outil local

La version installée de l’outil local `dotnetsay` est 2.1.3.  La version la plus récente est 2.1.4. Utilisez la commande de [mise à jour de l’outil dotnet](dotnet-tool-update.md) pour mettre à jour l’outil avec la dernière version.

```dotnetcli
dotnet tool update dotnetsay
```

La sortie indique le nouveau numéro de version :

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

La commande Update recherche le premier fichier manifeste qui contient l’ID de package et le met à jour. S’il n’existe aucun ID de package de ce type dans un fichier manifeste qui se trouve dans l’étendue de la recherche, le kit de développement logiciel (SDK) ajoute une nouvelle entrée au fichier manifeste le plus proche. L’étendue de recherche se trouve dans les répertoires parents jusqu’à ce qu’un fichier manifeste avec `isRoot = true` soit trouvé.

## <a name="remove-local-tools"></a>Supprimer les outils locaux

Supprimez les outils installés en exécutant la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) :

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Dépannage

Si vous obtenez un message d’erreur lors de la suite du didacticiel, consultez [résoudre les problèmes d’utilisation de l’outil .net Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations, consultez [outils .net Core](global-tools.md)
