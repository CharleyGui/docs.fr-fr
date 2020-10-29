---
title: Découper les applications autonomes
description: Découvrez comment supprimer les applications autonomes pour réduire leur taille. .NET Core regroupe le Runtime avec une application qui est publiée automatiquement et qui comprend généralement un plus grand nombre d’exécutions.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bf38ffe4d47986ae78c6cf2b2e5ecb292411ba6c
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925283"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="ba831-104">Supprimer les exécutables et les déploiements autonomes</span><span class="sxs-lookup"><span data-stu-id="ba831-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="ba831-105">Le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) est le modèle de déploiement le plus performant depuis la création de .net.</span><span class="sxs-lookup"><span data-stu-id="ba831-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="ba831-106">Dans ce scénario, le développeur d’applications ne regroupe que l’application et les assemblys tiers dans l’attente que le Runtime .NET et les bibliothèques d’infrastructure soient disponibles sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="ba831-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="ba831-107">Ce modèle de déploiement est toujours le plus dominant dans .NET Core, mais dans certains scénarios, le modèle dépendant du Framework n’est pas optimal.</span><span class="sxs-lookup"><span data-stu-id="ba831-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="ba831-108">L’alternative consiste à publier une [application autonome](index.md#publish-self-contained), où le Runtime .net Core et l’infrastructure sont regroupés avec l’application et les assemblys tiers.</span><span class="sxs-lookup"><span data-stu-id="ba831-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="ba831-109">Le modèle Trim-self-contained Deployment est une version spécialisée du modèle de déploiement autonome qui est optimisé pour réduire la taille du déploiement.</span><span class="sxs-lookup"><span data-stu-id="ba831-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="ba831-110">La réduction de la taille du déploiement est une condition essentielle pour certains scénarios côté client comme les applications éblouissantes.</span><span class="sxs-lookup"><span data-stu-id="ba831-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="ba831-111">En fonction de la complexité de l’application, seul un sous-ensemble des assemblys de l’infrastructure est référencé et un sous-ensemble du code dans chaque assembly est requis pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ba831-111">Depending on the complexity of the application, only a subset of the framework assemblies are referenced, and a subset of the code within each assembly is required to run the application.</span></span> <span data-ttu-id="ba831-112">Les parties inutilisées des bibliothèques ne sont pas nécessaires et peuvent être supprimées de l’application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="ba831-112">The unused parts of the libraries are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="ba831-113">Toutefois, il existe un risque que l’analyse du temps de génération de l’application puisse provoquer des échecs lors de l’exécution, en raison de l’impossibilité d’analyser de manière fiable divers modèles de code problématiques (principalement centrés sur l’utilisation de la réflexion).</span><span class="sxs-lookup"><span data-stu-id="ba831-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="ba831-114">Étant donné que la fiabilité ne peut pas être garantie, ce modèle de déploiement est proposé sous la forme d’une fonctionnalité en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="ba831-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span>

