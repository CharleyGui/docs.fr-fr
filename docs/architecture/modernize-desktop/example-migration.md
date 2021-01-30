---
title: Exemple de migration vers .NET 5
description: Illustrant comment migrer un exemple d’application ciblant .NET Framework vers .NET 5.
ms.date: 01/19/2021
ms.openlocfilehash: 39ecdfa639f4d68a4a8821da839f014c8de42ab0
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216263"
---
# <a name="example-of-migrating-to-net"></a><span data-ttu-id="c8e43-103">Exemple de migration vers .NET</span><span class="sxs-lookup"><span data-stu-id="c8e43-103">Example of migrating to .NET</span></span>

<span data-ttu-id="c8e43-104">Dans ce chapitre, nous présentons des recommandations pratiques pour vous aider à effectuer une migration de votre application existante de .NET Framework vers .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET.</span></span>

<span data-ttu-id="c8e43-105">Nous présentons un processus bien structuré que vous pouvez suivre et les éléments les plus importants à prendre en compte à chaque étape.</span><span class="sxs-lookup"><span data-stu-id="c8e43-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="c8e43-106">Nous documentons ensuite un processus de migration pas à pas pour un exemple d’application de bureau à partir de WinForms et des versions de WPF.</span><span class="sxs-lookup"><span data-stu-id="c8e43-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="c8e43-107">Vue d’ensemble du processus de migration</span><span class="sxs-lookup"><span data-stu-id="c8e43-107">Migration process overview</span></span>

<span data-ttu-id="c8e43-108">Le processus de migration se compose de quatre étapes séquentielles :</span><span class="sxs-lookup"><span data-stu-id="c8e43-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="c8e43-109">**Préparation**: comprenez les dépendances du projet pour avoir une idée de ce qui est avant.</span><span class="sxs-lookup"><span data-stu-id="c8e43-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="c8e43-110">Dans cette étape, vous allez passer le projet actuel dans un État qui simplifie le point de démarrage de la migration.</span><span class="sxs-lookup"><span data-stu-id="c8e43-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="c8e43-111">**Migrer un fichier projet :** les projets .NET utilisent le nouveau format de projet de style SDK.</span><span class="sxs-lookup"><span data-stu-id="c8e43-111">**Migrate Project File:** .NET projects use the new SDK-style project format.</span></span> <span data-ttu-id="c8e43-112">Créez un nouveau fichier projet avec ce format ou mettez à jour celui dont vous avez besoin pour utiliser le style du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="c8e43-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="c8e43-113">**Correction du code et de la génération :** Générez le code dans .NET en adressant les différences au niveau de l’API entre .NET Framework et .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-113">**Fix code and build:** Build the code in .NET addressing API-level differences between .NET Framework and .NET.</span></span> <span data-ttu-id="c8e43-114">Si nécessaire, mettez à jour les packages tiers avec ceux qui prennent en charge .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-114">If needed, update third-party packages to the ones that support .NET.</span></span>

4. <span data-ttu-id="c8e43-115">**Exécuter et tester :** Il peut y avoir des différences qui n’apparaissent pas jusqu’au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c8e43-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="c8e43-116">Donc, n’oubliez pas d’exécuter l’application et de tester que tout fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="c8e43-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="c8e43-117">Préparation</span><span class="sxs-lookup"><span data-stu-id="c8e43-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="c8e43-118">Migrer le fichier packages.config</span><span class="sxs-lookup"><span data-stu-id="c8e43-118">Migrate packages.config file</span></span>

<span data-ttu-id="c8e43-119">Dans une application .NET Framework, toutes les références aux packages externes sont déclarées dans le fichier *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="c8e43-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="c8e43-120">Dans .NET, il n’est plus nécessaire d’utiliser le fichier *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="c8e43-120">In .NET, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="c8e43-121">Utilisez plutôt la propriété [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) dans le fichier projet pour spécifier les packages NuGet pour votre application.</span><span class="sxs-lookup"><span data-stu-id="c8e43-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="c8e43-122">Par conséquent, vous devez passer d’un format à un autre.</span><span class="sxs-lookup"><span data-stu-id="c8e43-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="c8e43-123">Vous pouvez effectuer la mise à jour manuellement, en utilisant les dépendances contenues dans le fichier *packages.config* et en les migrant vers le fichier projet au `PackageReference` format.</span><span class="sxs-lookup"><span data-stu-id="c8e43-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="c8e43-124">Vous pouvez également laisser Visual Studio faire le travail pour vous : cliquez avec le bouton droit sur le fichier *packages.config* et sélectionnez l’option **migrer packages.config vers PackageReference** .</span><span class="sxs-lookup"><span data-stu-id="c8e43-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net"></a><span data-ttu-id="c8e43-125">Vérifier chaque compatibilité de dépendance dans .NET</span><span class="sxs-lookup"><span data-stu-id="c8e43-125">Verify every dependency compatibility in .NET</span></span>

