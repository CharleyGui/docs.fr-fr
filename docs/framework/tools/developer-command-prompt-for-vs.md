---
title: Invite de commandes développeur pour Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715837"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Invite de commandes développeur pour Visual Studio

Developer Command Prompt for Visual Studio vous permet d’utiliser plus facilement les outils cadres .NET. Il s’agit d’une invite de commande qui définit automatiquement des variables spécifiques de l’environnement. Après l’ouverture de Developer Command Prompt, vous pouvez `ildasm` entrer `clrver`les commandes pour des outils [cadre .NET](index.md) tels que ou .

## <a name="prerequisites"></a>Conditions préalables requises

- [Studio visuel 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Rechercher l’invite de commandes sur votre ordinateur

Vous pouvez avoir plusieurs invites de commande, selon la version de Visual Studio et les SDK supplémentaires et les charges de travail que vous avez installées. Si les étapes suivantes ne fonctionnent pas, vous pouvez essayer de [localiser manuellement les fichiers sur votre machine](#manually-locate-the-files-on-your-machine) ou démarrer [l’invite de commande de l’intérieur de Visual Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Sélectionnez La clé de logo **Start** ![Windows sur le clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) et faites défiler la lettre **V**.

1. Élargissez le dossier **Visual Studio 2019.**

1. Choisissez **Developer Command Prompt pour VS 2019** (ou l’invite de commande que vous souhaitez utiliser).

   Alternativement, vous pouvez commencer à taper le nom de l’invite de commande dans la boîte de recherche sur la barre des tâches, et choisir le résultat que vous voulez que la liste de résultat commence à afficher les correspondances de recherche.

   ![Gif animé montrant le comportement de recherche sur Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows de votre clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) de votre clavier, par exemple.

1. Sur l’écran **Démarrer,** appuyez sur **Ctrl**+**Tab** pour ouvrir la liste **Apps,** puis appuyez sur **V**. Cela fait ressortir une liste qui comprend toutes les invites de commande Visual Studio installées.

1. Choisissez **Developer Command Prompt pour VS 2019** (ou l’invite de commande que vous souhaitez utiliser).

### <a name="windows-7"></a>Windows 7

1. Choisissez **Démarrer,** puis d’élargir **tous les programmes**.

1. Choisissez **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt pour VS 2019**, ou l’invite de commande que vous souhaitez utiliser.

   ![Menu Windows 7 Démarrer avec l’invite de commande surlignée](./media/developer-command-prompt-for-vs/windows7-menu.png)

Si vous avez d’autres SDK installés, tels que windows [10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [des versions précédentes,](https://developer.microsoft.com/windows/downloads/sdk-archive)vous pouvez voir des invites de commande supplémentaires. Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.

## <a name="manually-locate-the-files-on-your-machine"></a>Recherche manuelle des fichiers sur votre ordinateur

Habituellement, les raccourcis pour les invites de commande que vous avez installé sont placés dans le dossier **de menu Démarrer** pour Visual Studio, comme dans % *ProgramData%-Microsoft-Windows-Start Menu-Programs-Visual Studio 2019 -Visual Studio Tools*. Mais si, pour une raison quelconque, la recherche de l’invite de commande ne produit pas les résultats attendus, vous pouvez essayer de localiser manuellement le raccourci sur votre machine. Essayez de rechercher le nom du fichier d’invite de commande, tel que *VsDevCmd.bat*, ou allez au dossier Tools, tels que *%ProgramFiles (x86)% -Microsoft Visual Studio-2019-Community-Common7-Tools* (changements de chemin selon votre version Visual Studio, édition et emplacement d’installation).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Démarrer l’invite de commande de l’intérieur Visual Studio

Pour un accès plus facile, vous pouvez ajouter Developer Command Prompt, ou toute autre invite de commande, au menu Tools dans Visual Studio. Pour cela, il vous suffit de l’ajouter à la liste des outils externes. Voici la procédure à suivre :

1. Ouvrez Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Continuer sans code**.

1. Sur la barre de menu, choisissez **Tools** > **External Tools**.

1. Dans la boîte de dialogue **Outils externes**, choisissez le bouton **Ajouter**. Une nouvelle entrée apparaît.

1. Entrez un **titre** pour votre nouvel élément de menu, par exemple `Command Prompt`.

1. Dans le champ **de commande,** spécifiez le fichier que vous souhaitez lancer, tel que `%comspec%` ou `C:\Windows\System32\cmd.exe`.

1. Dans le domaine **Arguments,** spécifiez où trouver `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`l’invite de commande spécifique que vous souhaitez utiliser, comme . Cette commande lance le Developer Command Prompt qui est installé avec Visual Studio 2019 Community. Changez cette valeur en fonction de l’emplacement d’installation, de l’édition et de la version de Visual Studio.

1. Dans le domaine **de l’annuaire initial,** spécifiez l’annuaire dans lequel l’invite de commande commencera. Choisissez une valeur telle que **l’annuaire de projet** en sélectionnant la flèche à côté du champ.

1. Choisissez le bouton **OK**.

   ![Dialogue outils externes avec les valeurs de champ remplies.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Le nouvel élément de menu est ajouté et vous pouvez accéder à l’invite de commandes à partir du menu Outils.

   ![Élément de menu d’invite de commandes dans Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Voir aussi

- [Outils du .NET Framework](index.md)
- [Gestion des outils externes](/visualstudio/ide/managing-external-tools)
- [Utilisez l’outil Microsoft CMD de la ligne de commande](/cpp/build/building-on-the-command-line)
