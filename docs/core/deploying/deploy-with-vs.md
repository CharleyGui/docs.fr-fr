---
title: Déployer des applications .NET Core avec Visual Studio
description: Apprenez à déployer des applications .NET Core avec Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f80b483fedc600a1e1a48d36ce9b7b95c6de9f27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428891"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="efbbc-103">Déployer des applications .NET Core avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="efbbc-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="efbbc-104">Pour déployer une application .NET Core, vous pouvez soit effectuer un *déploiement dépendant du framework* (qui inclut vos binaires d’application, mais qui dépend de la présence de .NET Core sur le système cible), soit effectuer un *déploiement autonome* (qui inclut votre application et les binaires .NET Core).</span><span class="sxs-lookup"><span data-stu-id="efbbc-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="efbbc-105">Pour obtenir une vue d’ensemble du déploiement des applications .NET Core, consultez [Déploiement d’applications .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="efbbc-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="efbbc-106">Les sections suivantes montrent comment utiliser Microsoft Visual Studio pour créer les genres de déploiements suivants :</span><span class="sxs-lookup"><span data-stu-id="efbbc-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="efbbc-107">Déploiement dépendant du framework</span><span class="sxs-lookup"><span data-stu-id="efbbc-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="efbbc-108">Déploiement dépendant du framework avec des dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="efbbc-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="efbbc-109">Déploiement autonome</span><span class="sxs-lookup"><span data-stu-id="efbbc-109">Self-contained deployment</span></span>
- <span data-ttu-id="efbbc-110">Déploiement autonome avec des dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="efbbc-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="efbbc-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="efbbc-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="efbbc-112">Déploiement dépendant du framework</span><span class="sxs-lookup"><span data-stu-id="efbbc-112">Framework-dependent deployment</span></span>