<span data-ttu-id="ba831-115">Le moteur d’analyse de la durée de génération fournit des avertissements au développeur de modèles de code qui sont problématiques pour détecter l’autre code requis.</span><span class="sxs-lookup"><span data-stu-id="ba831-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic to detect which other code is required.</span></span> <span data-ttu-id="ba831-116">Le code peut être annoté avec des attributs pour indiquer au massicot les autres éléments à inclure.</span><span class="sxs-lookup"><span data-stu-id="ba831-116">Code can be annotated with attributes to tell the trimmer what else to include.</span></span> <span data-ttu-id="ba831-117">De nombreux modèles de réflexion peuvent être remplacés par la génération de code au moment de la génération à l’aide de [générateurs de source](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-117">Many reflection patterns can be replaced with build-time code generation using [Source Generators](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span></span>

<span data-ttu-id="ba831-118">Le mode de découpage des applications est configuré avec le `TrimMode` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ba831-118">The trim mode for the applications is configured with the `TrimMode` setting.</span></span> <span data-ttu-id="ba831-119">La valeur par défaut est `copyused` et regroupe les assemblys référencés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="ba831-119">The default value is `copyused` and bundles referenced assemblies with the application.</span></span> <span data-ttu-id="ba831-120">La `link` valeur est utilisée avec les applications de Webassembly éblouissantes et supprime le code inutilisé dans les assemblys.</span><span class="sxs-lookup"><span data-stu-id="ba831-120">The `link` value is used with Blazor WebAssembly applications and trims unused code within assemblies.</span></span> <span data-ttu-id="ba831-121">Les avertissements d’analyse de suppression fournissent des informations sur les modèles de code où une analyse de dépendance complète n’était pas possible.</span><span class="sxs-lookup"><span data-stu-id="ba831-121">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="ba831-122">Ces avertissements sont supprimés par défaut et peuvent être activés en affectant à l’indicateur la valeur `SuppressTrimAnalysisWarnings` `false` .</span><span class="sxs-lookup"><span data-stu-id="ba831-122">These warnings are suppressed by default and can be turned on by setting the flag `SuppressTrimAnalysisWarnings` to `false`.</span></span> <span data-ttu-id="ba831-123">Pour plus d’informations sur les options de suppression disponibles, consultez [options de suppression](trimming-options.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-123">For more information about the trim options available, see [Trimming options](trimming-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ba831-124">Le découpage est une fonctionnalité expérimentale de .NET Core 3,1 et .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="ba831-124">Trimming is an experimental feature in .NET Core 3.1 and .NET 5.0.</span></span> <span data-ttu-id="ba831-125">Le découpage est _uniquement_ disponible pour les applications qui sont publiées de façon autonome.</span><span class="sxs-lookup"><span data-stu-id="ba831-125">Trimming is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="ba831-126">Empêcher la troncation des assemblys</span><span class="sxs-lookup"><span data-stu-id="ba831-126">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="ba831-127">Il existe des scénarios dans lesquels la fonctionnalité de suppression ne parviendra pas à détecter les références.</span><span class="sxs-lookup"><span data-stu-id="ba831-127">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="ba831-128">Par exemple, quand la réflexion est utilisée sur un assembly de Runtime, que ce soit par votre application ou une bibliothèque référencée par votre application, l’assembly n’est pas directement référencé.</span><span class="sxs-lookup"><span data-stu-id="ba831-128">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="ba831-129">Le rognage ne tient pas compte de ces références indirectes et exclut la bibliothèque du dossier publié.</span><span class="sxs-lookup"><span data-stu-id="ba831-129">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="ba831-130">Lorsque le code référence indirectement un assembly par le biais de la réflexion, vous pouvez empêcher la troncation de l’assembly avec le `<TrimmerRootAssembly>` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ba831-130">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="ba831-131">L’exemple suivant montre comment empêcher la troncation d’un assembly appelé `System.Security` assembly :</span><span class="sxs-lookup"><span data-stu-id="ba831-131">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="support-for-ssl-certificates"></a><span data-ttu-id="ba831-132">Prise en charge des certificats SSL</span><span class="sxs-lookup"><span data-stu-id="ba831-132">Support for SSL certificates</span></span>

<span data-ttu-id="ba831-133">Si votre application charge des certificats SSL, par exemple dans une application ASP.NET Core, vous souhaiterez vous assurer que lors du découpage, vous empêchez de découper les assemblys qui faciliteront le chargement des certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="ba831-133">If your app loads SSL certificates, such as in an ASP.NET Core app, you'll want to ensure that when trimming you prevent trimming assemblies that will help with loading SSL certificates.</span></span>

<span data-ttu-id="ba831-134">Nous pouvons mettre à jour notre fichier projet pour inclure les éléments suivants pour ASP.NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="ba831-134">We can update our project file to include the following for ASP.NET Core 3.1:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>...</PropertyGroup>
  <!--Include the following for .aspnetcore 3.1-->
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Net" />
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

<span data-ttu-id="ba831-135">Si vous utilisez .net 5,0, nous pouvons mettre à jour notre fichier projet pour inclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ba831-135">If we're using .Net 5.0, we can update our project file to include the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
 <PropertyGroup>...</PropertyGroup>
 <!--Include the following for .net 5.0-->
 <ItemGroup>
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="ba831-136">Découper votre application-CLI</span><span class="sxs-lookup"><span data-stu-id="ba831-136">Trim your app - CLI</span></span>

<span data-ttu-id="ba831-137">Découpez votre application à l’aide de la commande [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="ba831-137">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="ba831-138">Lorsque vous publiez votre application, définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba831-138">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="ba831-139">Publier en tant qu’application autonome pour un Runtime spécifique : `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="ba831-139">Publish as a self-contained app for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="ba831-140">Activer le découpage : `/p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="ba831-140">Enable trimming: `/p:PublishTrimmed=true`</span></span>

<span data-ttu-id="ba831-141">L’exemple suivant publie une application pour Windows comme autonome et découpe la sortie.</span><span class="sxs-lookup"><span data-stu-id="ba831-141">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

<span data-ttu-id="ba831-142">L’exemple suivant publie une application en mode de découpage agressif où le code inutilisé dans les assemblys est tronqué et les avertissements de découpage sont activés.</span><span class="sxs-lookup"><span data-stu-id="ba831-142">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and trimmer warnings enabled.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

<span data-ttu-id="ba831-143">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-143">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="ba831-144">Découper votre application-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba831-144">Trim your app - Visual Studio</span></span>

<span data-ttu-id="ba831-145">Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.</span><span class="sxs-lookup"><span data-stu-id="ba831-145">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="ba831-146">Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le projet que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="ba831-146">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="ba831-147">Sélectionnez **publier...** .</span><span class="sxs-lookup"><span data-stu-id="ba831-147">Select **Publish...** .</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

    <span data-ttu-id="ba831-149">Si vous ne disposez pas déjà d’un profil de publication, suivez les instructions pour en créer un et choisissez le type cible du **dossier** .</span><span class="sxs-lookup"><span data-stu-id="ba831-149">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="ba831-150">Choisissez **Modifier** .</span><span class="sxs-lookup"><span data-stu-id="ba831-150">Choose **Edit** .</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Profil de publication Visual Studio avec le bouton modifier.":::

01. <span data-ttu-id="ba831-152">Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba831-152">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="ba831-153">Définissez **le** **mode de déploiement** sur autonome.</span><span class="sxs-lookup"><span data-stu-id="ba831-153">Set **Deployment mode** to **Self-contained** .</span></span>
    - <span data-ttu-id="ba831-154">Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="ba831-154">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="ba831-155">Sélectionnez **découper les assemblys inutilisés (en** préversion).</span><span class="sxs-lookup"><span data-stu-id="ba831-155">Select **Trim unused assemblies (in preview)** .</span></span>

    <span data-ttu-id="ba831-156">Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .</span><span class="sxs-lookup"><span data-stu-id="ba831-156">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Boîte de dialogue Paramètres de profil avec les options mode de déploiement, Runtime cible et découper les assemblys inutilisés mis en surbrillance.":::

01. <span data-ttu-id="ba831-158">Choisissez **publier** pour publier votre application supprimée.</span><span class="sxs-lookup"><span data-stu-id="ba831-158">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="ba831-159">Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-159">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="ba831-160">Découper votre application-Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="ba831-160">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="ba831-161">Visual Studio pour Mac ne fournit pas d’options pour découper votre application pendant la publication.</span><span class="sxs-lookup"><span data-stu-id="ba831-161">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="ba831-162">Vous devez publier manuellement en suivant les instructions de la section [Trim Your App-CLI](#trim-your-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="ba831-162">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="ba831-163">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-163">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba831-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba831-164">See also</span></span>

- <span data-ttu-id="ba831-165">[Déploiement d’applications .net Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-165">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="ba831-166">[Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-166">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="ba831-167">[Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-167">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="ba831-168">[commande dotnet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="ba831-168">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
