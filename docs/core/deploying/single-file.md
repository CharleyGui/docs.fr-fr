---
title: Application à fichier unique
description: Découvrez ce qu’est une application à fichier unique et pourquoi envisager d’utiliser ce modèle de déploiement d’application.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 795ea98a9fd9d672b199eb2d9b24151340ef8246
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495798"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="96aac-103">Déploiement et exécutable d’un seul fichier</span><span class="sxs-lookup"><span data-stu-id="96aac-103">Single file deployment and executable</span></span>

<span data-ttu-id="96aac-104">L’empaquetage de tous les fichiers dépendants de l’application dans un seul fichier binaire fournit à un développeur d’applications l’option intéressante pour déployer et distribuer l’application en tant que fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="96aac-105">Ce modèle de déploiement est disponible depuis .NET Core 3,0 et a été amélioré dans .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="96aac-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="96aac-106">Précédemment dans .NET Core 3,0, lorsqu’un utilisateur exécute votre application à fichier unique, l’hôte .NET Core extrait d’abord tous les fichiers dans un répertoire temporaire avant d’exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="96aac-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="96aac-107">.NET 5,0 améliore cette expérience en exécutant directement le code sans avoir besoin d’extraire les fichiers de l’application.</span><span class="sxs-lookup"><span data-stu-id="96aac-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="96aac-108">Le déploiement d’un seul fichier est disponible pour le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) et pour les [applications autonomes](index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="96aac-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="96aac-109">La taille du fichier unique dans une application autonome est importante, car elle inclut le runtime et les bibliothèques de Framework.</span><span class="sxs-lookup"><span data-stu-id="96aac-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="96aac-110">L’option de déploiement de fichier unique peut être combinée avec [ReadyToRun](../tools/dotnet-publish.md) et [Trim (une fonctionnalité expérimentale dans .net 5,0) options de](trim-self-contained.md) publication.</span><span class="sxs-lookup"><span data-stu-id="96aac-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

<span data-ttu-id="96aac-111">Vous devez tenir compte de certains points à prendre en compte lors de l’utilisation d’un fichier unique, qui consiste à utiliser des informations de chemin d’accès pour localiser un fichier relatif à l’emplacement de votre application.</span><span class="sxs-lookup"><span data-stu-id="96aac-111">There are some caveats that you need to be aware for single-file use, first of which is the use of path information to locate a file relative to the location of your application.</span></span> <span data-ttu-id="96aac-112">L' <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API retourne une chaîne vide, qui est le comportement par défaut pour les assemblys chargés à partir de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="96aac-112">The <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API will return an empty string, which is the default behavior for assemblies loaded from memory.</span></span> <span data-ttu-id="96aac-113">Le compilateur émet un avertissement pour cette API pendant la génération pour signaler au développeur le comportement spécifique.</span><span class="sxs-lookup"><span data-stu-id="96aac-113">The compiler will give a warning for this API during build time to alert the developer to the specific behavior.</span></span> <span data-ttu-id="96aac-114">Si le chemin d’accès au répertoire de l’application est nécessaire, l' <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API retourne le répertoire dans lequel réside le apphost (le bundle de fichier unique lui-même).</span><span class="sxs-lookup"><span data-stu-id="96aac-114">If the path to the application directory is needed, the <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API will return the directory where the AppHost (the single-file bundle itself) resides.</span></span> <span data-ttu-id="96aac-115">Les applications C++ managées ne conviennent pas au déploiement de fichier unique et nous vous recommandons d’écrire des applications en C# pour qu’elles soient compatibles avec un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="96aac-115">Managed C++ applications aren't well suited for single-file deployment and we recommend that you write applications in C# to be single-file compatible.</span></span>

