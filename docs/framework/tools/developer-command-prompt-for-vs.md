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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715837"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Invite de commandes développeur pour Visual Studio

Invite de commandes développeur pour Visual Studio vous permet d’utiliser plus facilement les outils .NET Framework. Il s’agit d’une invite de commandes qui définit automatiquement des variables d’environnement spécifiques. Après avoir ouvert Invite de commandes développeur, vous pouvez entrer les commandes pour [.NET Framework outils](index.md) tels que `ildasm` ou `clrver`.

## <a name="prerequisites"></a>Configuration requise

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Rechercher l’invite de commandes sur votre ordinateur

Vous pouvez avoir plusieurs invites de commande, en fonction de la version de Visual Studio et de tous les kits de développement logiciel (SDK) et charges de travail supplémentaires que vous avez installés. Si les étapes suivantes ne fonctionnent pas, vous pouvez essayer de [localiser manuellement les fichiers sur votre ordinateur](#manually-locate-the-files-on-your-machine) ou [de démarrer l’invite de commandes à partir de Visual Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Sélectionnez **démarrer** ![touche du logo Windows sur le clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) et faites défiler jusqu’à la lettre **V**.

1. Développez le dossier **Visual Studio 2019** .

1. Choisissez **invite de commandes développeur pour VS 2019** (ou l’invite de commandes que vous souhaitez utiliser).

   Vous pouvez également commencer à taper le nom de l’invite de commandes dans la zone de recherche de la barre des tâches, puis choisir le résultat à partir duquel la liste des résultats commence à afficher les résultats de la recherche.

   ![Image GIF animée montrant le comportement de recherche sur Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows de votre clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) de votre clavier, par exemple.

1. Dans l’écran d' **Accueil** , appuyez sur CTRL+**onglet** pour ouvrir la liste des **applications** , puis appuyez sur la **touche** **V**. Une liste incluant toutes les invites de commandes Visual Studio installées s’affiche.

1. Choisissez **invite de commandes développeur pour VS 2019** (ou l’invite de commandes que vous souhaitez utiliser).

### <a name="windows-7"></a>Windows 7

1. Choisissez **Démarrer** , puis développez **tous les programmes**.

1. Sélectionnez **Visual Studio 2019** > **Visual Studio Tools** > **invite de commandes développeur pour vs 2019**, ou l’invite de commandes que vous souhaitez utiliser.

   ![Menu Démarrer de Windows 7 avec l’invite de commandes en surbrillance](./media/developer-command-prompt-for-vs/windows7-menu.png)

Si vous avez installé d’autres kits de [développement logiciel (SDK) Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versions antérieures](https://developer.microsoft.com/windows/downloads/sdk-archive), vous pouvez voir des invites de commandes supplémentaires. Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.

## <a name="manually-locate-the-files-on-your-machine"></a>Recherche manuelle des fichiers sur votre ordinateur

En règle générale, les raccourcis des invites de commandes que vous avez installées sont placés dans le dossier du **menu Démarrer** de Visual Studio, par exemple dans *%ProgramData%\Microsoft\Windows\Start c:\ProgramData\Microsoft\Windows\Menu Studio 2019 \ Visual Studio Tools*. Toutefois, si, pour une raison quelconque, la recherche de l’invite de commandes ne produit pas les résultats attendus, vous pouvez tenter de localiser manuellement le raccourci sur votre ordinateur. Essayez de rechercher le nom du fichier d’invite de commandes, par exemple *VsDevCmd. bat*, ou accédez au dossier Tools, tel que *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (le chemin d’accès change en fonction de la version, de l’édition et de l’emplacement de l’installation de Visual Studio).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Démarrer l’invite de commandes à partir de Visual Studio

Pour faciliter l’accès, vous pouvez ajouter Invite de commandes développeur, ou toute autre invite de commandes, au menu outils de Visual Studio. Pour cela, il vous suffit de l’ajouter à la liste des outils externes. Procédez comme suit :

1. Ouvrez Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Continuer sans code**.

1. Dans la barre de menus, choisissez **outils** > **outils externes**.

1. Dans la boîte de dialogue **Outils externes**, choisissez le bouton **Ajouter**. Une nouvelle entrée apparaît.

1. Entrez un **titre** pour votre nouvel élément de menu, par exemple `Command Prompt`.

1. Dans le champ **Commande**, spécifiez le fichier à lancer, par exemple `%comspec%` ou `C:\Windows\System32\cmd.exe`.

1. Dans le champ **arguments** , indiquez où trouver l’invite de commandes spécifique que vous souhaitez utiliser, par exemple `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`. Cette commande lance le Invite de commandes développeur installé avec la Communauté Visual Studio 2019. Changez cette valeur en fonction de l’emplacement d’installation, de l’édition et de la version de Visual Studio.

1. Dans le champ **répertoire initial** , spécifiez le répertoire dans lequel l’invite de commandes démarrera. Choisissez une valeur telle que **répertoire du projet** en sélectionnant la flèche en regard du champ.

1. Sélectionnez le bouton **OK** .

   ![Boîte de dialogue outils externes avec les valeurs de champ renseignées.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Le nouvel élément de menu est ajouté et vous pouvez accéder à l’invite de commandes à partir du menu outils.

   ![Élément de menu d’invite de commandes dans Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Voir aussi

- [Outils de .NET Framework](index.md)
- [Gestion des outils externes](/visualstudio/ide/managing-external-tools)
- [Utiliser l’ensemble C++ d’outils Microsoft à partir de la ligne de commande](/cpp/build/building-on-the-command-line)
