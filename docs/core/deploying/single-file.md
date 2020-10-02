---
title: Application à fichier unique
description: Découvrez ce qu’est une application à fichier unique et pourquoi envisager d’utiliser ce modèle de déploiement d’application.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: b7693d6c119d00a798ef03ed1019f2f04c1828cf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654650"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="9acd1-103">Déploiement et exécutable d’un seul fichier</span><span class="sxs-lookup"><span data-stu-id="9acd1-103">Single file deployment and executable</span></span>

<span data-ttu-id="9acd1-104">L’empaquetage de tous les fichiers dépendants de l’application dans un seul fichier binaire fournit à un développeur d’applications l’option intéressante pour déployer et distribuer l’application en tant que fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="9acd1-105">Ce modèle de déploiement est disponible depuis .NET Core 3,0 et a été amélioré dans .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="9acd1-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="9acd1-106">Précédemment dans .NET Core 3,0, lorsqu’un utilisateur exécute votre application à fichier unique, l’hôte .NET Core extrait d’abord tous les fichiers dans un répertoire temporaire avant d’exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="9acd1-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="9acd1-107">.NET 5,0 améliore cette expérience en exécutant directement le code sans avoir besoin d’extraire les fichiers de l’application.</span><span class="sxs-lookup"><span data-stu-id="9acd1-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="9acd1-108">Le déploiement d’un seul fichier est disponible pour le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) et pour les [applications autonomes](index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="9acd1-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="9acd1-109">La taille du fichier unique dans une application autonome est importante, car elle inclut le runtime et les bibliothèques de Framework.</span><span class="sxs-lookup"><span data-stu-id="9acd1-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="9acd1-110">L’option de déploiement de fichier unique peut être combinée avec [ReadyToRun](../tools/dotnet-publish.md) et [Trim (une fonctionnalité expérimentale dans .net 5,0) options de](trim-self-contained.md) publication.</span><span class="sxs-lookup"><span data-stu-id="9acd1-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="9acd1-111">Incompatibilité d’API</span><span class="sxs-lookup"><span data-stu-id="9acd1-111">API incompatibility</span></span>