<span data-ttu-id="c8e43-126">Une fois que vous avez migré les références du package, vous devez vérifier la compatibilité de chaque référence.</span><span class="sxs-lookup"><span data-stu-id="c8e43-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="c8e43-127">Vous pouvez explorer les dépendances de chaque package NuGet utilisé par votre application sur [NuGet.org](https://www.nuget.org/). Si le package possède des dépendances de .NET Standard, il va travailler sur .NET 5,0, car .NET [prend en charge](../../standard/net-standard.md#net-implementation-support) toutes les versions de .NET standard.</span><span class="sxs-lookup"><span data-stu-id="c8e43-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET 5.0 because .NET [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="c8e43-128">L’illustration suivante montre les dépendances du `Castle.Windsor` Package :</span><span class="sxs-lookup"><span data-stu-id="c8e43-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Capture d’écran des dépendances NuGet pour le package Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="c8e43-130">Pour vérifier la compatibilité du package, vous pouvez utiliser l’outil <https://fuget.org> qui fournit des informations plus détaillées sur les versions et les dépendances.</span><span class="sxs-lookup"><span data-stu-id="c8e43-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="c8e43-131">Le projet peut peut-être référencer des versions de package plus anciennes qui ne prennent pas en charge .NET, mais vous pouvez trouver des versions plus récentes qui le prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="c8e43-131">Maybe the project is referencing older package versions that don't support .NET, but you might find newer versions that do support it.</span></span> <span data-ttu-id="c8e43-132">Par conséquent, la mise à jour des packages vers des versions plus récentes est généralement une bonne recommandation.</span><span class="sxs-lookup"><span data-stu-id="c8e43-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="c8e43-133">Toutefois, vous devez tenir compte du fait que la mise à jour de la version du package peut entraîner des modifications avec rupture qui vous obligent à mettre à jour votre code.</span><span class="sxs-lookup"><span data-stu-id="c8e43-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="c8e43-134">Que se passe-t-il si vous ne trouvez pas de version compatible ?</span><span class="sxs-lookup"><span data-stu-id="c8e43-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="c8e43-135">Que se passe-t-il si vous ne souhaitez pas mettre à jour la version d’un package en raison de ces modifications avec rupture ?</span><span class="sxs-lookup"><span data-stu-id="c8e43-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="c8e43-136">Ne vous inquiétez pas, car il est possible de dépendre .NET Framework packages d’une application .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET application.</span></span> <span data-ttu-id="c8e43-137">N’oubliez pas de le tester de manière intensive, car cela peut provoquer des erreurs d’exécution si le package externe appelle une API qui n’est pas disponible sur .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET.</span></span> <span data-ttu-id="c8e43-138">C’est très utile lorsque vous utilisez un ancien package qui ne va pas être mis à jour et que vous pouvez simplement recibler pour travailler sur .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="c8e43-139">Vérifier la compatibilité des API</span><span class="sxs-lookup"><span data-stu-id="c8e43-139">Check for API compatibility</span></span>

<span data-ttu-id="c8e43-140">Dans la mesure où la surface de l’API dans .NET Framework et .NET est similaire, mais pas identique, vous devez vérifier les API qui sont disponibles sur .NET et celles qui ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="c8e43-140">Since the API surface in .NET Framework and .NET is similar but not identical, you must check which APIs are available on .NET and which aren't.</span></span> <span data-ttu-id="c8e43-141">Vous pouvez utiliser l’outil Analyseur de portabilité .NET pour déterminer les API utilisées qui ne sont pas présentes sur .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET.</span></span> <span data-ttu-id="c8e43-142">Il examine le niveau binaire de votre application, extrait toutes les API appelées, puis répertorie les API qui ne sont pas disponibles sur votre Framework cible (.NET 5,0 dans le cas présent).</span><span class="sxs-lookup"><span data-stu-id="c8e43-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET 5.0 in this case).</span></span>

<span data-ttu-id="c8e43-143">Vous trouverez plus d’informations sur cet outil à l’adresse suivante :</span><span class="sxs-lookup"><span data-stu-id="c8e43-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="c8e43-144">Un aspect intéressant de cet outil est qu’il ne couvre que les différences par rapport à votre propre code et non le code des packages externes, que vous ne pouvez pas modifier.</span><span class="sxs-lookup"><span data-stu-id="c8e43-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="c8e43-145">N’oubliez pas que vous devez avoir mis à jour la plupart de ces packages pour qu’ils fonctionnent avec .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-145">Remember you should have updated most of these packages to make them work with .NET.</span></span>

### <a name="migrate-with-try-convert-tool"></a><span data-ttu-id="c8e43-146">Migrer avec l’outil essayer la conversion</span><span class="sxs-lookup"><span data-stu-id="c8e43-146">Migrate with Try Convert tool</span></span>

<span data-ttu-id="c8e43-147">L’outil [essayer Convert](https://github.com/dotnet/try-convert/releases) est un excellent moyen de migrer un projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-147">The [Try Convert](https://github.com/dotnet/try-convert/releases) tool is a great way to migrate a project.</span></span> <span data-ttu-id="c8e43-148">Il s’agit d’un outil global qui tente de mettre à niveau votre fichier projet de l’ancien style vers le nouveau style du kit de développement logiciel (SDK) et recible les projets applicables vers .NET 5.</span><span class="sxs-lookup"><span data-stu-id="c8e43-148">It's a global tool that attempts to upgrade your project file from the old style to the new SDK style, and retargets applicable projects to .NET 5.</span></span> <span data-ttu-id="c8e43-149">Une fois l’installation terminée, vous pouvez exécuter les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c8e43-149">Once installed, you can run the following commands:</span></span>

```dotnetcli
try-convert -p "<path to your project file>"
```

<span data-ttu-id="c8e43-150">Ou :</span><span class="sxs-lookup"><span data-stu-id="c8e43-150">Or:</span></span>

```dotnetcli
try-convert -w "<path to your solution>"
```

<span data-ttu-id="c8e43-151">Une fois que l’outil a tenté la conversion, rechargez vos fichiers dans Visual Studio pour exécuter et tester.</span><span class="sxs-lookup"><span data-stu-id="c8e43-151">After the tool attempts the conversion, reload your files in Visual Studio to run and test.</span></span> <span data-ttu-id="c8e43-152">Il est possible que la conversion try ne puisse pas effectuer la conversion en raison des spécificités de votre projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-152">There's a possibility that Try Convert won't be able to perform the conversion due to the specifics of your project.</span></span> <span data-ttu-id="c8e43-153">Dans ce cas, vous pouvez consulter les étapes ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c8e43-153">In that case, you can refer the below steps.</span></span>

#### <a name="migrate-manually"></a><span data-ttu-id="c8e43-154">Migrer manuellement</span><span class="sxs-lookup"><span data-stu-id="c8e43-154">Migrate manually</span></span>

1. <span data-ttu-id="c8e43-155">Créer le nouveau projet .NET</span><span class="sxs-lookup"><span data-stu-id="c8e43-155">Create the new .NET project</span></span>

<span data-ttu-id="c8e43-156">Dans la plupart des cas, vous souhaiterez mettre à jour votre projet existant vers le nouveau format .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-156">In most cases, you'll want to update your existing project to the new .NET format.</span></span> <span data-ttu-id="c8e43-157">Toutefois, vous pouvez également créer un nouveau projet tout en conservant l’ancien.</span><span class="sxs-lookup"><span data-stu-id="c8e43-157">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="c8e43-158">Le principal inconvénient de la mise à jour de l’ancien projet est que vous perdez la prise en charge du concepteur, ce qui peut être important pour vous et votre équipe de développement.</span><span class="sxs-lookup"><span data-stu-id="c8e43-158">The main drawback from updating the old project is that you lose designer support, which may be important to you and your development team.</span></span> <span data-ttu-id="c8e43-159">Si vous souhaitez continuer à utiliser le concepteur, vous devez créer un nouveau projet .NET en parallèle avec l’ancien et partager les ressources.</span><span class="sxs-lookup"><span data-stu-id="c8e43-159">If you want to keep using the designer, you must create a new .NET project in parallel with the old one and share assets.</span></span> <span data-ttu-id="c8e43-160">Si vous avez besoin de modifier des éléments d’interface utilisateur dans le concepteur, vous pouvez basculer vers l’ancien projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-160">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="c8e43-161">Et étant donné que les ressources sont liées, elles sont également mises à jour dans le projet .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-161">And since assets are linked, they'll be updated in the .NET project as well.</span></span>

<span data-ttu-id="c8e43-162">Le [projet de type SDK](../../core/project-sdk/msbuild-props.md) pour .net est beaucoup plus simple que le format de projet de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8e43-162">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="c8e43-163">Outre les entrées mentionnées précédemment `PackageReference` , vous n’avez pas besoin d’en faire plus.</span><span class="sxs-lookup"><span data-stu-id="c8e43-163">Apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="c8e43-164">Le nouveau format de projet [inclut des fichiers avec certaines extensions par défaut](../../core/project-sdk/overview.md#default-includes-and-excludes), tels que les `.cs` `.xaml` fichiers et, sans qu’il soit nécessaire de les inclure explicitement dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-164">The new project format [includes files with certain extensions by default](../../core/project-sdk/overview.md#default-includes-and-excludes), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="c8e43-165">Considérations relatives à AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="c8e43-165">AssemblyInfo considerations</span></span>

<span data-ttu-id="c8e43-166">Les attributs sont générés automatiquement dans les projets .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-166">Attributes are autogenerated on .NET projects.</span></span> <span data-ttu-id="c8e43-167">Si le projet contient un fichier *AssemblyInfo.cs* , les définitions sont dupliquées, ce qui entraîne des conflits de compilation.</span><span class="sxs-lookup"><span data-stu-id="c8e43-167">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="c8e43-168">Vous pouvez supprimer l’ancien fichier *AssemblyInfo.cs* ou désactiver la génération en ajoutant l’entrée suivante dans le fichier de projet .net :</span><span class="sxs-lookup"><span data-stu-id="c8e43-168">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="c8e43-169">Ressources</span><span class="sxs-lookup"><span data-stu-id="c8e43-169">Resources</span></span>

<span data-ttu-id="c8e43-170">Les ressources incorporées sont automatiquement incluses, mais les ressources ne le sont pas. vous devez donc migrer les ressources vers le nouveau fichier projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-170">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="c8e43-171">Références de package</span><span class="sxs-lookup"><span data-stu-id="c8e43-171">Package references</span></span>

<span data-ttu-id="c8e43-172">Avec l’option **migrer packages.config vers PackageReference** , vous pouvez facilement déplacer vos références de package externes vers le nouveau format mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="c8e43-172">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="c8e43-173">Mettre à jour les références de package</span><span class="sxs-lookup"><span data-stu-id="c8e43-173">Update package references</span></span>

<span data-ttu-id="c8e43-174">Mettez à jour les versions des packages que vous avez détectés comme étant compatibles, comme indiqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="c8e43-174">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="c8e43-175">Corriger le code et générer</span><span class="sxs-lookup"><span data-stu-id="c8e43-175">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="c8e43-176">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="c8e43-176">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="c8e43-177">Si votre application dépend d’API qui ne sont pas disponibles sur .NET, telles que le registre, les ACL ou WCF, vous devez inclure une référence au `Microsoft.Windows.Compatibility` package pour ajouter ces API spécifiques à Windows.</span><span class="sxs-lookup"><span data-stu-id="c8e43-177">If your application depends on APIs that aren't available on .NET, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="c8e43-178">Ils fonctionnent sur .NET mais ne sont pas inclus, car ils ne sont pas interplateformes.</span><span class="sxs-lookup"><span data-stu-id="c8e43-178">They work on .NET but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="c8e43-179">Il existe un outil appelé analyseur d’API ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ) qui vous aide à identifier les API qui ne sont pas compatibles avec votre code.</span><span class="sxs-lookup"><span data-stu-id="c8e43-179">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="c8e43-180">Utiliser des \# directives if</span><span class="sxs-lookup"><span data-stu-id="c8e43-180">Use \#if directives</span></span>

<span data-ttu-id="c8e43-181">Si vous avez besoin de chemins d’exécution différents pour cibler .NET Framework et .NET, vous devez utiliser des constantes de compilation.</span><span class="sxs-lookup"><span data-stu-id="c8e43-181">If you need different execution paths when targeting .NET Framework and .NET, you should use compilation constants.</span></span> <span data-ttu-id="c8e43-182">Ajoutez des \# directives if à votre code pour conserver la même base de code pour les deux cibles.</span><span class="sxs-lookup"><span data-stu-id="c8e43-182">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net"></a><span data-ttu-id="c8e43-183">Technologies non disponibles sur .NET</span><span class="sxs-lookup"><span data-stu-id="c8e43-183">Technologies not available on .NET</span></span>

<span data-ttu-id="c8e43-184">Certaines technologies ne sont pas disponibles sur .NET, telles que :</span><span class="sxs-lookup"><span data-stu-id="c8e43-184">Some technologies aren't available on .NET, such as:</span></span>

* <span data-ttu-id="c8e43-185">AppDomains</span><span class="sxs-lookup"><span data-stu-id="c8e43-185">AppDomains</span></span>
* <span data-ttu-id="c8e43-186">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="c8e43-186">Remoting</span></span>
* <span data-ttu-id="c8e43-187">Sécurité d'accès du code</span><span class="sxs-lookup"><span data-stu-id="c8e43-187">Code Access Security</span></span>
* <span data-ttu-id="c8e43-188">Serveur WCF</span><span class="sxs-lookup"><span data-stu-id="c8e43-188">WCF Server</span></span>
* <span data-ttu-id="c8e43-189">Flux de travail Windows</span><span class="sxs-lookup"><span data-stu-id="c8e43-189">Windows Workflow</span></span>

<span data-ttu-id="c8e43-190">C’est la raison pour laquelle vous devez remplacer ces technologies si vous les utilisez dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c8e43-190">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="c8e43-191">Pour plus d’informations, consultez l’article [.NET Framework technologies indisponibles sur .net Core et .net 5 +](../../core/porting/net-framework-tech-unavailable.md) .</span><span class="sxs-lookup"><span data-stu-id="c8e43-191">For more information, see the [.NET Framework technologies unavailable on .NET Core and .NET 5+](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="c8e43-192">Régénérer les clients générés automatiquement</span><span class="sxs-lookup"><span data-stu-id="c8e43-192">Regenerate autogenerated clients</span></span>

<span data-ttu-id="c8e43-193">Si votre application utilise du code généré automatiquement, tel qu’un client WCF, vous devrez peut-être régénérer ce code pour cibler .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-193">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET.</span></span> <span data-ttu-id="c8e43-194">Parfois, vous pouvez trouver des références manquantes, car elles ne sont pas incluses dans le jeu d’assemblys .NET par défaut.</span><span class="sxs-lookup"><span data-stu-id="c8e43-194">Sometimes, you can find some missing references since they may not be included as part of the default .NET assemblies set.</span></span> <span data-ttu-id="c8e43-195">À l’aide d’un outil tel que <https://apisof.net/> , vous pouvez facilement localiser l’assembly dans lequel réside la référence manquante, puis l’ajouter à partir de NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-195">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="c8e43-196">Restauration de versions de package</span><span class="sxs-lookup"><span data-stu-id="c8e43-196">Rolling back package versions</span></span>

<span data-ttu-id="c8e43-197">En règle générale, nous avons indiqué précédemment que vous souhaitez mieux mettre à jour chaque version de package pour qu’elle soit compatible avec .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-197">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET.</span></span> <span data-ttu-id="c8e43-198">Toutefois, vous pouvez constater que le ciblage d’une version mise à jour et compatible d’un assembly n’est pas payant.</span><span class="sxs-lookup"><span data-stu-id="c8e43-198">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="c8e43-199">Si le coût de la modification n’est pas acceptable, vous pouvez envisager de restaurer les versions des packages en gardant celles que vous utilisez sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8e43-199">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="c8e43-200">Bien qu’ils ne ciblent pas .NET, ils doivent fonctionner correctement sauf s’ils appellent des API non prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c8e43-200">Although they may not be targeting .NET, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="c8e43-201">Exécuter et tester</span><span class="sxs-lookup"><span data-stu-id="c8e43-201">Run and test</span></span>

<span data-ttu-id="c8e43-202">Une fois que votre application est en cours d’élaboration sans erreur, vous pouvez démarrer la dernière étape de la migration en testant chaque fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="c8e43-202">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="c8e43-203">Dans cette étape finale, vous trouverez plusieurs problèmes différents selon la complexité de votre application et les dépendances et les API que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="c8e43-203">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="c8e43-204">Par exemple, si vous utilisez des fichiers de configuration (*app.config*), vous risquez de rencontrer des erreurs au moment de l’exécution, comme des sections de configuration absentes.</span><span class="sxs-lookup"><span data-stu-id="c8e43-204">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="c8e43-205">L’utilisation du `Microsoft.Extensions.Configuration` package NuGet doit corriger cette erreur.</span><span class="sxs-lookup"><span data-stu-id="c8e43-205">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="c8e43-206">Une autre raison pour les erreurs est l’utilisation `BeginInvoke` des `EndInvoke` méthodes et, car elles ne sont pas prises en charge sur .net.</span><span class="sxs-lookup"><span data-stu-id="c8e43-206">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET.</span></span> <span data-ttu-id="c8e43-207">Ils ne sont pas pris en charge sur .NET, car ils ont une dépendance vis-à-vis de la communication à distance, qui n’existe pas sur .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-207">They aren't supported on .NET because they have a dependency on Remoting, which doesn't exist on .NET.</span></span> <span data-ttu-id="c8e43-208">Pour résoudre ce problème, essayez d’utiliser le `await` mot clé (si disponible) ou la <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="c8e43-208">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c8e43-209">Vous pouvez utiliser des analyseurs de compatibilité pour vous permettre d’identifier les API et les modèles de code dans votre code qui peuvent potentiellement provoquer des problèmes au moment de l’exécution avec .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-209">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET.</span></span> <span data-ttu-id="c8e43-210">Accédez à <https://github.com/dotnet/platform-compat> et utilisez l’analyseur d’API .net sur votre projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-210">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="c8e43-211">Migration d’une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8e43-211">Migrating a Windows Forms application</span></span>

<span data-ttu-id="c8e43-212">Pour illustrer le processus de migration complet d’une application Windows Forms, nous avons choisi de migrer l’exemple d’application eShop disponible à l’adresse <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="c8e43-212">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="c8e43-213">Vous pouvez trouver le résultat final de la migration à l’adresse <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="c8e43-213">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="c8e43-214">Cette application affiche un catalogue de produits et permet à l’utilisateur de naviguer, de filtrer et de rechercher des produits.</span><span class="sxs-lookup"><span data-stu-id="c8e43-214">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="c8e43-215">Du point de vue de l’architecture, l’application s’appuie sur un service WCF externe qui sert de façade à une base de données principale.</span><span class="sxs-lookup"><span data-stu-id="c8e43-215">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="c8e43-216">Vous pouvez voir la fenêtre principale de l’application dans l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="c8e43-216">You can see the main application window in the following picture:</span></span>

![Fenêtre d’application principale](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="c8e43-218">Si vous ouvrez le fichier de projet *. csproj* , vous pouvez voir ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c8e43-218">If you open the *.csproj* project file, you can see something like this:</span></span>

![Capture d’écran du contenu du fichier csproj](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="c8e43-220">Comme mentionné précédemment, le projet .NET a un style plus compact et vous devez migrer la structure du projet vers le nouveau style du kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-220">As previously mentioned, .NET project has a more compact style and you need to migrate the project structure to the new .NET SDK style.</span></span>

<span data-ttu-id="c8e43-221">Dans le Explorateur de solutions, cliquez avec le bouton droit sur le projet Windows Forms et sélectionnez **décharger le projet**  >  **modifier**.</span><span class="sxs-lookup"><span data-stu-id="c8e43-221">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="c8e43-222">Vous pouvez maintenant mettre à jour le fichier. csproj.</span><span class="sxs-lookup"><span data-stu-id="c8e43-222">Now you can update the .csproj file.</span></span> <span data-ttu-id="c8e43-223">Vous allez supprimer tout le contenu et le remplacer par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c8e43-223">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c8e43-224">Enregistrez et rechargez le projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-224">Save and reload the project.</span></span> <span data-ttu-id="c8e43-225">Vous avez maintenant terminé la mise à jour du fichier projet et le projet cible le .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-225">You're now done updating the project file and the project is targeting the .NET.</span></span>

<span data-ttu-id="c8e43-226">Si vous compilez le projet à ce stade, vous trouverez des erreurs liées à la référence du client WCF.</span><span class="sxs-lookup"><span data-stu-id="c8e43-226">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="c8e43-227">Étant donné que ce code est généré automatiquement, vous devez le régénérer pour cibler .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-227">Since this code is autogenerated, you must regenerate it to target .NET.</span></span>

![Capture d’écran des erreurs de compilation dans Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="c8e43-229">Supprimez le fichier *Reference.cs* et générez un nouveau client de service.</span><span class="sxs-lookup"><span data-stu-id="c8e43-229">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="c8e43-230">Cliquez avec le bouton droit sur **services connectés** , puis sélectionnez l’option **Ajouter un service connecté** .</span><span class="sxs-lookup"><span data-stu-id="c8e43-230">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Capture d’écran du menu Services connectés avec l’option Ajouter un service connecté sélectionnée](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="c8e43-232">La fenêtre Services connectés s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="c8e43-232">The Connected Services window opens.</span></span> <span data-ttu-id="c8e43-233">Sélectionnez l’option **service Web Microsoft WCF** .</span><span class="sxs-lookup"><span data-stu-id="c8e43-233">Select the **Microsoft WCF Web Service** option.</span></span>

![Capture d’écran de la fenêtre Services connectés](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="c8e43-235">Si vous avez le service WCF dans la même solution que dans cet exemple, vous pouvez sélectionner l’option **Discover** au lieu de spécifier une URL de service.</span><span class="sxs-lookup"><span data-stu-id="c8e43-235">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![Capture d’écran de la fenêtre Configurer la référence de service Web WCF](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="c8e43-237">Une fois le service localisé, l’outil reflète le contrat d’API implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="c8e43-237">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="c8e43-238">Modifiez le nom de l’espace de noms `eShopServiceReference` comme indiqué dans l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="c8e43-238">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![Capture d’écran du contrat d’API et de l’espace de noms modifié](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="c8e43-240">Sélectionnez le bouton **Terminer** .</span><span class="sxs-lookup"><span data-stu-id="c8e43-240">Select the **Finish** button.</span></span> <span data-ttu-id="c8e43-241">Après un certain temps, vous verrez le code généré.</span><span class="sxs-lookup"><span data-stu-id="c8e43-241">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="c8e43-242">Vous devez voir trois fichiers générés automatiquement :</span><span class="sxs-lookup"><span data-stu-id="c8e43-242">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="c8e43-243">*Prise en main*: lien vers GitHub pour fournir des informations sur WCF.</span><span class="sxs-lookup"><span data-stu-id="c8e43-243">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="c8e43-244">*ConnectedService.jssur*: paramètres de configuration pour la connexion au service.</span><span class="sxs-lookup"><span data-stu-id="c8e43-244">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="c8e43-245">*Reference.cs*: code du client WCF réel.</span><span class="sxs-lookup"><span data-stu-id="c8e43-245">*Reference.cs*: the actual WCF client code.</span></span>

![Capture d’écran de la fenêtre de Explorateur de solutions avec les trois fichiers générés automatiquement](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="c8e43-247">Si vous recompilez, vous verrez de nombreuses erreurs provenant des fichiers *. cs* dans le dossier *d’assistance* .</span><span class="sxs-lookup"><span data-stu-id="c8e43-247">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="c8e43-248">Ce dossier était présent dans la version de .NET Framework, mais il n’est pas inclus dans l’ancien *. csproj*.</span><span class="sxs-lookup"><span data-stu-id="c8e43-248">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="c8e43-249">Mais avec le nouveau projet de type SDK, chaque fichier de code présent sous l’emplacement du fichier projet est inclus par défaut.</span><span class="sxs-lookup"><span data-stu-id="c8e43-249">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="c8e43-250">Autrement dit, le nouveau projet .NET Core tente de compiler les fichiers dans le dossier *d’assistance* .</span><span class="sxs-lookup"><span data-stu-id="c8e43-250">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="c8e43-251">Étant donné que ce dossier n’est pas nécessaire, vous pouvez le supprimer en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="c8e43-251">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="c8e43-252">Si vous compilez à nouveau le projet et que vous l’exécutez, vous ne verrez pas les images du produit.</span><span class="sxs-lookup"><span data-stu-id="c8e43-252">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="c8e43-253">Le problème vient du fait que le chemin d’accès aux fichiers a été légèrement modifié.</span><span class="sxs-lookup"><span data-stu-id="c8e43-253">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="c8e43-254">Pour résoudre ce problème, vous devez ajouter un autre niveau de profondeur dans le chemin d’accès, en mettant à jour la ligne dans le fichier `CatalogView.cs` :</span><span class="sxs-lookup"><span data-stu-id="c8e43-254">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="c8e43-255">par</span><span class="sxs-lookup"><span data-stu-id="c8e43-255">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="c8e43-256">Après cette modification, vous pouvez vérifier que l’application est lancée et s’exécute comme prévu sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c8e43-256">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="c8e43-257">Migration d’une application WPF</span><span class="sxs-lookup"><span data-stu-id="c8e43-257">Migrating a WPF application</span></span>

<span data-ttu-id="c8e43-258">Nous allons utiliser l' `Shop.ClassicWPF` exemple d’application pour effectuer la migration.</span><span class="sxs-lookup"><span data-stu-id="c8e43-258">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="c8e43-259">L’illustration suivante montre une capture d’écran de l’application avant la migration :</span><span class="sxs-lookup"><span data-stu-id="c8e43-259">The following image shows a screenshot of the app before migration:</span></span>

![Exemple d’application avant la migration](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="c8e43-261">Cette application utilise une base de données SQL Server Express locale pour contenir les informations du catalogue de produits.</span><span class="sxs-lookup"><span data-stu-id="c8e43-261">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="c8e43-262">Cette base de données est accessible directement à partir de l’application WPF.</span><span class="sxs-lookup"><span data-stu-id="c8e43-262">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="c8e43-263">Tout d’abord, vous devez mettre à jour le fichier *. csproj* avec le nouveau style de kit de développement logiciel (SDK) utilisé par les applications .net core.</span><span class="sxs-lookup"><span data-stu-id="c8e43-263">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="c8e43-264">Suivez les mêmes étapes que celles décrites dans la Windows Forms migration : vous déchargez le projet, ouvrez le fichier *. csproj* , mettez à jour son contenu, puis rechargez le projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-264">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="c8e43-265">Dans ce cas, supprimez tout le contenu du fichier *. csproj* et remplacez-le par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c8e43-265">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c8e43-266">Si vous rechargez le projet et le compilez, vous obtiendrez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="c8e43-266">If you reload the project and compile it, you'll get the following error:</span></span>

![Capture d’écran des erreurs de compilation dans Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="c8e43-268">Étant donné que vous avez supprimé tout le contenu *. csproj* , vous avez perdu une spécification de référence de projet présente dans l’ancien projet.</span><span class="sxs-lookup"><span data-stu-id="c8e43-268">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="c8e43-269">Vous devez simplement ajouter cette ligne au fichier *. csproj* pour inclure la référence du projet :</span><span class="sxs-lookup"><span data-stu-id="c8e43-269">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="c8e43-270">Vous pouvez également laisser Visual Studio vous aider en cliquant avec le bouton droit sur le nœud **dépendances** et en sélectionnant **Ajouter une référence de projet**.</span><span class="sxs-lookup"><span data-stu-id="c8e43-270">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="c8e43-271">Sélectionnez le projet dans la solution, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="c8e43-271">Select the project from the solution and click **OK**:</span></span>

![Capture d’écran de la boîte de dialogue Gestionnaire de références avec le projet eShop. SqlProvider sélectionné](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="c8e43-273">Une fois que vous avez ajouté la référence de projet manquante, l’application se compile et s’exécute comme prévu sur .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e43-273">Once you add the missing project reference, the application compiles and runs as expected on .NET.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8e43-274">[Précédent](windows-migration.md) 
> [Suivant](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="c8e43-274">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
