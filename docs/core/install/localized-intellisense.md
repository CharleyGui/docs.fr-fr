---
title: Installer des fichiers IntelliSense traduits
description: Découvrez comment configurer votre ordinateur de développement pour utiliser des fichiers IntelliSense traduits pour les projets .NET Core dans Visual Studio.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443476"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="2ab48-103">Guide pratique pour installer des fichiers IntelliSense traduits pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ab48-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="2ab48-104">[IntelliSense](/visualstudio/ide/using-intellisense) est une aide à la complétion de code qui est disponible dans différents environnements de développement intégrés (IDE) comme Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ab48-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="2ab48-105">Par défaut, lorsque vous développez des projets .NET Core, le kit SDK comprend uniquement la version anglaise des fichiers IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2ab48-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="2ab48-106">Cet article explique :</span><span class="sxs-lookup"><span data-stu-id="2ab48-106">This article explains:</span></span>

- <span data-ttu-id="2ab48-107">Comment installer la version traduite de ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="2ab48-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="2ab48-108">Comment modifier l’installation de Visual Studio pour utiliser une autre langue.</span><span class="sxs-lookup"><span data-stu-id="2ab48-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ab48-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="2ab48-109">Prerequisites</span></span>

- <span data-ttu-id="2ab48-110">[Kit SDK .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2ab48-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="2ab48-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2ab48-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="2ab48-112">Télécharger et installer les fichiers IntelliSense traduits</span><span class="sxs-lookup"><span data-stu-id="2ab48-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ab48-113">Cette procédure vous demande d’avoir l’autorisation Administrateur pour copier les fichiers IntelliSense dans le dossier d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ab48-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="2ab48-114">Accédez à la page de [Téléchargement des fichiers IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense).</span><span class="sxs-lookup"><span data-stu-id="2ab48-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="2ab48-115">Téléchargez le fichier IntelliSense correspondant à la langue et à la version que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="2ab48-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="2ab48-116">Extrayez le contenu du fichier .zip.</span><span class="sxs-lookup"><span data-stu-id="2ab48-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="2ab48-117">Accédez au dossier d’installation .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ab48-117">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="2ab48-118">Par défaut, il se trouve sous *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="2ab48-118">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>

   - <span data-ttu-id="2ab48-119">Choisissez le kit SDK pour lequel vous souhaitez installer IntelliSense et accédez au chemin associé.</span><span class="sxs-lookup"><span data-stu-id="2ab48-119">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="2ab48-120">Les options suivantes sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="2ab48-120">You have the following options:</span></span>

      | <span data-ttu-id="2ab48-121">Type de kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="2ab48-121">SDK type</span></span>        | <span data-ttu-id="2ab48-122">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="2ab48-122">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="2ab48-123">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2ab48-123">.NET Core</span></span>       | <span data-ttu-id="2ab48-124">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="2ab48-124">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="2ab48-125">Bureau Windows</span><span class="sxs-lookup"><span data-stu-id="2ab48-125">Windows Desktop</span></span> | <span data-ttu-id="2ab48-126">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="2ab48-126">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="2ab48-127">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2ab48-127">.NET Standard</span></span>   | <span data-ttu-id="2ab48-128">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="2ab48-128">*NETStandard.Library.Ref*</span></span>          |
   
   - <span data-ttu-id="2ab48-129">Accédez à la version pour laquelle vous souhaitez installer les fichiers IntelliSense traduits.</span><span class="sxs-lookup"><span data-stu-id="2ab48-129">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="2ab48-130">Par exemple, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="2ab48-130">For example, *3.1.0*.</span></span>
   - <span data-ttu-id="2ab48-131">Ouvrez le dossier *ref*.</span><span class="sxs-lookup"><span data-stu-id="2ab48-131">Open the *ref* folder.</span></span>
   - <span data-ttu-id="2ab48-132">Ouvrez le dossier du moniker.</span><span class="sxs-lookup"><span data-stu-id="2ab48-132">Open the moniker folder.</span></span> <span data-ttu-id="2ab48-133">Par exemple, *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="2ab48-133">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="2ab48-134">Donc, le chemin complet auquel vous voulez accéder devrait ressembler à *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="2ab48-134">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="2ab48-135">Créez un sous-dossier dans le dossier du moniker que vous venez d’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="2ab48-135">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="2ab48-136">Le nom du dossier indique la langue que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="2ab48-136">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="2ab48-137">Le tableau suivant spécifie les différentes options :</span><span class="sxs-lookup"><span data-stu-id="2ab48-137">The following table specifies the different options:</span></span>

   | <span data-ttu-id="2ab48-138">Langue</span><span class="sxs-lookup"><span data-stu-id="2ab48-138">Language</span></span>              | <span data-ttu-id="2ab48-139">Nom de dossier</span><span class="sxs-lookup"><span data-stu-id="2ab48-139">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="2ab48-140">Portugais brésilien</span><span class="sxs-lookup"><span data-stu-id="2ab48-140">Brazilian Portuguese</span></span>  | <span data-ttu-id="2ab48-141">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="2ab48-141">*pt-br*</span></span>     |
   | <span data-ttu-id="2ab48-142">Chinois (simplifié)</span><span class="sxs-lookup"><span data-stu-id="2ab48-142">Chinese (simplified)</span></span>  | <span data-ttu-id="2ab48-143">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="2ab48-143">*zh-hans*</span></span>   |
   | <span data-ttu-id="2ab48-144">Chinois (traditionnel)</span><span class="sxs-lookup"><span data-stu-id="2ab48-144">Chinese (traditional)</span></span> | <span data-ttu-id="2ab48-145">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="2ab48-145">*zh-hant*</span></span>   |
   | <span data-ttu-id="2ab48-146">Français</span><span class="sxs-lookup"><span data-stu-id="2ab48-146">French</span></span>                | <span data-ttu-id="2ab48-147">*fr*</span><span class="sxs-lookup"><span data-stu-id="2ab48-147">*fr*</span></span>        |
   | <span data-ttu-id="2ab48-148">Allemand</span><span class="sxs-lookup"><span data-stu-id="2ab48-148">German</span></span>                | <span data-ttu-id="2ab48-149">*de*</span><span class="sxs-lookup"><span data-stu-id="2ab48-149">*de*</span></span>        |
   | <span data-ttu-id="2ab48-150">Italien</span><span class="sxs-lookup"><span data-stu-id="2ab48-150">Italian</span></span>               | <span data-ttu-id="2ab48-151">*it*</span><span class="sxs-lookup"><span data-stu-id="2ab48-151">*it*</span></span>        |
   | <span data-ttu-id="2ab48-152">Japonais</span><span class="sxs-lookup"><span data-stu-id="2ab48-152">Japanese</span></span>              | <span data-ttu-id="2ab48-153">*ja*</span><span class="sxs-lookup"><span data-stu-id="2ab48-153">*ja*</span></span>        |
   | <span data-ttu-id="2ab48-154">Coréen</span><span class="sxs-lookup"><span data-stu-id="2ab48-154">Korean</span></span>                | <span data-ttu-id="2ab48-155">*ko*</span><span class="sxs-lookup"><span data-stu-id="2ab48-155">*ko*</span></span>        |
   | <span data-ttu-id="2ab48-156">Russe</span><span class="sxs-lookup"><span data-stu-id="2ab48-156">Russian</span></span>               | <span data-ttu-id="2ab48-157">*ru*</span><span class="sxs-lookup"><span data-stu-id="2ab48-157">*ru*</span></span>        |
   | <span data-ttu-id="2ab48-158">Espagnol</span><span class="sxs-lookup"><span data-stu-id="2ab48-158">Spanish</span></span>               | <span data-ttu-id="2ab48-159">*es*</span><span class="sxs-lookup"><span data-stu-id="2ab48-159">*es*</span></span>        |

1. <span data-ttu-id="2ab48-160">Copiez les fichiers *.xml* que vous avez extraits à l’étape 3 dans ce nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="2ab48-160">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="2ab48-161">Étant donné que les fichiers *.xml* sont répartis dans les dossiers de SDK, copiez-les dans le kit SDK correspondant que vous avez choisi à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="2ab48-161">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="2ab48-162">Modifier la langue de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ab48-162">Modify Visual Studio language</span></span>

<span data-ttu-id="2ab48-163">Pour que Visual Studio utilise une autre langue pour IntelliSense, installez le module linguistique approprié.</span><span class="sxs-lookup"><span data-stu-id="2ab48-163">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="2ab48-164">Vous pouvez effectuer cette opération [pendant l’installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou plus tard en modifiant l’installation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ab48-164">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="2ab48-165">Si vous avez déjà configuré Visual Studio dans la langue de votre choix, votre installation IntelliSense est prête.</span><span class="sxs-lookup"><span data-stu-id="2ab48-165">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="2ab48-166">Installer le module linguistique</span><span class="sxs-lookup"><span data-stu-id="2ab48-166">Install the language pack</span></span>

<span data-ttu-id="2ab48-167">Si vous n’avez pas installé le module linguistique souhaité au cours de l’installation, mettez à jour Visual Studio comme suit pour installer le module linguistique :</span><span class="sxs-lookup"><span data-stu-id="2ab48-167">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ab48-168">Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui dispose d’autorisations Administrateur.</span><span class="sxs-lookup"><span data-stu-id="2ab48-168">To install, update, or modify Visual Studio, you must log on with an account that has administrative permissions.</span></span> <span data-ttu-id="2ab48-169">Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2ab48-169">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="2ab48-170">Recherchez le programme d’installation de Visual Studio sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ab48-170">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="2ab48-171">Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-171">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Ouvrir Visual Studio Installer à partir de Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="2ab48-173">Vous trouverez également Visual Studio Installer à l’emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="2ab48-173">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="2ab48-174">Vous devrez peut-être mettre à jour le programme d’installation avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2ab48-174">You might have to update the installer before continuing.</span></span> <span data-ttu-id="2ab48-175">Dans ce cas, suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="2ab48-175">If so, follow the prompts.</span></span>

1. <span data-ttu-id="2ab48-176">Dans le programme d’installation, recherchez l’édition de Visual Studio dans laquelle vous voulez ajouter le module linguistique, puis choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-176">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Mettre à jour ou modifier Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="2ab48-178">Si vous ne voyez pas de bouton **Modifier** mais que vous voyez un bouton **Mettre à jour** à la place, vous devez mettre à jour Visual Studio avant de pouvoir modifier votre installation.</span><span class="sxs-lookup"><span data-stu-id="2ab48-178">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="2ab48-179">Une fois la mise à jour terminée, le bouton **Modifier** doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="2ab48-179">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="2ab48-180">Sous l’onglet **Modules linguistiques**, sélectionnez ou désélectionnez les langues à installer ou désinstaller.</span><span class="sxs-lookup"><span data-stu-id="2ab48-180">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Onglet Modules linguistiques de Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="2ab48-182">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-182">Choose **Modify**.</span></span> <span data-ttu-id="2ab48-183">La mise à jour démarre.</span><span class="sxs-lookup"><span data-stu-id="2ab48-183">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="2ab48-184">Modifier les paramètres de langue dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ab48-184">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="2ab48-185">Une fois que vous avez installé les modules linguistiques souhaités, modifiez les paramètres de Visual Studio pour utiliser une autre langue :</span><span class="sxs-lookup"><span data-stu-id="2ab48-185">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="2ab48-186">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ab48-186">Open Visual Studio.</span></span>

1. <span data-ttu-id="2ab48-187">Dans la fenêtre de démarrage, choisissez **Continuer sans code**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-187">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="2ab48-188">Dans le menu principal, sélectionnez **Outils** > **Options**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-188">On the main menu, select **Tools** > **Options**.</span></span> <span data-ttu-id="2ab48-189">La boîte de dialogue Options s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="2ab48-189">The Options dialog opens.</span></span>

1. <span data-ttu-id="2ab48-190">Sous le dossier **Environnement**, choisissez **Paramètres internationaux**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-190">Under the **Environment** folder, choose **International Settings**.</span></span>

1. <span data-ttu-id="2ab48-191">Dans la liste déroulante **Langue**, sélectionnez la langue souhaitée.</span><span class="sxs-lookup"><span data-stu-id="2ab48-191">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="2ab48-192">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-192">Choose **OK**.</span></span> 

1. <span data-ttu-id="2ab48-193">Une boîte de dialogue vous informe que vous devez redémarrer Visual Studio pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="2ab48-193">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="2ab48-194">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2ab48-194">Choose **OK**.</span></span>

1. <span data-ttu-id="2ab48-195">Redémarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ab48-195">Restart Visual Studio.</span></span>

<span data-ttu-id="2ab48-196">Après le redémarrage, IntelliSense doit fonctionner comme prévu quand vous ouvrez un projet .NET Core qui cible la version des fichiers IntelliSense que vous venez d’installer.</span><span class="sxs-lookup"><span data-stu-id="2ab48-196">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ab48-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ab48-197">See also</span></span>

- [<span data-ttu-id="2ab48-198">IntelliSense dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ab48-198">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
