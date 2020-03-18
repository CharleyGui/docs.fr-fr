---
title: Installer des fichiers IntelliSense localisés
description: Découvrez comment configurer votre machine de développement pour utiliser des fichiers IntelliSense localisés pour des projets .NET Core dans Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157711"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="67f98-103">Comment installer des fichiers IntelliSense localisés pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="67f98-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="67f98-104">[IntelliSense](/visualstudio/ide/using-intellisense) est une aide à l’achèvement du code qui est disponible dans différents environnements de développement intégrés (IDE), tels que Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67f98-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="67f98-105">Par défaut, lorsque vous développez des projets .NET Core, le SDK ne comprend que la version anglaise des fichiers IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="67f98-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="67f98-106">Cet article explique :</span><span class="sxs-lookup"><span data-stu-id="67f98-106">This article explains:</span></span>

- <span data-ttu-id="67f98-107">Comment installer la version localisée de ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="67f98-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="67f98-108">Comment modifier l’installation Visual Studio pour utiliser une langue différente.</span><span class="sxs-lookup"><span data-stu-id="67f98-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="67f98-109">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="67f98-109">Prerequisites</span></span>

- <span data-ttu-id="67f98-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="67f98-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="67f98-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="67f98-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="67f98-112">Télécharger et installer les fichiers IntelliSense localisés</span><span class="sxs-lookup"><span data-stu-id="67f98-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67f98-113">Cette procédure exige que vous ayez la permission de l’administrateur de copier les fichiers IntelliSense au dossier d’installation .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67f98-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="67f98-114">Rendez-vous sur la page [télécharger les fichiers IntelliSense.](https://dotnet.microsoft.com/download/dotnet-core/intellisense)</span><span class="sxs-lookup"><span data-stu-id="67f98-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="67f98-115">Téléchargez le fichier IntelliSense pour la langue et la version que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="67f98-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="67f98-116">Extraire le contenu du fichier zip.</span><span class="sxs-lookup"><span data-stu-id="67f98-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="67f98-117">Naviguez vers le dossier Intellisense .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67f98-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="67f98-118">Naviguez vers le dossier d’installation .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67f98-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="67f98-119">Par défaut, il est inférieur *à %ProgramFiles%-dotnet packs*.</span><span class="sxs-lookup"><span data-stu-id="67f98-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="67f98-120">Choisissez le SDK pour lequel vous souhaitez installer l’IntelliSense et naviguez vers le chemin associé.</span><span class="sxs-lookup"><span data-stu-id="67f98-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="67f98-121">Vous disposez des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="67f98-121">You have the following options:</span></span>

      | <span data-ttu-id="67f98-122">Type de kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="67f98-122">SDK type</span></span>        | <span data-ttu-id="67f98-123">Path</span><span class="sxs-lookup"><span data-stu-id="67f98-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="67f98-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="67f98-124">.NET Core</span></span>       | <span data-ttu-id="67f98-125">*Microsoft.NETCore.App.Ref (en anglais seulement)*</span><span class="sxs-lookup"><span data-stu-id="67f98-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="67f98-126">Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="67f98-126">Windows Desktop</span></span> | <span data-ttu-id="67f98-127">*Microsoft.WindowsDesktop.App.Ref (en)*</span><span class="sxs-lookup"><span data-stu-id="67f98-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="67f98-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="67f98-128">.NET Standard</span></span>   | <span data-ttu-id="67f98-129">*NETStandard.Library.Ref NETStandard.Library.Ref NETStandard.Library.Ref NETStand*</span><span class="sxs-lookup"><span data-stu-id="67f98-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="67f98-130">Naviguez vers la version pour laquelle vous souhaitez installer l’IntelliSense localisé.</span><span class="sxs-lookup"><span data-stu-id="67f98-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="67f98-131">Par exemple, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="67f98-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="67f98-132">Ouvrez le dossier *d’arbitre.*</span><span class="sxs-lookup"><span data-stu-id="67f98-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="67f98-133">Ouvrez le dossier de surnom.</span><span class="sxs-lookup"><span data-stu-id="67f98-133">Open the moniker folder.</span></span> <span data-ttu-id="67f98-134">Par exemple, *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="67f98-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="67f98-135">Ainsi, le chemin complet que vous navigueriez à ressembler à *C: 'Program Files’dotnet’packs-Microsoft.NETCore.App.Ref'3.1.0'ref’netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="67f98-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="67f98-136">Créez un sous-pliage à l’intérieur du dossier de surnom que vous venez d’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="67f98-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="67f98-137">Le nom du dossier indique la langue que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="67f98-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="67f98-138">Le tableau suivant précise les différentes options :</span><span class="sxs-lookup"><span data-stu-id="67f98-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="67f98-139">Langage</span><span class="sxs-lookup"><span data-stu-id="67f98-139">Language</span></span>              | <span data-ttu-id="67f98-140">Nom du dossier</span><span class="sxs-lookup"><span data-stu-id="67f98-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="67f98-141">Portugais brésilien</span><span class="sxs-lookup"><span data-stu-id="67f98-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="67f98-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="67f98-142">*pt-br*</span></span>     |
   | <span data-ttu-id="67f98-143">Chinois (simplifié)</span><span class="sxs-lookup"><span data-stu-id="67f98-143">Chinese (simplified)</span></span>  | <span data-ttu-id="67f98-144">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="67f98-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="67f98-145">Chinois (traditionnel)</span><span class="sxs-lookup"><span data-stu-id="67f98-145">Chinese (traditional)</span></span> | <span data-ttu-id="67f98-146">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="67f98-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="67f98-147">Français</span><span class="sxs-lookup"><span data-stu-id="67f98-147">French</span></span>                | <span data-ttu-id="67f98-148">*Fr*</span><span class="sxs-lookup"><span data-stu-id="67f98-148">*fr*</span></span>        |
   | <span data-ttu-id="67f98-149">Allemand</span><span class="sxs-lookup"><span data-stu-id="67f98-149">German</span></span>                | <span data-ttu-id="67f98-150">*de*</span><span class="sxs-lookup"><span data-stu-id="67f98-150">*de*</span></span>        |
   | <span data-ttu-id="67f98-151">Italien</span><span class="sxs-lookup"><span data-stu-id="67f98-151">Italian</span></span>               | <span data-ttu-id="67f98-152">*Il*</span><span class="sxs-lookup"><span data-stu-id="67f98-152">*it*</span></span>        |
   | <span data-ttu-id="67f98-153">Japonais</span><span class="sxs-lookup"><span data-stu-id="67f98-153">Japanese</span></span>              | <span data-ttu-id="67f98-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="67f98-154">*ja*</span></span>        |
   | <span data-ttu-id="67f98-155">Coréen</span><span class="sxs-lookup"><span data-stu-id="67f98-155">Korean</span></span>                | <span data-ttu-id="67f98-156">*ko (en)*</span><span class="sxs-lookup"><span data-stu-id="67f98-156">*ko*</span></span>        |
   | <span data-ttu-id="67f98-157">Russe</span><span class="sxs-lookup"><span data-stu-id="67f98-157">Russian</span></span>               | <span data-ttu-id="67f98-158">*Ru*</span><span class="sxs-lookup"><span data-stu-id="67f98-158">*ru*</span></span>        |
   | <span data-ttu-id="67f98-159">Espagnol</span><span class="sxs-lookup"><span data-stu-id="67f98-159">Spanish</span></span>               | <span data-ttu-id="67f98-160">*es es*</span><span class="sxs-lookup"><span data-stu-id="67f98-160">*es*</span></span>        |

1. <span data-ttu-id="67f98-161">Copiez les fichiers *.xml* que vous avez extraits sur l’étape 3 à ce nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="67f98-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="67f98-162">Les fichiers *.xml* sont décomposés par les dossiers SDK, alors copiez-les sur le SDK correspondant que vous avez choisi sur l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="67f98-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="67f98-163">Modifier le langage Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67f98-163">Modify Visual Studio language</span></span>

<span data-ttu-id="67f98-164">Pour Visual Studio d’utiliser une langue différente pour IntelliSense, installez le pack de langue approprié.</span><span class="sxs-lookup"><span data-stu-id="67f98-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="67f98-165">Cela peut être fait lors de [l’installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou à une date ultérieure en modifiant l’installation Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67f98-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="67f98-166">Si vous avez déjà Visual Studio configuré dans la langue de votre choix, votre installation IntelliSense est prête.</span><span class="sxs-lookup"><span data-stu-id="67f98-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="67f98-167">Installer le pack de langue</span><span class="sxs-lookup"><span data-stu-id="67f98-167">Install the language pack</span></span>

<span data-ttu-id="67f98-168">Si vous n’avez pas installé le pack de langue désiré pendant la configuration, mettez à jour Visual Studio comme suit pour installer le pack de langue :</span><span class="sxs-lookup"><span data-stu-id="67f98-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67f98-169">Pour installer, mettre à jour ou modifier Visual Studio, vous devez vous connecter avec un compte qui a la permission de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="67f98-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="67f98-170">Pour plus d’informations, voir [les autorisations des utilisateurs et Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="67f98-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="67f98-171">Recherchez le programme d’installation de Visual Studio sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="67f98-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="67f98-172">Par exemple, sur un ordinateur exécutant Windows 10, sélectionnez **Démarrer**, puis faites défiler jusqu’à la lettre **V** où il est répertorié comme **Visual Studio Installer**.</span><span class="sxs-lookup"><span data-stu-id="67f98-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Ouvrez l’installateur visual studio à partir de Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="67f98-174">Vous trouverez également Visual Studio Installer à l’emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="67f98-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="67f98-175">Vous devrez peut-être mettre à jour le programme d’installation avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="67f98-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="67f98-176">Dans ce cas, suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="67f98-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="67f98-177">Dans l’installateur, recherchez l’édition de Visual Studio à laquelle vous souhaitez ajouter le pack de langue, puis choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="67f98-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Mettre à jour ou modifier Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="67f98-179">Si vous ne voyez pas de bouton **Modifier** mais que vous en voyez une **mise à jour** à la place, vous devez mettre à jour votre studio visuel avant de pouvoir modifier votre installation.</span><span class="sxs-lookup"><span data-stu-id="67f98-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="67f98-180">Une fois la mise à jour terminée, le bouton **Modifier** doit s’apparaître.</span><span class="sxs-lookup"><span data-stu-id="67f98-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="67f98-181">Dans **l’onglet Packs langue,** sélectionnez ou désélectionner les langues que vous souhaitez installer ou désinstaller.</span><span class="sxs-lookup"><span data-stu-id="67f98-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visuel Studio langue packs onglet](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="67f98-183">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="67f98-183">Choose **Modify**.</span></span> <span data-ttu-id="67f98-184">La mise à jour démarre.</span><span class="sxs-lookup"><span data-stu-id="67f98-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="67f98-185">Modifier les paramètres linguistiques dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67f98-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="67f98-186">Une fois que vous avez installé les packs de langage souhaités, modifiez vos paramètres Visual Studio pour utiliser une langue différente :</span><span class="sxs-lookup"><span data-stu-id="67f98-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="67f98-187">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67f98-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="67f98-188">Dans la fenêtre de démarrage, choisissez **Continuer sans code**.</span><span class="sxs-lookup"><span data-stu-id="67f98-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="67f98-189">Sur la barre de menu, sélectionnez **Options Outils** > **.**</span><span class="sxs-lookup"><span data-stu-id="67f98-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="67f98-190">Le dialogue Options s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="67f98-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="67f98-191">Sous le nœud **Environnement,** choisissez **paramètres internationaux**.</span><span class="sxs-lookup"><span data-stu-id="67f98-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="67f98-192">Sur le **décrochage linguistique,** sélectionnez la langue désirée.</span><span class="sxs-lookup"><span data-stu-id="67f98-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="67f98-193">Choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="67f98-193">Choose **OK**.</span></span>

1. <span data-ttu-id="67f98-194">Un dialogue vous informe que vous devez redémarrer Visual Studio pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="67f98-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="67f98-195">Choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="67f98-195">Choose **OK**.</span></span>

1. <span data-ttu-id="67f98-196">Redémarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67f98-196">Restart Visual Studio.</span></span>

<span data-ttu-id="67f98-197">Après cela, votre IntelliSense devrait fonctionner comme prévu lorsque vous ouvrez un projet .NET Core qui cible la version des fichiers IntelliSense que vous venez d’installer.</span><span class="sxs-lookup"><span data-stu-id="67f98-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="67f98-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67f98-198">See also</span></span>

- [<span data-ttu-id="67f98-199">IntelliSense dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67f98-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
