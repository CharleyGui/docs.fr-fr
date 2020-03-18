---
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
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342365"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Comment : définir des variables d’environnement pour la ligne de commande Visual Studio

Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande.

> [!NOTE]
> Visual Studio 2015 et les versions précédentes ont utilisé VSVARS32.bat, pas VsDevCmd.bat dans le même but. Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.

Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes. Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.

### <a name="to-run-vsdevcmdbat"></a>Pour exécuter VsDevCmd.BAT

1. À partir du menu **Démarrer,** ouvrez **l’invite de commande de développeur pour VS 2019.**  C’est dans le dossier **Visual Studio 2019.**

2. Modification de la\\*version*\\studio visuel «Program Files-Microsoft)*offre*de «Common7-Tools\\ou fichiers de programme (x86) Microsoft Visual Studio*Version*\\*offrant*la sous-direction de votre installation.  (*Version* *2019* pour la version actuelle. *Offre* correspond à *Enterprise*, *Professional* ou *Community*.)

3. Exécutez VsDevCmd.bat en tapant **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd.bat peut varier d’un ordinateur à l’autre. Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé par un fichier VsDevCmd.bat d’un autre ordinateur. À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.

### <a name="available-options-for-vsdevcmdbat"></a>Options disponibles pour VsDevCmd.BAT

Pour afficher les options disponibles pour VsDevCmd.BAT, exécutez la commande avec l’option `-help` :

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Voir aussi

- [Génération en ligne de commande avec csc.exe](./command-line-building-with-csc-exe.md)
