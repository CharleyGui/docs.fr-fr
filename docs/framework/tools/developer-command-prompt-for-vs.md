---
title: Invite de commandes développeur pour Visual Studio
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79cfc607e20d921c7ae942cb9755eee4264336eb
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877056"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Invite de commandes développeur pour Visual Studio

L’invite de commandes développeur pour Visual Studio vous permet d’utiliser plus facilement les outils .NET Framework. Il s’agit d’une invite de commandes qui définit automatiquement les variables d’environnement spécifiques.

> [!div class="button"]
> [Télécharger Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Rechercher l’invite de commandes sur votre ordinateur

Vous pouvez avoir plusieurs invites de commandes, en fonction de la version de Visual Studio et des SDK que vous avez installés. Par exemple, les versions 64 bits de Visual Studio fournissent à la fois des invites de commandes 32 bits et 64 bits. (Les versions 32 bits et 64 bits de la plupart des outils sont identiques ; toutefois, certains outils apportent des modifications propres aux environnements 32 bits et 64 bits.) Si les étapes suivantes ne fonctionnent pas, vous pouvez essayer de [rechercher manuellement les fichiers sur votre ordinateur](#manually-locate-the-files-on-your-machine) ou de [lancer l’invite de commandes à partir de Visual Studio](#run-the-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>Dans Windows 10

1. Dans la zone de recherche dans la barre des tâches, commencez à taper le nom de l’outil, tel que `dev` ou `developer command prompt`. S’affiche alors une liste des applications installées qui correspondent à votre modèle de recherche. Si vous recherchez une autre invite de commandes, essayez d’entrer un autre terme de recherche, par exemple `prompt`.

2. Choisissez **Invite de commandes développeur pour Visual Studio** (ou l’invite de commandes que vous voulez utiliser).

### <a name="in-windows-81"></a>Dans Windows 8.1

1. Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows de votre clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) de votre clavier, par exemple.

2. Dans l’écran **Démarrer**, appuyez sur **Ctrl**+**Tab** pour ouvrir la liste **Applications**, puis entrez `V`. Cela entraîne l’affichage d’une liste qui inclut toutes les invites de commandes Visual Studio installées.

3. Choisissez **Invite de commandes développeur** (ou l’invite de commandes que vous voulez utiliser).

### <a name="in-windows-8"></a>Dans Windows 8

1. Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows du clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) de votre clavier, par exemple.

2. Sur l’écran **Démarrer**, appuyez sur la touche de logo Windows ![Touche de logo Windows du clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) `+ Z`.

3. Choisissez l’icône **Vue Applications** en bas de l’écran, puis entrez `V`. Cela entraîne l’affichage d’une liste qui inclut toutes les invites de commandes Visual Studio installées.

4. Choisissez **Invite de commandes développeur** (ou l’invite de commandes que vous voulez utiliser).

### <a name="in-windows-7"></a>Dans Windows 7

1. Sélectionnez **Démarrer**, développez **Tous les programmes**, puis développez **Microsoft Visual Studio**.

2. En fonction de la version de Visual Studio que vous avez installée, choisissez **Visual Studio Tools**, **Invite de commandes Visual Studio** ou l’invite de commandes que vous voulez utiliser.

Si vous avez installé d’autres SDK, tels que le [SDK Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk), ou des [versions antérieures](https://developer.microsoft.com/windows/downloads/sdk-archive), vous pouvez voir des invites de commandes supplémentaires pour les architectures ARM, x86 ou x64. Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.

## <a name="manually-locate-the-files-on-your-machine"></a>Recherche manuelle des fichiers sur votre ordinateur

En règle générale, les raccourcis des invites de commandes que vous avez installées sont placés dans le dossier **Menu Démarrer** de Visual Studio, par exemple dans C:\ProgramData\Microsoft\Windows\Menu Démarrer\Programmes\Visual Studio 2017\Visual Studio Tools. Mais si pour une raison quelconque la recherche de l’invite de commandes ne donne pas les résultats attendus, vous pouvez tenter de localiser manuellement le raccourci sur votre machine. Essayez de rechercher le nom du fichier d’invite de commandes, par exemple *VsDevCmd.bat*, ou accédez au dossier Tools à l’emplacement C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (le chemin varie en fonction de l’emplacement d’installation, de l’édition et de la version de Visual Studio).

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Exécuter l’invite de commandes à partir de Visual Studio

Pour faciliter l’accès, vous pouvez ajouter l’invite de commandes développeur Visual Studio ou toute autre invite de commandes au menu **Outils** de Visual Studio. Pour cela, il vous suffit de l’ajouter à la liste des outils externes. Procédez comme suit :

1. Ouvrez Visual Studio.

2. Sélectionnez le menu **Outils**, puis choisissez **Outils externes**.

3. Dans la boîte de dialogue **Outils externes**, choisissez le bouton **Ajouter**. Une nouvelle entrée apparaît.

4. Entrez un **titre** pour votre nouvel élément de menu, par exemple `Command Prompt`.

5. Dans le champ **Commande**, spécifiez le fichier à lancer, par exemple `%comspec%` ou `C:\Windows\System32\cmd.exe`.

6. Dans le champ **Arguments**, indiquez où trouver l’invite de commandes à utiliser en particulier, par exemple `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (cette commande lance l’invite de commandes développeur installée avec Visual Studio 2017 Enterprise). Changez cette valeur en fonction de l’emplacement d’installation, de l’édition et de la version de Visual Studio.

7. Choisissez une valeur pour le champ **Répertoire Initial**, par exemple **Répertoire du projet**.

8. Sélectionnez le bouton **OK** .

   Le nouvel élément de menu est ajouté et vous pouvez accéder à l’invite de commandes à partir du menu **Outils**.

   ![Élément de menu d’invite de commandes dans Visual Studio](media/command-prompt-vs-menu.png)

## <a name="see-also"></a>Voir aussi

- [Outils](../../../docs/framework/tools/index.md)
- [Gestion des outils externes](/visualstudio/ide/managing-external-tools)
