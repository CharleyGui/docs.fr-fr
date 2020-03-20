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
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="3d64b-102">Invite de commandes développeur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3d64b-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="3d64b-103">Developer Command Prompt for Visual Studio vous permet d’utiliser plus facilement les outils cadres .NET.</span><span class="sxs-lookup"><span data-stu-id="3d64b-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="3d64b-104">Il s’agit d’une invite de commande qui définit automatiquement des variables spécifiques de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="3d64b-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="3d64b-105">Après l’ouverture de Developer Command Prompt, vous pouvez `ildasm` entrer `clrver`les commandes pour des outils [cadre .NET](index.md) tels que ou .</span><span class="sxs-lookup"><span data-stu-id="3d64b-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3d64b-106">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="3d64b-106">Prerequisites</span></span>

- [<span data-ttu-id="3d64b-107">Studio visuel 2019</span><span class="sxs-lookup"><span data-stu-id="3d64b-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="3d64b-108">Rechercher l’invite de commandes sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="3d64b-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="3d64b-109">Vous pouvez avoir plusieurs invites de commande, selon la version de Visual Studio et les SDK supplémentaires et les charges de travail que vous avez installées.</span><span class="sxs-lookup"><span data-stu-id="3d64b-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="3d64b-110">Si les étapes suivantes ne fonctionnent pas, vous pouvez essayer de [localiser manuellement les fichiers sur votre machine](#manually-locate-the-files-on-your-machine) ou démarrer [l’invite de commande de l’intérieur de Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3d64b-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="3d64b-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3d64b-111">Windows 10</span></span>

1. <span data-ttu-id="3d64b-112">Sélectionnez La clé de logo **Start** ![Windows sur le clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="3d64b-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="3d64b-113">et faites défiler la lettre **V**.</span><span class="sxs-lookup"><span data-stu-id="3d64b-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="3d64b-114">Élargissez le dossier **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="3d64b-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="3d64b-115">Choisissez **Developer Command Prompt pour VS 2019** (ou l’invite de commande que vous souhaitez utiliser).</span><span class="sxs-lookup"><span data-stu-id="3d64b-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="3d64b-116">Alternativement, vous pouvez commencer à taper le nom de l’invite de commande dans la boîte de recherche sur la barre des tâches, et choisir le résultat que vous voulez que la liste de résultat commence à afficher les correspondances de recherche.</span><span class="sxs-lookup"><span data-stu-id="3d64b-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Gif animé montrant le comportement de recherche sur Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="3d64b-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3d64b-118">Windows 8.1</span></span>

1. <span data-ttu-id="3d64b-119">Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows de votre clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="3d64b-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="3d64b-120">de votre clavier, par exemple.</span><span class="sxs-lookup"><span data-stu-id="3d64b-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="3d64b-121">Sur l’écran **Démarrer,** appuyez sur **Ctrl**+**Tab** pour ouvrir la liste **Apps,** puis appuyez sur **V**. Cela fait ressortir une liste qui comprend toutes les invites de commande Visual Studio installées.</span><span class="sxs-lookup"><span data-stu-id="3d64b-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="3d64b-122">Choisissez **Developer Command Prompt pour VS 2019** (ou l’invite de commande que vous souhaitez utiliser).</span><span class="sxs-lookup"><span data-stu-id="3d64b-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="3d64b-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="3d64b-123">Windows 7</span></span>

1. <span data-ttu-id="3d64b-124">Choisissez **Démarrer,** puis d’élargir **tous les programmes**.</span><span class="sxs-lookup"><span data-stu-id="3d64b-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="3d64b-125">Choisissez **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt pour VS 2019**, ou l’invite de commande que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="3d64b-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Windows 7 Démarrer avec l’invite de commande surlignée](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="3d64b-127">Si vous avez d’autres SDK installés, tels que windows [10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [des versions précédentes,](https://developer.microsoft.com/windows/downloads/sdk-archive)vous pouvez voir des invites de commande supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="3d64b-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="3d64b-128">Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.</span><span class="sxs-lookup"><span data-stu-id="3d64b-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="3d64b-129">Recherche manuelle des fichiers sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="3d64b-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="3d64b-130">Habituellement, les raccourcis pour les invites de commande que vous avez installé sont placés dans le dossier **de menu Démarrer** pour Visual Studio, comme dans % *ProgramData%-Microsoft-Windows-Start Menu-Programs-Visual Studio 2019 -Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="3d64b-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="3d64b-131">Mais si, pour une raison quelconque, la recherche de l’invite de commande ne produit pas les résultats attendus, vous pouvez essayer de localiser manuellement le raccourci sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="3d64b-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="3d64b-132">Essayez de rechercher le nom du fichier d’invite de commande, tel que *VsDevCmd.bat*, ou allez au dossier Tools, tels que *%ProgramFiles (x86)% -Microsoft Visual Studio-2019-Community-Common7-Tools* (changements de chemin selon votre version Visual Studio, édition et emplacement d’installation).</span><span class="sxs-lookup"><span data-stu-id="3d64b-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="3d64b-133">Démarrer l’invite de commande de l’intérieur Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3d64b-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="3d64b-134">Pour un accès plus facile, vous pouvez ajouter Developer Command Prompt, ou toute autre invite de commande, au menu Tools dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d64b-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="3d64b-135">Pour cela, il vous suffit de l’ajouter à la liste des outils externes.</span><span class="sxs-lookup"><span data-stu-id="3d64b-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="3d64b-136">Voici la procédure à suivre :</span><span class="sxs-lookup"><span data-stu-id="3d64b-136">Here are the steps:</span></span>

1. <span data-ttu-id="3d64b-137">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d64b-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="3d64b-138">Dans la fenêtre de démarrage, choisissez **Continuer sans code**.</span><span class="sxs-lookup"><span data-stu-id="3d64b-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="3d64b-139">Sur la barre de menu, choisissez **Tools** > **External Tools**.</span><span class="sxs-lookup"><span data-stu-id="3d64b-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="3d64b-140">Dans la boîte de dialogue **Outils externes**, choisissez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="3d64b-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="3d64b-141">Une nouvelle entrée apparaît.</span><span class="sxs-lookup"><span data-stu-id="3d64b-141">A new entry appears.</span></span>

1. <span data-ttu-id="3d64b-142">Entrez un **titre** pour votre nouvel élément de menu, par exemple `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="3d64b-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="3d64b-143">Dans le champ **de commande,** spécifiez le fichier que vous souhaitez lancer, tel que `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="3d64b-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="3d64b-144">Dans le domaine **Arguments,** spécifiez où trouver `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`l’invite de commande spécifique que vous souhaitez utiliser, comme .</span><span class="sxs-lookup"><span data-stu-id="3d64b-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="3d64b-145">Cette commande lance le Developer Command Prompt qui est installé avec Visual Studio 2019 Community.</span><span class="sxs-lookup"><span data-stu-id="3d64b-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="3d64b-146">Changez cette valeur en fonction de l’emplacement d’installation, de l’édition et de la version de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d64b-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="3d64b-147">Dans le domaine **de l’annuaire initial,** spécifiez l’annuaire dans lequel l’invite de commande commencera.</span><span class="sxs-lookup"><span data-stu-id="3d64b-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="3d64b-148">Choisissez une valeur telle que **l’annuaire de projet** en sélectionnant la flèche à côté du champ.</span><span class="sxs-lookup"><span data-stu-id="3d64b-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="3d64b-149">Choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="3d64b-149">Choose the **OK** button.</span></span>

   ![Dialogue outils externes avec les valeurs de champ remplies.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="3d64b-151">Le nouvel élément de menu est ajouté et vous pouvez accéder à l’invite de commandes à partir du menu Outils.</span><span class="sxs-lookup"><span data-stu-id="3d64b-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Élément de menu d’invite de commandes dans Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="3d64b-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d64b-153">See also</span></span>

- [<span data-ttu-id="3d64b-154">Outils du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3d64b-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="3d64b-155">Gestion des outils externes</span><span class="sxs-lookup"><span data-stu-id="3d64b-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="3d64b-156">Utilisez l’outil Microsoft CMD de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="3d64b-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