<span data-ttu-id="efbbc-113">Le déploiement d’un déploiement dépendant du framework sans dépendances tierces implique simplement la génération, le test et la publication de l’application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="efbbc-114">Un exemple simple écrit en C# illustre le processus.</span><span class="sxs-lookup"><span data-stu-id="efbbc-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="efbbc-115">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="efbbc-115">Create the project.</span></span>

   <span data-ttu-id="efbbc-116">Sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="efbbc-117">Dans la boîte de dialogue **Nouveau projet**, développez les catégories de projet de votre langage (C# ou Visual Basic) au sein du volet des types de projet **Installé**, choisissez **.NET Core**, puis sélectionnez le modèle **Application console (.NET Core)** dans le volet central.</span><span class="sxs-lookup"><span data-stu-id="efbbc-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="efbbc-118">Entrez un nom de projet, tel que « FDD », dans la zone de texte **Nom**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="efbbc-119">Sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="efbbc-120">Ajoutez le code source de l’application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-120">Add the application's source code.</span></span>

   <span data-ttu-id="efbbc-121">Ouvrez le fichier *Program.cs* ou *Program.vb* dans l’éditeur, puis remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="efbbc-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="efbbc-122">Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés.</span><span class="sxs-lookup"><span data-stu-id="efbbc-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="efbbc-123">Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.</span><span class="sxs-lookup"><span data-stu-id="efbbc-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="efbbc-124">Créez une build Debug de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="efbbc-125">Sélectionnez **Générer** > **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="efbbc-126">Vous pouvez également compiler et exécuter la build Debug de votre application en sélectionnant **Déboguer** > **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="efbbc-127">Déployez votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-127">Deploy your app.</span></span>

   <span data-ttu-id="efbbc-128">Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="efbbc-129">Pour publier à partir de Visual Studio, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="efbbc-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="efbbc-130">Remplacez la configuration de solution **Debug** par **Release** dans la barre d’outils pour générer une build Release (et non une build Debug) de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="efbbc-131">Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="efbbc-132">Sous l’onglet **Publier**, sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="efbbc-133">Visual Studio écrit les fichiers qui composent votre application dans le système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="efbbc-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="efbbc-134">L’onglet **Publier** affiche maintenant un seul profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="efbbc-135">Les paramètres de configuration du profil sont affichés dans la section **Résumé** de l’onglet.</span><span class="sxs-lookup"><span data-stu-id="efbbc-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="efbbc-136">Les fichiers résultants sont placés dans un répertoire nommé `Publish` sur Windows (`publish` sur les systèmes Unix), qui se trouve dans un sous-répertoire du sous-répertoire *.\bin\release\netcoreapp2.1* de votre projet.</span><span class="sxs-lookup"><span data-stu-id="efbbc-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="efbbc-137">En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="efbbc-138">Le fichier est surtout utile pour le débogage d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="efbbc-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="efbbc-139">Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="efbbc-140">Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="efbbc-141">Déployez l’ensemble complet des fichiers d’application de la façon qui vous convient.</span><span class="sxs-lookup"><span data-stu-id="efbbc-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="efbbc-142">Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.</span><span class="sxs-lookup"><span data-stu-id="efbbc-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="efbbc-143">Une fois l’installation terminée, les utilisateurs peuvent exécuter votre application en utilisant la commande `dotnet` suivie du nom de l’application. Par exemple : `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="efbbc-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="efbbc-144">Outre les binaires de l’application, votre programme d’installation doit également regrouper le programme d’installation du framework partagé ou vérifier qu’il est bien installé comme prérequis de l’installation de l’application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="efbbc-145">L’installation du framework partagé nécessite un accès Administrateur/root car il est à l’échelle de la machine.</span><span class="sxs-lookup"><span data-stu-id="efbbc-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="efbbc-146">Déploiement dépendant du framework avec des dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="efbbc-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="efbbc-147">Pour exécuter un déploiement dépendant du framework avec une ou plusieurs dépendances tierces, ces dépendances doivent être accessibles à votre projet.</span><span class="sxs-lookup"><span data-stu-id="efbbc-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="efbbc-148">Avant de pouvoir générer votre application, vous devez effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="efbbc-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="efbbc-149">Utilisez le **Gestionnaire de package NuGet** pour ajouter à votre projet une référence à un package NuGet et installer le package s’il n’est pas disponible sur votre système.</span><span class="sxs-lookup"><span data-stu-id="efbbc-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="efbbc-150">Pour ouvrir le Gestionnaire de package, sélectionnez **Outils** > **Gestionnaire de package NuGet** > **Gérer les packages NuGet pour la solution**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="efbbc-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span><span class="sxs-lookup"><span data-stu-id="efbbc-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="efbbc-152">L’onglet **Installé** répertorie les packages NuGet installés sur votre système.</span><span class="sxs-lookup"><span data-stu-id="efbbc-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="efbbc-153">Si `Newtonsoft.Json` n’est pas répertorié, sélectionnez l’onglet **Parcourir** et entrez « Newtonsoft.Json » dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="efbbc-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="efbbc-154">Sélectionnez `Newtonsoft.Json` et, dans le volet droit, choisissez votre projet avant de sélectionner **Installer**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="efbbc-155">Si `Newtonsoft.Json` est déjà installé sur votre système, ajoutez-le à votre projet en sélectionnant votre projet dans le volet droit de l’onglet **Gérer les packages de la solution**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="efbbc-156">Notez qu’un déploiement dépendant du framework avec des dépendances tierces n’est portable que dans la mesure de la portabilité de ses dépendances tierces.</span><span class="sxs-lookup"><span data-stu-id="efbbc-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="efbbc-157">Par exemple, si une bibliothèque tierce prend uniquement en charge macOS, l’application n’est pas portable sur des systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="efbbc-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="efbbc-158">Cela se produit si la dépendance tierce elle-même dépend du code natif.</span><span class="sxs-lookup"><span data-stu-id="efbbc-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="efbbc-159">Un [serveur Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) constitue un bon exemple, car il nécessite une dépendance native à [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="efbbc-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="efbbc-160">Quand un déploiement dépendant du framework est créé pour une application avec ce type de dépendance tierce, le résultat publié contient un dossier pour chaque [identificateur de runtime](../rid-catalog.md) pris en charge par la dépendance native (et qui existe dans le package NuGet).</span><span class="sxs-lookup"><span data-stu-id="efbbc-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="efbbc-161">Déploiement autonome sans dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="efbbc-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="efbbc-162">L’exécution d’un déploiement autonome sans aucune dépendance tierce implique la création du projet, la modification du fichier *csproj*, la génération, le test et la publication de l’application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="efbbc-163">Un exemple simple écrit en C# illustre le processus.</span><span class="sxs-lookup"><span data-stu-id="efbbc-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="efbbc-164">Commencez par créer, coder et tester votre projet comme pour un déploiement dépendant du framework :</span><span class="sxs-lookup"><span data-stu-id="efbbc-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="efbbc-165">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="efbbc-165">Create the project.</span></span>

   <span data-ttu-id="efbbc-166">Sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="efbbc-167">Dans la boîte de dialogue **Nouveau projet**, développez les catégories de projet de votre langage (C# ou Visual Basic) au sein du volet des types de projet **Installé**, choisissez **.NET Core**, puis sélectionnez le modèle **Application console (.NET Core)** dans le volet central.</span><span class="sxs-lookup"><span data-stu-id="efbbc-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="efbbc-168">Entrez un nom de projet, tel que « SCD », dans la zone de texte **Nom**, puis sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="efbbc-169">Ajoutez le code source de l’application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-169">Add the application's source code.</span></span>

   <span data-ttu-id="efbbc-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span><span class="sxs-lookup"><span data-stu-id="efbbc-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="efbbc-171">Il invite l’utilisateur à entrer du texte et affiche les différents mots entrés.</span><span class="sxs-lookup"><span data-stu-id="efbbc-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="efbbc-172">Il utilise l’expression régulière `\w+` pour séparer les mots dans le texte d’entrée.</span><span class="sxs-lookup"><span data-stu-id="efbbc-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="efbbc-173">Déterminez si vous souhaitez utiliser le mode invariant de globalisation.</span><span class="sxs-lookup"><span data-stu-id="efbbc-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="efbbc-174">En particulier, si votre application cible Linux, vous pouvez réduire la taille totale de votre déploiement en tirant parti du [mode invariant de globalisation](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="efbbc-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="efbbc-175">Le mode invariant de globalisation est utile pour les applications qui ne sont pas globalement compatibles et qui peuvent utiliser les conventions de mise en forme, les conventions de casse et la comparaison de chaînes, ainsi que l’ordre de tri de la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="efbbc-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="efbbc-176">Pour activer le mode invariant, cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Modifier SCD.csproj** ou **Modifier SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="efbbc-177">Ajoutez ensuite les lignes en surbrillance suivantes au fichier :</span><span class="sxs-lookup"><span data-stu-id="efbbc-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="efbbc-178">Créez une build Debug de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="efbbc-179">Sélectionnez **Générer** > **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="efbbc-180">Vous pouvez également compiler et exécuter la build Debug de votre application en sélectionnant **Déboguer** > **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="efbbc-181">Cette étape de débogage vous permet d’identifier les problèmes de votre application quand elle s’exécute sur la plateforme hôte.</span><span class="sxs-lookup"><span data-stu-id="efbbc-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="efbbc-182">Vous devez tout de même la tester sur chacune des plateformes cibles.</span><span class="sxs-lookup"><span data-stu-id="efbbc-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="efbbc-183">Si vous avez activé le mode invariant de globalisation, vérifiez si l’absence de données relatives à la culture convient à votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="efbbc-184">Une fois le débogage effectué, vous pouvez publier votre déploiement autonome :</span><span class="sxs-lookup"><span data-stu-id="efbbc-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="efbbc-185">Visual Studio 15.6 et versions antérieures</span><span class="sxs-lookup"><span data-stu-id="efbbc-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="efbbc-186">Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.</span><span class="sxs-lookup"><span data-stu-id="efbbc-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="efbbc-187">Pour publier votre application à partir de Visual Studio, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="efbbc-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="efbbc-188">Définissez les plateformes ciblées par votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="efbbc-189">Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Modifier SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="efbbc-190">Créez une balise `<RuntimeIdentifiers>` dans la section `<PropertyGroup>` de votre fichier *csproj* qui définit les plateformes ciblées par votre application, et spécifiez l’identificateur de runtime de chaque plateforme ciblée.</span><span class="sxs-lookup"><span data-stu-id="efbbc-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="efbbc-191">Notez que vous devez également ajouter un point-virgule pour séparer les identificateurs de runtime.</span><span class="sxs-lookup"><span data-stu-id="efbbc-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="efbbc-192">Consultez [Catalogue des identificateurs de runtime](../rid-catalog.md) pour obtenir une liste des identificateurs de runtime.</span><span class="sxs-lookup"><span data-stu-id="efbbc-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="efbbc-193">Dans l’exemple suivant, l’application s’exécute sur les systèmes d’exploitation Windows 10 64 bits et sur le système d’exploitation OS X 64 bits version 10.11.</span><span class="sxs-lookup"><span data-stu-id="efbbc-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="efbbc-194">Notez que l’élément `<RuntimeIdentifiers>` peut être placé dans n’importe quelle section `<PropertyGroup>` de votre fichier *csproj*.</span><span class="sxs-lookup"><span data-stu-id="efbbc-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="efbbc-195">Un exemple complet de fichier *csproj* figure plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="efbbc-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="efbbc-196">Publiez votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-196">Publish your app.</span></span>

   <span data-ttu-id="efbbc-197">Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.</span><span class="sxs-lookup"><span data-stu-id="efbbc-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="efbbc-198">Pour publier votre application à partir de Visual Studio, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="efbbc-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="efbbc-199">Remplacez la configuration de solution **Debug** par **Release** dans la barre d’outils pour générer une build Release (et non une build Debug) de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="efbbc-200">Cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="efbbc-201">Sous l’onglet **Publier**, sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="efbbc-202">Visual Studio écrit les fichiers qui composent votre application dans le système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="efbbc-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="efbbc-203">L’onglet **Publier** affiche maintenant un seul profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="efbbc-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span><span class="sxs-lookup"><span data-stu-id="efbbc-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="efbbc-205">Par défaut, Visual Studio écrit tous les fichiers publiés dans un répertoire unique.</span><span class="sxs-lookup"><span data-stu-id="efbbc-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="efbbc-206">Pour des raisons pratiques, il est préférable de créer des profils séparés pour chaque runtime cible et de placer les fichiers publiés dans un répertoire spécifique à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="efbbc-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="efbbc-207">Vous devez donc créer un profil de publication distinct pour chaque plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="efbbc-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="efbbc-208">À présent, effectuez les étapes suivantes pour regénérer l’application pour chaque plateforme :</span><span class="sxs-lookup"><span data-stu-id="efbbc-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="efbbc-209">Sélectionnez **Créer un profil** dans la boîte de dialogue **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="efbbc-210">Dans la boîte de dialogue **Choisir une cible de publication** remplacez l’emplacement indiqué dans **Choisir un dossier** par *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="efbbc-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="efbbc-211">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-211">Select **OK**.</span></span>

         1. <span data-ttu-id="efbbc-212">Sélectionnez le nouveau profil (**FolderProfile1**) dans la liste des profils et vérifiez que le **Runtime cible** est `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="efbbc-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="efbbc-213">Si ce n’est pas le cas, sélectionnez **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="efbbc-214">Dans la boîte de dialogue **Paramètres du profil**, définissez **Runtime cible** avec la valeur `win10-x64` et sélectionnez **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="efbbc-215">Sinon, sélectionnez **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="efbbc-216">Sélectionnez **Publier** pour publier votre application pour des plateformes Windows 10 64 bits.</span><span class="sxs-lookup"><span data-stu-id="efbbc-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="efbbc-217">Suivez les étapes précédentes pour créer un profil pour la plateforme `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="efbbc-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="efbbc-218">L’**Emplacement cible** est *bin\Release\PublishOutput\osx.10.11-x64* et le **Runtime cible** est `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="efbbc-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="efbbc-219">Le nom attribué par Visual Studio à ce profil est **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="efbbc-220">Notez que chaque emplacement cible contient l’ensemble complet des fichiers nécessaires pour lancer votre application, à savoir les fichiers de votre application et tous les fichiers .NET Core.</span><span class="sxs-lookup"><span data-stu-id="efbbc-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="efbbc-221">En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="efbbc-222">Le fichier est surtout utile pour le débogage d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="efbbc-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="efbbc-223">Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="efbbc-224">Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="efbbc-225">Déployez les fichiers publiés de la façon qui vous convient.</span><span class="sxs-lookup"><span data-stu-id="efbbc-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="efbbc-226">Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.</span><span class="sxs-lookup"><span data-stu-id="efbbc-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="efbbc-227">Voici le fichier *csproj* complet pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="efbbc-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="efbbc-228">Visual Studio 15.7 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="efbbc-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="efbbc-229">Après avoir débogué et testé le programme, créez les fichiers à déployer avec votre application pour chaque plateforme ciblée.</span><span class="sxs-lookup"><span data-stu-id="efbbc-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="efbbc-230">Cela implique la création d’un profil distinct pour chaque plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="efbbc-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="efbbc-231">Pour chaque plateforme ciblée par votre application, effectuez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="efbbc-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="efbbc-232">Créez un profil pour la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="efbbc-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="efbbc-233">S’il s’agit du premier profil que vous créez, cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="efbbc-234">Si vous avez déjà créé un profil, cliquez avec le bouton droit sur le projet pour ouvrir la boîte de dialogue **Publier**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="efbbc-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="efbbc-235">Sélectionnez ensuite **Nouveau profil**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="efbbc-236">La boîte de dialogue **Choisir une cible de publication** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="efbbc-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="efbbc-237">Sélectionnez l’emplacement où Visual Studio publie votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="efbbc-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span><span class="sxs-lookup"><span data-stu-id="efbbc-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="efbbc-239">Si vous publiez sur plusieurs plateformes, ajoutez une chaîne identifiant la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="efbbc-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="efbbc-240">Par exemple, si vous ajoutez la chaîne « linux » au chemin de fichier, Visual Studio publie le déploiement dépendant du framework de votre application sur *\<répertoire-projet>\bin\Release\netcoreapp2.1\publish\linux*.</span><span class="sxs-lookup"><span data-stu-id="efbbc-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="efbbc-241">Pour créer le profil, sélectionnez l’icône de liste déroulante en regard du bouton **Publier**, puis sélectionnez **Créer un profil**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="efbbc-242">Sélectionnez ensuite le bouton **Créer un profil** pour créer le profil.</span><span class="sxs-lookup"><span data-stu-id="efbbc-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="efbbc-243">Indiquez que vous publiez un déploiement autonome, et définissez la plateforme ciblée par votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="efbbc-244">Dans la boîte de dialogue **Publier**, sélectionnez le lien **Configurer** pour ouvrir la boîte de dialogue **Paramètres du profil**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="efbbc-245">Sélectionnez **Autonome** dans la zone de liste **Mode de déploiement**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="efbbc-246">Dans la zone de liste **Runtime cible**, sélectionnez l’une des plateformes ciblées par votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="efbbc-247">Sélectionnez **Enregistrer** pour faire accepter vos changements, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="efbbc-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="efbbc-248">Nommez votre profil.</span><span class="sxs-lookup"><span data-stu-id="efbbc-248">Name your profile.</span></span>

   1. <span data-ttu-id="efbbc-249">Sélectionnez **Actions** > **Renommer le profil** pour nommer le profil.</span><span class="sxs-lookup"><span data-stu-id="efbbc-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="efbbc-250">Attribuez au profil un nom qui identifie la plateforme cible, puis sélectionnez \**Enregistrer*.</span><span class="sxs-lookup"><span data-stu-id="efbbc-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="efbbc-251">Répétez ces étapes pour définir les plateformes cibles supplémentaires ciblées par votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="efbbc-252">Vous avez configuré vos profils et êtes maintenant prêt à publier votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="efbbc-253">Pour cela :</span><span class="sxs-lookup"><span data-stu-id="efbbc-253">To do this:</span></span>

   1. <span data-ttu-id="efbbc-254">Si la fenêtre **Publier** n’est pas ouverte, cliquez avec le bouton droit sur le projet (pas la solution) dans l’**Explorateur de solutions**, puis sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="efbbc-255">Sélectionnez le profil à publier, puis sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="efbbc-256">Procédez ainsi pour chaque profil à publier.</span><span class="sxs-lookup"><span data-stu-id="efbbc-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="efbbc-257">Notez que chaque emplacement cible (dans notre exemple, bin\release\netcoreapp2.1\publish\\*nom-profil* contient l’ensemble complet des fichiers (vos fichiers d’application et tous les fichiers .NET Core).) nécessaires au lancement de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="efbbc-258">En même temps que les fichiers de votre application, le processus de publication produit un fichier de base de données du programme (.pdb) qui contient des informations de débogage sur votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="efbbc-259">Le fichier est surtout utile pour le débogage d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="efbbc-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="efbbc-260">Vous pouvez choisir de ne pas l’empaqueter avec les fichiers de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="efbbc-261">Vous devez toutefois l’enregistrer au cas où vous souhaiteriez déboguer la build Release de votre application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="efbbc-262">Déployez les fichiers publiés de la façon qui vous convient.</span><span class="sxs-lookup"><span data-stu-id="efbbc-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="efbbc-263">Par exemple, vous pouvez les empaqueter dans un fichier Zip, utiliser une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.</span><span class="sxs-lookup"><span data-stu-id="efbbc-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="efbbc-264">Voici le fichier *csproj* complet pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="efbbc-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="efbbc-265">De plus, Visual Studio crée un profil de publication distinct (\*.pubxml) pour chaque plateforme que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="efbbc-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="efbbc-266">Par exemple, le fichier de notre profil linux (linux.pubxml) se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="efbbc-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="efbbc-267">Déploiement autonome avec des dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="efbbc-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="efbbc-268">L’exécution d’un déploiement autonome avec une ou plusieurs dépendances tierces implique l’ajout des dépendances.</span><span class="sxs-lookup"><span data-stu-id="efbbc-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="efbbc-269">Avant de pouvoir générer votre application, vous devez effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="efbbc-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="efbbc-270">Utilisez le **Gestionnaire de package NuGet** pour ajouter à votre projet une référence à un package NuGet et installer le package s’il n’est pas disponible sur votre système.</span><span class="sxs-lookup"><span data-stu-id="efbbc-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="efbbc-271">Pour ouvrir le Gestionnaire de package, sélectionnez **Outils** > **Gestionnaire de package NuGet** > **Gérer les packages NuGet pour la solution**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="efbbc-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span><span class="sxs-lookup"><span data-stu-id="efbbc-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="efbbc-273">L’onglet **Installé** répertorie les packages NuGet installés sur votre système.</span><span class="sxs-lookup"><span data-stu-id="efbbc-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="efbbc-274">Si `Newtonsoft.Json` n’est pas répertorié, sélectionnez l’onglet **Parcourir** et entrez « Newtonsoft.Json » dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="efbbc-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="efbbc-275">Sélectionnez `Newtonsoft.Json` et, dans le volet droit, choisissez votre projet avant de sélectionner **Installer**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="efbbc-276">Si `Newtonsoft.Json` est déjà installé sur votre système, ajoutez-le à votre projet en sélectionnant votre projet dans le volet droit de l’onglet **Gérer les packages de la solution**.</span><span class="sxs-lookup"><span data-stu-id="efbbc-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="efbbc-277">Voici le fichier *csproj* complet pour ce projet :</span><span class="sxs-lookup"><span data-stu-id="efbbc-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="efbbc-278">Visual Studio 15.6 et versions antérieures</span><span class="sxs-lookup"><span data-stu-id="efbbc-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="efbbc-279">Visual Studio 15.7 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="efbbc-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="efbbc-280">Quand vous déployez votre application, toutes les dépendances tierces utilisées dans votre application sont également incluses avec vos fichiers d’application.</span><span class="sxs-lookup"><span data-stu-id="efbbc-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="efbbc-281">Il n’est pas nécessaire que les bibliothèques tierces soient déjà présentes sur le système sur lequel l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="efbbc-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="efbbc-282">Notez que vous pouvez déployer un déploiement autonome avec une bibliothèque tierce seulement sur des plateformes prises en charge par cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="efbbc-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="efbbc-283">Cela revient à avoir des dépendances tierces avec des dépendances natives dans votre déploiement dépendant du framework, où les dépendances natives n’existent pas sur la plateforme cible, sauf si elles y ont été installées précédemment.</span><span class="sxs-lookup"><span data-stu-id="efbbc-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="efbbc-284">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efbbc-284">See also</span></span>

- [<span data-ttu-id="efbbc-285">Déploiement d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="efbbc-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="efbbc-286">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="efbbc-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
