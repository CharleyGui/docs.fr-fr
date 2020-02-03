---
title: Installer des fichiers IntelliSense localisés
description: Découvrez comment configurer votre ordinateur de développement pour utiliser des fichiers IntelliSense localisés pour les projets .NET Core dans Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: 58b462507edf953a6c28aadbb9e3239a5cbe05b2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733649"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="6ab1f-103">Comment installer des fichiers IntelliSense localisés pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ab1f-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="6ab1f-104">[IntelliSense](/visualstudio/ide/using-intellisense) est une aide à la saisie semi-automatique de code qui est disponible dans différents environnements de développement intégré (IDE), tels que Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="6ab1f-105">Par défaut, lorsque vous développez des projets .NET Core, le kit de développement logiciel (SDK) comprend uniquement la version anglaise des fichiers IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="6ab1f-106">Cet article explique les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6ab1f-106">This article explains:</span></span>

- <span data-ttu-id="6ab1f-107">Comment installer la version localisée de ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="6ab1f-108">Comment modifier l’installation de Visual Studio pour utiliser une autre langue.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ab1f-109">Composants requis</span><span class="sxs-lookup"><span data-stu-id="6ab1f-109">Prerequisites</span></span>

- <span data-ttu-id="6ab1f-110">[Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="6ab1f-111">[Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="6ab1f-112">Télécharger et installer les fichiers IntelliSense localisés</span><span class="sxs-lookup"><span data-stu-id="6ab1f-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ab1f-113">Cette procédure nécessite que vous disposiez de l’autorisation d’administrateur pour copier les fichiers IntelliSense dans le dossier d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="6ab1f-114">Accédez à la page [Télécharger les fichiers IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .</span><span class="sxs-lookup"><span data-stu-id="6ab1f-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="6ab1f-115">Téléchargez le fichier IntelliSense correspondant à la langue et à la version que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="6ab1f-116">Extrayez le contenu du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="6ab1f-117">Accédez au dossier IntelliSense .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="6ab1f-118">Accédez au dossier d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="6ab1f-119">Par défaut, il se trouve sous *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="6ab1f-120">Choisissez le kit de développement logiciel (SDK) pour lequel vous souhaitez installer IntelliSense et accédez au chemin d’accès associé.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="6ab1f-121">Les options suivantes sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="6ab1f-121">You have the following options:</span></span>

      | <span data-ttu-id="6ab1f-122">Type de kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="6ab1f-122">SDK type</span></span>        | <span data-ttu-id="6ab1f-123">Chemin d'accès</span><span class="sxs-lookup"><span data-stu-id="6ab1f-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="6ab1f-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ab1f-124">.NET Core</span></span>       | <span data-ttu-id="6ab1f-125">*Microsoft. Netcore. app. Ref*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="6ab1f-126">Bureau Windows</span><span class="sxs-lookup"><span data-stu-id="6ab1f-126">Windows Desktop</span></span> | <span data-ttu-id="6ab1f-127">*Microsoft. WindowsDesktop. app. Ref*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="6ab1f-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="6ab1f-128">.NET Standard</span></span>   | <span data-ttu-id="6ab1f-129">*Netstandard. Library. Ref*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-129">*NETStandard.Library.Ref*</span></span>          |
   
   1. <span data-ttu-id="6ab1f-130">Accédez à la version pour laquelle vous souhaitez installer la fonctionnalité IntelliSense localisée.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="6ab1f-131">Par exemple, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="6ab1f-132">Ouvrez le dossier *ref* .</span><span class="sxs-lookup"><span data-stu-id="6ab1f-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="6ab1f-133">Ouvrez le dossier moniker.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-133">Open the moniker folder.</span></span> <span data-ttu-id="6ab1f-134">Par exemple, *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="6ab1f-135">Par conséquent, le chemin d’accès complet que vous recherchez devrait ressembler à *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="6ab1f-136">Créez un sous-dossier à l’intérieur du dossier moniker que vous venez d’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="6ab1f-137">Le nom du dossier indique la langue que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="6ab1f-138">Le tableau suivant spécifie les différentes options :</span><span class="sxs-lookup"><span data-stu-id="6ab1f-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="6ab1f-139">Langue</span><span class="sxs-lookup"><span data-stu-id="6ab1f-139">Language</span></span>              | <span data-ttu-id="6ab1f-140">Nom du dossier</span><span class="sxs-lookup"><span data-stu-id="6ab1f-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="6ab1f-141">Portugais (Brésil)</span><span class="sxs-lookup"><span data-stu-id="6ab1f-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="6ab1f-142">*PT-BR*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-142">*pt-br*</span></span>     |
   | <span data-ttu-id="6ab1f-143">Chinois (simplifié)</span><span class="sxs-lookup"><span data-stu-id="6ab1f-143">Chinese (simplified)</span></span>  | <span data-ttu-id="6ab1f-144">*zh-Hans*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="6ab1f-145">Chinois (traditionnel)</span><span class="sxs-lookup"><span data-stu-id="6ab1f-145">Chinese (traditional)</span></span> | <span data-ttu-id="6ab1f-146">*zh-Hant*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="6ab1f-147">Français</span><span class="sxs-lookup"><span data-stu-id="6ab1f-147">French</span></span>                | <span data-ttu-id="6ab1f-148">*fr*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-148">*fr*</span></span>        |
   | <span data-ttu-id="6ab1f-149">Allemand</span><span class="sxs-lookup"><span data-stu-id="6ab1f-149">German</span></span>                | <span data-ttu-id="6ab1f-150">*de*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-150">*de*</span></span>        |
   | <span data-ttu-id="6ab1f-151">Italien</span><span class="sxs-lookup"><span data-stu-id="6ab1f-151">Italian</span></span>               | <span data-ttu-id="6ab1f-152">*tel*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-152">*it*</span></span>        |
   | <span data-ttu-id="6ab1f-153">Japonais</span><span class="sxs-lookup"><span data-stu-id="6ab1f-153">Japanese</span></span>              | <span data-ttu-id="6ab1f-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-154">*ja*</span></span>        |
   | <span data-ttu-id="6ab1f-155">Coréen</span><span class="sxs-lookup"><span data-stu-id="6ab1f-155">Korean</span></span>                | <span data-ttu-id="6ab1f-156">*Ko*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-156">*ko*</span></span>        |
   | <span data-ttu-id="6ab1f-157">Russe</span><span class="sxs-lookup"><span data-stu-id="6ab1f-157">Russian</span></span>               | <span data-ttu-id="6ab1f-158">*Arabie*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-158">*ru*</span></span>        |
   | <span data-ttu-id="6ab1f-159">Espagnol</span><span class="sxs-lookup"><span data-stu-id="6ab1f-159">Spanish</span></span>               | <span data-ttu-id="6ab1f-160">*sec*</span><span class="sxs-lookup"><span data-stu-id="6ab1f-160">*es*</span></span>        |

1. <span data-ttu-id="6ab1f-161">Copiez les fichiers *. xml* que vous avez extraits à l’étape 3 dans ce nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="6ab1f-162">Les fichiers *. xml* sont décomposés par dossiers SDK. par conséquent, copiez-les dans le kit de développement logiciel (SDK) correspondant que vous avez choisi à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="6ab1f-163">Modifier le langage de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ab1f-163">Modify Visual Studio language</span></span>

<span data-ttu-id="6ab1f-164">Pour que Visual Studio utilise une langue différente pour IntelliSense, installez le module linguistique approprié.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="6ab1f-165">Vous pouvez effectuer cette opération [pendant l’installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou ultérieurement en modifiant l’installation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="6ab1f-166">Si vous avez déjà configuré Visual Studio dans le langage de votre choix, votre installation IntelliSense est prête.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="6ab1f-167">Installer le module linguistique</span><span class="sxs-lookup"><span data-stu-id="6ab1f-167">Install the language pack</span></span>

<span data-ttu-id="6ab1f-168">Si vous n’avez pas installé le module linguistique souhaité au cours de l’installation, mettez à jour Visual Studio comme suit pour installer le module linguistique :</span><span class="sxs-lookup"><span data-stu-id="6ab1f-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ab1f-169">Pour installer, mettre à jour ou modifier Visual Studio, vous devez ouvrir une session avec un compte disposant de l’autorisation administrateur.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="6ab1f-170">Pour plus d’informations, consultez [Autorisations utilisateur et Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6ab1f-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="6ab1f-171">Recherchez le programme d’installation de Visual Studio sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="6ab1f-172">Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Ouvrir le Visual Studio Installer à partir de Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="6ab1f-174">Vous trouverez également Visual Studio Installer à l’emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="6ab1f-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="6ab1f-175">Vous devrez peut-être mettre à jour le programme d’installation avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="6ab1f-176">Dans ce cas, suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="6ab1f-177">Dans le programme d’installation, recherchez l’édition de Visual Studio à laquelle vous souhaitez ajouter le module linguistique, puis choisissez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Mettre à jour ou modifier Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="6ab1f-179">Si vous ne voyez pas de bouton **modifier** mais que vous voyez une **mise à jour** , vous devez mettre à jour votre Visual Studio avant de pouvoir modifier votre installation.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="6ab1f-180">Une fois la mise à jour terminée, le bouton **modifier** doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="6ab1f-181">Sous l’onglet **modules linguistiques** , sélectionnez ou désélectionnez les langues que vous voulez installer ou désinstaller.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Onglet modules linguistiques de Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="6ab1f-183">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-183">Choose **Modify**.</span></span> <span data-ttu-id="6ab1f-184">La mise à jour démarre.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="6ab1f-185">Modifier les paramètres de langue dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ab1f-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="6ab1f-186">Une fois que vous avez installé les modules linguistiques souhaités, modifiez les paramètres de Visual Studio pour utiliser une autre langue :</span><span class="sxs-lookup"><span data-stu-id="6ab1f-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="6ab1f-187">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="6ab1f-188">Dans la fenêtre de démarrage, choisissez **Continuer sans code**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="6ab1f-189">Dans la barre de menus, sélectionnez **outils** > **options**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="6ab1f-190">La boîte de dialogue Options s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="6ab1f-191">Sous le nœud **environnement** , choisissez **paramètres internationaux**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="6ab1f-192">Dans la liste déroulante **langue** , sélectionnez la langue de votre choix.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="6ab1f-193">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-193">Choose **OK**.</span></span> 

1. <span data-ttu-id="6ab1f-194">Une boîte de dialogue vous informe que vous devez redémarrer Visual Studio pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="6ab1f-195">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-195">Choose **OK**.</span></span>

1. <span data-ttu-id="6ab1f-196">Redémarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-196">Restart Visual Studio.</span></span>

<span data-ttu-id="6ab1f-197">Après cela, votre IntelliSense doit fonctionner comme prévu quand vous ouvrez un projet .NET Core qui cible la version des fichiers IntelliSense que vous venez d’installer.</span><span class="sxs-lookup"><span data-stu-id="6ab1f-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ab1f-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ab1f-198">See also</span></span>

- [<span data-ttu-id="6ab1f-199">IntelliSense dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ab1f-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
