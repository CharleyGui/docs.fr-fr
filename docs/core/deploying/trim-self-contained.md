---
title: Couper les applications autonomes
description: Apprenez à couper les applications autonomes pour réduire leur taille. .NET Core regroupe l’heure d’exécution avec une application qui est publiée autonome et inclut généralement plus de l’exécution alors est nécessaire.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242904"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="565fd-104">Supprimer les exécutables et les déploiements autonomes</span><span class="sxs-lookup"><span data-stu-id="565fd-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="565fd-105">Lors de la publication d’une application autonome, le temps d’exécution .NET Core est regroupé avec l’application.</span><span class="sxs-lookup"><span data-stu-id="565fd-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="565fd-106">Ce regroupement ajoute une quantité importante de contenu à votre application emballée.</span><span class="sxs-lookup"><span data-stu-id="565fd-106">This bundling adds a significant amount of content to your packaged application.</span></span> <span data-ttu-id="565fd-107">Lorsqu’il s’agit de déployer votre application, la taille est souvent un facteur important.</span><span class="sxs-lookup"><span data-stu-id="565fd-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="565fd-108">Garder la taille de l’application de paquet aussi petite que possible est généralement un objectif pour les développeurs d’applications.</span><span class="sxs-lookup"><span data-stu-id="565fd-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="565fd-109">Selon la complexité de l’application, seul un sous-ensemble de l’exécution est nécessaire pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="565fd-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="565fd-110">Ces parties inutilisées du temps d’exécution ne sont pas nécessaires et peuvent être extraites de l’application emballée.</span><span class="sxs-lookup"><span data-stu-id="565fd-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="565fd-111">La fonction de coupe fonctionne en examinant les binaires d’application pour découvrir et construire un graphique des assemblages de temps d’exécution requis.</span><span class="sxs-lookup"><span data-stu-id="565fd-111">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="565fd-112">Les assemblages restants qui ne sont pas référencés sont exclus.</span><span class="sxs-lookup"><span data-stu-id="565fd-112">The remaining runtime assemblies that aren't referenced are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="565fd-113">Le rognage est une fonctionnalité expérimentale dans .NET Core 3.1 et _n’est_ disponible que pour les applications qui sont publiées autonomes.</span><span class="sxs-lookup"><span data-stu-id="565fd-113">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="565fd-114">Empêcher les assemblages d’être coupés</span><span class="sxs-lookup"><span data-stu-id="565fd-114">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="565fd-115">Il existe des scénarios dans lesquels la fonctionnalité de coupe ne détectera pas les références.</span><span class="sxs-lookup"><span data-stu-id="565fd-115">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="565fd-116">Par exemple, lorsque la réflexion est utilisée sur un assemblage en temps d’exécution, soit par votre application, soit par une bibliothèque référencée par votre application, l’assemblage n’est pas directement référencé.</span><span class="sxs-lookup"><span data-stu-id="565fd-116">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="565fd-117">Le rognage n’est pas au courant de ces références indirectes et exclurait la bibliothèque du dossier publié.</span><span class="sxs-lookup"><span data-stu-id="565fd-117">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="565fd-118">Lorsque le code fait indirectement référence à un assemblage par la réflexion, `<TrimmerRootAssembly>` vous pouvez empêcher l’assemblage d’être garni avec le réglage.</span><span class="sxs-lookup"><span data-stu-id="565fd-118">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="565fd-119">L’exemple suivant montre comment `System.Security` empêcher qu’un assemblage appelé assemblage ne soit coupé :</span><span class="sxs-lookup"><span data-stu-id="565fd-119">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="565fd-120">Coupez votre application - CLI</span><span class="sxs-lookup"><span data-stu-id="565fd-120">Trim your app - CLI</span></span>

<span data-ttu-id="565fd-121">Coupez votre application à l’aide de la commande [de publication dotnet.](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="565fd-121">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="565fd-122">Lorsque vous publiez votre application, définissez les trois paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="565fd-122">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="565fd-123">Publier comme autonome:`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="565fd-123">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="565fd-124">Désactiver la publication à un seul fichier :`-p:PublishSingleFile=false`</span><span class="sxs-lookup"><span data-stu-id="565fd-124">Disable single-file publishing: `-p:PublishSingleFile=false`</span></span>
- <span data-ttu-id="565fd-125">Activer l’élagage :`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="565fd-125">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="565fd-126">L’exemple suivant publie une application pour Windows 10 en tant qu’autonome et réduit la sortie.</span><span class="sxs-lookup"><span data-stu-id="565fd-126">The following example publishes an app for Windows 10 as self-contained and trims the output.</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

<span data-ttu-id="565fd-127">Pour plus d’informations, voir [Publier .NET Core apps avec .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-127">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="565fd-128">Coupez votre application - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="565fd-128">Trim your app - Visual Studio</span></span>

<span data-ttu-id="565fd-129">Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.</span><span class="sxs-lookup"><span data-stu-id="565fd-129">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="565fd-130">Sur le volet **Solution Explorer,** cliquez à droite sur le projet que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="565fd-130">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="565fd-131">Sélectionnez **Publier...**.</span><span class="sxs-lookup"><span data-stu-id="565fd-131">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Solution Explorer avec un menu à clic droit mettant en évidence l’option Publier.":::

    <span data-ttu-id="565fd-133">Si vous n’avez pas déjà de profil de publication, suivez les instructions pour en créer un et choisissez le type cible **Folder.**</span><span class="sxs-lookup"><span data-stu-id="565fd-133">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="565fd-134">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="565fd-134">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Studio visuel publier le profil avec bouton d’édition.":::

01. <span data-ttu-id="565fd-136">Dans le dialogue **des paramètres de profil,** définissez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="565fd-136">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="565fd-137">Définissez **le mode de déploiement** en **autonome.**</span><span class="sxs-lookup"><span data-stu-id="565fd-137">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="565fd-138">Définissez **l’heure d’exécution de Target** à la plate-forme que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="565fd-138">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="565fd-139">Sélectionnez **des assemblages inutilisés Trim (en avant-première).**</span><span class="sxs-lookup"><span data-stu-id="565fd-139">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="565fd-140">Choisissez **Enregistrer** pour enregistrer les paramètres et revenir au dialogue **Publier.**</span><span class="sxs-lookup"><span data-stu-id="565fd-140">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Les paramètres de profil dialoguent avec le mode de déploiement, l’exécution cible et les options d’assemblage inutilisés mises en évidence.":::

01. <span data-ttu-id="565fd-142">Choisissez **Publier** pour publier votre application paré.</span><span class="sxs-lookup"><span data-stu-id="565fd-142">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="565fd-143">Pour plus d’informations, voir [Publier .NET Core apps avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-143">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="565fd-144">Coupez votre application - Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="565fd-144">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="565fd-145">Visual Studio pour Mac ne fournit pas d’options pour couper votre application lors de la publication.</span><span class="sxs-lookup"><span data-stu-id="565fd-145">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="565fd-146">Vous devrez publier manuellement en suivant les instructions de la section [Trim votre application - CLI.](#trim-your-app---cli)</span><span class="sxs-lookup"><span data-stu-id="565fd-146">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="565fd-147">Pour plus d’informations, voir [Publier .NET Core apps avec .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-147">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="565fd-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="565fd-148">See also</span></span>

- <span data-ttu-id="565fd-149">[.NET Déploiement d’applications de base](index.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-149">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="565fd-150">[Publier .NET Core apps avec .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-150">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="565fd-151">[Publier des applications .NET Core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-151">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="565fd-152">[dotnet publier commande](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="565fd-152">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