<span data-ttu-id="9acd1-112">Certaines API ne sont pas compatibles avec le déploiement à fichier unique et les applications peuvent nécessiter une modification si elles utilisent ces API.</span><span class="sxs-lookup"><span data-stu-id="9acd1-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="9acd1-113">Si vous utilisez un Framework ou un package tiers, il est possible qu’ils puissent également utiliser l’une de ces API et qu’il soit nécessaire de les modifier.</span><span class="sxs-lookup"><span data-stu-id="9acd1-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="9acd1-114">La cause la plus courante de problèmes dépend des chemins d’accès aux fichiers ou dll livrés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="9acd1-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="9acd1-115">Le tableau ci-dessous contient les détails de l’API de la bibliothèque Runtime appropriée pour une utilisation à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="9acd1-116">API</span><span class="sxs-lookup"><span data-stu-id="9acd1-116">API</span></span>                            | <span data-ttu-id="9acd1-117">Notes</span><span class="sxs-lookup"><span data-stu-id="9acd1-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="9acd1-118">Retourne une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="9acd1-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="9acd1-119">Retourne une chaîne avec la valeur de `<Unknown>` ou lève une exception.</span><span class="sxs-lookup"><span data-stu-id="9acd1-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="9acd1-120">Retourne une chaîne avec la valeur de `<Unknown>` .</span><span class="sxs-lookup"><span data-stu-id="9acd1-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="9acd1-121">Lève <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="9acd1-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="9acd1-122">Lève <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="9acd1-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="9acd1-123">Lève <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="9acd1-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="9acd1-124">Lève <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="9acd1-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="9acd1-125">Retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="9acd1-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="9acd1-126">Retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="9acd1-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="9acd1-127">Nous avons des recommandations pour la résolution des scénarios courants :</span><span class="sxs-lookup"><span data-stu-id="9acd1-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="9acd1-128">Pour accéder aux fichiers à côté de l’exécutable, utilisez <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9acd1-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="9acd1-129">Pour rechercher le nom de fichier de l’exécutable, utilisez le premier élément de <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9acd1-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="9acd1-130">Pour éviter d’expédier entièrement des fichiers libres, envisagez d’utiliser des [ressources incorporées](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-130">To avoid shipping loose files entirely, consider using [embedded resources](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span></span>

## <a name="other-considerations"></a><span data-ttu-id="9acd1-131">Autres considérations</span><span class="sxs-lookup"><span data-stu-id="9acd1-131">Other considerations</span></span>

<span data-ttu-id="9acd1-132">Un fichier unique ne regroupe pas les bibliothèques natives par défaut.</span><span class="sxs-lookup"><span data-stu-id="9acd1-132">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="9acd1-133">Sur Linux, nous prévoyons le runtime dans le bundle et seules les bibliothèques natives de l’application sont déployées dans le même répertoire que l’application à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-133">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="9acd1-134">Sur Windows, nous prévoyons uniquement le code d’hébergement et les bibliothèques Runtime et application natives sont déployées dans le même répertoire que l’application à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-134">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="9acd1-135">Cela permet de garantir une bonne expérience de débogage, qui requiert que les fichiers natifs soient exclus du fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-135">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="9acd1-136">Il existe une option pour définir un indicateur, `IncludeNativeLibrariesForSelfExtract` , pour inclure les bibliothèques natives dans le groupe de fichiers unique, mais ces fichiers seront extraits dans un répertoire temporaire de l’ordinateur client lors de l’exécution de l’application à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-136">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="9acd1-137">Une application à fichier unique aura tous les fichiers PDB associés et ne sera pas regroupée par défaut.</span><span class="sxs-lookup"><span data-stu-id="9acd1-137">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="9acd1-138">Si vous souhaitez inclure des fichiers PDB à l’intérieur de l’assembly pour les projets que vous générez, affectez la valeur `DebugType` `embedded` décrite [ci-dessous](#include-pdb-files-inside-the-bundle) en détail.</span><span class="sxs-lookup"><span data-stu-id="9acd1-138">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="9acd1-139">Les composants C++ managés ne sont pas adaptés au déploiement à fichier unique et nous vous recommandons d’écrire des applications en C# ou un autre langage C++ non managé pour qu’ils soient compatibles avec un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="9acd1-139">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="9acd1-140">Exclure des fichiers de l’incorporation</span><span class="sxs-lookup"><span data-stu-id="9acd1-140">Exclude files from being embedded</span></span>

<span data-ttu-id="9acd1-141">Certains fichiers peuvent être explicitement exclus de l’incorporation dans le fichier unique en définissant les métadonnées suivantes :</span><span class="sxs-lookup"><span data-stu-id="9acd1-141">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="9acd1-142">Par exemple, pour placer certains fichiers dans le répertoire de publication, mais pas les regrouper dans le fichier unique :</span><span class="sxs-lookup"><span data-stu-id="9acd1-142">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="9acd1-143">Inclure des fichiers PDB dans le bundle</span><span class="sxs-lookup"><span data-stu-id="9acd1-143">Include PDB files inside the bundle</span></span>

<span data-ttu-id="9acd1-144">Le fichier PDB d’un assembly peut être incorporé dans l’assembly lui-même (le `.dll` ) à l’aide du paramètre ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9acd1-144">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="9acd1-145">Étant donné que les symboles font partie de l’assembly, ils feront également partie de l’application à fichier unique :</span><span class="sxs-lookup"><span data-stu-id="9acd1-145">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="9acd1-146">Par exemple, ajoutez la propriété suivante au fichier projet d’un assembly pour incorporer le fichier PDB à cet assembly :</span><span class="sxs-lookup"><span data-stu-id="9acd1-146">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="9acd1-147">Publier une application à fichier unique-CLI</span><span class="sxs-lookup"><span data-stu-id="9acd1-147">Publish a single file app - CLI</span></span>

<span data-ttu-id="9acd1-148">Publiez une application à fichier unique à l’aide de la commande [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="9acd1-148">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="9acd1-149">Lorsque vous publiez votre application, définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="9acd1-149">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="9acd1-150">Publier pour un Runtime spécifique : `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="9acd1-150">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="9acd1-151">Publier en tant que fichier unique : `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="9acd1-151">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="9acd1-152">L’exemple suivant publie une application pour Windows sous la forme d’une application à fichier unique autonome.</span><span class="sxs-lookup"><span data-stu-id="9acd1-152">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="9acd1-153">L’exemple suivant publie une application pour Linux sous la forme d’une application à fichier unique dépendante de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="9acd1-153">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="9acd1-154">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-154">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="9acd1-155">Publier une application à fichier unique-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9acd1-155">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="9acd1-156">Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.</span><span class="sxs-lookup"><span data-stu-id="9acd1-156">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="9acd1-157">Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le projet que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="9acd1-157">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="9acd1-158">Sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="9acd1-158">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

    <span data-ttu-id="9acd1-160">Si vous ne disposez pas déjà d’un profil de publication, suivez les instructions pour en créer un et choisissez le type cible du **dossier** .</span><span class="sxs-lookup"><span data-stu-id="9acd1-160">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="9acd1-161">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="9acd1-161">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

01. <span data-ttu-id="9acd1-163">Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="9acd1-163">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="9acd1-164">Définissez **le** **mode de déploiement** sur autonome.</span><span class="sxs-lookup"><span data-stu-id="9acd1-164">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="9acd1-165">Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="9acd1-165">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="9acd1-166">Sélectionnez **produire un fichier unique**.</span><span class="sxs-lookup"><span data-stu-id="9acd1-166">Select **Produce single file**.</span></span>

    <span data-ttu-id="9acd1-167">Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .</span><span class="sxs-lookup"><span data-stu-id="9acd1-167">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

01. <span data-ttu-id="9acd1-169">Choisissez **publier** pour publier votre application en tant que fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-169">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="9acd1-170">Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-170">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="9acd1-171">Publier une application à fichier unique-Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="9acd1-171">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="9acd1-172">Visual Studio pour Mac ne fournit pas d’options permettant de publier votre application sous la forme d’un fichier unique.</span><span class="sxs-lookup"><span data-stu-id="9acd1-172">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="9acd1-173">Vous devez publier manuellement en suivant les instructions de la section [publication d’une application à fichier unique-CLI](#publish-a-single-file-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="9acd1-173">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="9acd1-174">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-174">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9acd1-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9acd1-175">See also</span></span>

- <span data-ttu-id="9acd1-176">[Déploiement d’applications .net Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-176">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="9acd1-177">[Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-177">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="9acd1-178">[Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-178">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="9acd1-179">[ `dotnet publish` commande](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="9acd1-179">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