<span data-ttu-id="96aac-116">Un fichier unique ne regroupe pas les bibliothèques natives par défaut.</span><span class="sxs-lookup"><span data-stu-id="96aac-116">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="96aac-117">Sur Linux, nous prévoyons le runtime dans le bundle et seules les bibliothèques natives de l’application sont déployées dans le même répertoire que l’application à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-117">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="96aac-118">Sur Windows, nous prévoyons uniquement le code d’hébergement et les bibliothèques Runtime et application natives sont déployées dans le même répertoire que l’application à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-118">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="96aac-119">Cela permet de garantir une bonne expérience de débogage, qui requiert que les fichiers natifs soient exclus du fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-119">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="96aac-120">Il existe une option pour définir un indicateur, `IncludeNativeLibrariesForSelfExtract` , pour inclure les bibliothèques natives dans le groupe de fichiers unique, mais ces fichiers seront extraits dans un répertoire temporaire de l’ordinateur client lors de l’exécution de l’application à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-120">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="96aac-121">Exclure des fichiers de l’incorporation</span><span class="sxs-lookup"><span data-stu-id="96aac-121">Exclude files from being embedded</span></span>

<span data-ttu-id="96aac-122">Certains fichiers peuvent être explicitement exclus de l’incorporation dans le fichier unique en définissant les métadonnées suivantes :</span><span class="sxs-lookup"><span data-stu-id="96aac-122">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="96aac-123">Par exemple, pour placer certains fichiers dans le répertoire de publication, mais pas les regrouper dans le fichier unique :</span><span class="sxs-lookup"><span data-stu-id="96aac-123">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="96aac-124">Publier une application à fichier unique-CLI</span><span class="sxs-lookup"><span data-stu-id="96aac-124">Publish a single file app - CLI</span></span>

<span data-ttu-id="96aac-125">Publiez une application à fichier unique à l’aide de la commande [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="96aac-125">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="96aac-126">Lorsque vous publiez votre application, définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="96aac-126">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="96aac-127">Publier pour un Runtime spécifique : `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="96aac-127">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="96aac-128">Publier en tant que fichier unique : `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="96aac-128">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="96aac-129">L’exemple suivant publie une application pour Windows sous la forme d’une application à fichier unique autonome.</span><span class="sxs-lookup"><span data-stu-id="96aac-129">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="96aac-130">L’exemple suivant publie une application pour Linux sous la forme d’une application à fichier unique dépendante de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="96aac-130">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="96aac-131">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-131">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="96aac-132">Publier une application à fichier unique-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="96aac-132">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="96aac-133">Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.</span><span class="sxs-lookup"><span data-stu-id="96aac-133">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="96aac-134">Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le projet que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="96aac-134">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="96aac-135">Sélectionnez **Publier**.</span><span class="sxs-lookup"><span data-stu-id="96aac-135">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

    <span data-ttu-id="96aac-137">Si vous ne disposez pas déjà d’un profil de publication, suivez les instructions pour en créer un et choisissez le type cible du **dossier** .</span><span class="sxs-lookup"><span data-stu-id="96aac-137">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="96aac-138">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="96aac-138">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Profil de publication Visual Studio avec le bouton modifier.":::

01. <span data-ttu-id="96aac-140">Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="96aac-140">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="96aac-141">Définissez **le** **mode de déploiement** sur autonome.</span><span class="sxs-lookup"><span data-stu-id="96aac-141">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="96aac-142">Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="96aac-142">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="96aac-143">Sélectionnez **produire un fichier unique**.</span><span class="sxs-lookup"><span data-stu-id="96aac-143">Select **Produce single file**.</span></span>

    <span data-ttu-id="96aac-144">Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .</span><span class="sxs-lookup"><span data-stu-id="96aac-144">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Boîte de dialogue Paramètres de profil avec le mode de déploiement, le runtime cible et les options à fichier unique mis en surbrillance.":::

01. <span data-ttu-id="96aac-146">Choisissez **publier** pour publier votre application en tant que fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-146">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="96aac-147">Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-147">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="96aac-148">Publier une application à fichier unique-Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="96aac-148">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="96aac-149">Visual Studio pour Mac ne fournit pas d’options permettant de publier votre application sous la forme d’un fichier unique.</span><span class="sxs-lookup"><span data-stu-id="96aac-149">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="96aac-150">Vous devez publier manuellement en suivant les instructions de la section [publication d’une application à fichier unique-CLI](#publish-a-single-file-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="96aac-150">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="96aac-151">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-151">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96aac-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96aac-152">See also</span></span>

- <span data-ttu-id="96aac-153">[Déploiement d’applications .net Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-153">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="96aac-154">[Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-154">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="96aac-155">[Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-155">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="96aac-156">[ `dotnet publish` commande](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="96aac-156">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
