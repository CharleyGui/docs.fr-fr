---
description: 'Comment : définir des variables d’environnement pour la ligne de commande Visual Studio'
title: 'Comment : définir des variables d’environnement pour la ligne de commande Visual Studio'
ms.date: 12/20/2019
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: b985c85e2fddce459ed68b3d07ba7d54a8b2d0a7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125603"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Comment : définir des variables d’environnement pour la ligne de commande Visual Studio

Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande.

> [!NOTE]
> Visual Studio 2015 et versions antérieures utilisaient VSVARS32.bat, pas VsDevCmd.bat dans le même but. Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.

Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes. Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.

### <a name="to-run-vsdevcmdbat"></a>Pour exécuter VsDevCmd.BAT

1. Dans le menu **Démarrer** , ouvrez le **Invite de commandes développeur pour vs 2019**.  Il se trouve dans le dossier **Visual Studio 2019** .

2. Accédez au sous-répertoire \Program Files\Microsoft Visual Studio \\ *version* \\ *offer*\Common7\Tools ou \Program Files (x86) \Microsoft Visual Studio \\ *version* \\ *offer*\Common7\Tools de votre installation.  (La*version* est *2019* pour la version actuelle. *Offre* correspond à *Enterprise*, *Professional* ou *Community*.)

3. Exécutez VsDevCmd.bat en tapant **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd.bat peut varier d’un ordinateur à l’autre. Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé par un fichier VsDevCmd.bat d’un autre ordinateur. À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.

### <a name="available-options-for-vsdevcmdbat"></a>Options disponibles pour VsDevCmd.BAT

Pour afficher les options disponibles pour VsDevCmd.BAT, exécutez la commande avec l’option `-help` :

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Voir aussi

- [Génération à partir de la ligne de commande avec csc.exe](./command-line-building-with-csc-exe.md)
