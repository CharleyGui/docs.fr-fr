---
title: 'Procédure : Définir des variables d’environnement pour la ligne de commande Visual Studio'
ms.date: 09/29/2017
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
ms.openlocfilehash: 9b26f6b80488ad4043054cd23f0f351773e8d6d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602854"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Procédure : Définir des variables d’environnement pour la ligne de commande Visual Studio

Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande.

> [!NOTE]
> Le fichier VsDevCmd.bat est un nouveau fichier fourni avec Visual Studio 2017. Visual Studio 2015 et versions antérieures utilisaient VSVARS32.bat dans le même but. Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.

Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes. Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.

### <a name="to-run-vsdevcmdbat"></a>Pour exécuter VsDevCmd.BAT

1. Dans le menu **Démarrer**, ouvrez **l’invite de commandes développeur pour VS2017**.  Elle se trouve dans le dossier **Visual Studio 2017**.

2. Accédez au sous-répertoire \Program Files\Microsoft Visual Studio\\*Version*\\*Offre*\Common7\Tools ou \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offre*\Common7\Tools de votre installation.  (*Version* correspond à *2017* pour la version actuelle. *Offre* correspond à *Enterprise*, *Professional* ou *Community*.)

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
