---
title: Invite de commandes développeur pour Visual Studio
description: Apprenez à utiliser le Invite de commandes développeur pour Visual Studio, qui vous permet d’utiliser plus facilement les outils .NET. Il définit automatiquement des variables d’environnement spécifiques.
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
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167168"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="2116e-104">Invite de commandes développeur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2116e-104">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="2116e-105">Invite de commandes développeur pour Visual Studio vous permet d’utiliser plus facilement les outils .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2116e-105">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="2116e-106">Il s’agit d’une invite de commandes qui définit automatiquement des variables d’environnement spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2116e-106">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="2116e-107">Après avoir ouvert Invite de commandes développeur, vous pouvez entrer les commandes pour [.NET Framework des outils](index.md) tels que `ildasm` ou `clrver` .</span><span class="sxs-lookup"><span data-stu-id="2116e-107">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2116e-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="2116e-108">Prerequisites</span></span>

- [<span data-ttu-id="2116e-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="2116e-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="2116e-110">Rechercher l’invite de commandes sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="2116e-110">Search for the command prompt on your machine</span></span>

<span data-ttu-id="2116e-111">Vous pouvez avoir plusieurs invites de commande, en fonction de la version de Visual Studio et de tous les kits de développement logiciel (SDK) et charges de travail supplémentaires que vous avez installés.</span><span class="sxs-lookup"><span data-stu-id="2116e-111">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="2116e-112">Si les étapes suivantes ne fonctionnent pas, vous pouvez essayer de [localiser manuellement les fichiers sur votre ordinateur](#manually-locate-the-files-on-your-machine) ou [de démarrer l’invite de commandes à partir de Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2116e-112">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="2116e-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="2116e-113">Windows 10</span></span>

1. <span data-ttu-id="2116e-114">Sélectionnez **Démarrer** ![ la touche de logo Windows sur le clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="2116e-114">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="2116e-115">et faites défiler jusqu’à la lettre **V**.</span><span class="sxs-lookup"><span data-stu-id="2116e-115">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="2116e-116">Développez le dossier **Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="2116e-116">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="2116e-117">Choisissez **invite de commandes développeur pour VS 2019** (ou l’invite de commandes que vous souhaitez utiliser).</span><span class="sxs-lookup"><span data-stu-id="2116e-117">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="2116e-118">Vous pouvez également commencer à taper le nom de l’invite de commandes dans la zone de recherche de la barre des tâches, puis choisir le résultat à partir duquel la liste des résultats commence à afficher les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="2116e-118">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Image GIF animée montrant le comportement de recherche sur Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="2116e-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="2116e-120">Windows 8.1</span></span>

1. <span data-ttu-id="2116e-121">Accédez à l’écran **Démarrer** en appuyant sur la touche de logo Windows ![Touche de logo Windows de votre clavier.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="2116e-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="2116e-122">de votre clavier, par exemple.</span><span class="sxs-lookup"><span data-stu-id="2116e-122">on your keyboard for example.</span></span>

1. <span data-ttu-id="2116e-123">Dans l’écran d' **Accueil** , appuyez sur **CTRL** + **Tab** pour ouvrir la liste des **applications** , puis appuyez sur la touche **V**. Une liste incluant toutes les invites de commandes Visual Studio installées s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2116e-123">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="2116e-124">Choisissez **invite de commandes développeur pour VS 2019** (ou l’invite de commandes que vous souhaitez utiliser).</span><span class="sxs-lookup"><span data-stu-id="2116e-124">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="2116e-125">Windows 7</span><span class="sxs-lookup"><span data-stu-id="2116e-125">Windows 7</span></span>

1. <span data-ttu-id="2116e-126">Choisissez **Démarrer** , puis développez **tous les programmes**.</span><span class="sxs-lookup"><span data-stu-id="2116e-126">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="2116e-127">Sélectionnez **Visual Studio 2019**  >  **Visual Studio Tools**  >  **invite de commandes développeur pour vs 2019**, ou l’invite de commandes que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="2116e-127">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Démarrer de Windows 7 avec l’invite de commandes en surbrillance](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="2116e-129">Si vous avez installé d’autres kits de [développement logiciel (SDK) Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versions antérieures](https://developer.microsoft.com/windows/downloads/sdk-archive), vous pouvez voir des invites de commandes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2116e-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="2116e-130">Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.</span><span class="sxs-lookup"><span data-stu-id="2116e-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="2116e-131">Recherche manuelle des fichiers sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="2116e-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="2116e-132">En règle générale, les raccourcis des invites de commandes que vous avez installées sont placés dans le dossier du **menu Démarrer** de Visual Studio, par exemple dans *%ProgramData%\Microsoft\Windows\Start c:\ProgramData\Microsoft\Windows\Menu Studio 2019 \ Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="2116e-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="2116e-133">Toutefois, si, pour une raison quelconque, la recherche de l’invite de commandes ne produit pas les résultats attendus, vous pouvez tenter de localiser manuellement le raccourci sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2116e-133">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="2116e-134">Essayez de rechercher le nom du fichier d’invite de commandes, par exemple *VsDevCmd.bat*, ou accédez au dossier Tools, tel que *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (changement de chemin d’accès en fonction de la version, de l’édition et de l’emplacement d’installation de Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="2116e-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="2116e-135">Démarrer l’invite de commandes à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2116e-135">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="2116e-136">Pour faciliter l’accès, vous pouvez ajouter Invite de commandes développeur, ou toute autre invite de commandes, au menu outils de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2116e-136">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="2116e-137">Pour cela, il vous suffit de l’ajouter à la liste des outils externes.</span><span class="sxs-lookup"><span data-stu-id="2116e-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="2116e-138">Voici la procédure à suivre :</span><span class="sxs-lookup"><span data-stu-id="2116e-138">Here are the steps:</span></span>

1. <span data-ttu-id="2116e-139">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2116e-139">Open Visual Studio.</span></span>

1. <span data-ttu-id="2116e-140">Dans la fenêtre de démarrage, choisissez **Continuer sans code**.</span><span class="sxs-lookup"><span data-stu-id="2116e-140">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="2116e-141">Dans la barre de menus, choisissez **Outils**outils  >  **externes**.</span><span class="sxs-lookup"><span data-stu-id="2116e-141">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="2116e-142">Dans la boîte de dialogue **Outils externes**, choisissez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2116e-142">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="2116e-143">Une nouvelle entrée apparaît.</span><span class="sxs-lookup"><span data-stu-id="2116e-143">A new entry appears.</span></span>

1. <span data-ttu-id="2116e-144">Entrez un **titre** pour votre nouvel élément de menu, par exemple `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="2116e-144">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="2116e-145">Dans le champ **commande** , spécifiez le fichier que vous souhaitez lancer, tel que `%comspec%` ou `C:\Windows\System32\cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="2116e-145">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="2116e-146">Dans le champ **arguments** , indiquez où trouver l’invite de commandes spécifique que vous souhaitez utiliser, par exemple `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"` .</span><span class="sxs-lookup"><span data-stu-id="2116e-146">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="2116e-147">Cette commande lance le Invite de commandes développeur installé avec la Communauté Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2116e-147">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="2116e-148">Changez cette valeur en fonction de l’emplacement d’installation, de l’édition et de la version de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2116e-148">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="2116e-149">Dans le champ **répertoire initial** , spécifiez le répertoire dans lequel l’invite de commandes démarrera.</span><span class="sxs-lookup"><span data-stu-id="2116e-149">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="2116e-150">Choisissez une valeur telle que **répertoire du projet** en sélectionnant la flèche en regard du champ.</span><span class="sxs-lookup"><span data-stu-id="2116e-150">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="2116e-151">Choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="2116e-151">Choose the **OK** button.</span></span>

   ![Boîte de dialogue outils externes avec les valeurs de champ renseignées.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="2116e-153">Le nouvel élément de menu est ajouté et vous pouvez accéder à l’invite de commandes à partir du menu Outils.</span><span class="sxs-lookup"><span data-stu-id="2116e-153">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Élément de menu d’invite de commandes dans Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="2116e-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2116e-155">See also</span></span>

- [<span data-ttu-id="2116e-156">Outils du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2116e-156">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="2116e-157">Gestion des outils externes</span><span class="sxs-lookup"><span data-stu-id="2116e-157">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="2116e-158">Utiliser l’ensemble d’outils Microsoft C++ à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2116e-158">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
