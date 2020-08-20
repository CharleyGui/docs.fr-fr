---
title: Découper les applications autonomes
description: Découvrez comment supprimer les applications autonomes pour réduire leur taille. .NET Core regroupe le Runtime avec une application qui est publiée automatiquement et qui comprend généralement un plus grand nombre d’exécutions.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 2bb0f03994468bbad3096ebf0b141bc1f47b867e
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656714"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="5b9e6-104">Supprimer les exécutables et les déploiements autonomes</span><span class="sxs-lookup"><span data-stu-id="5b9e6-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="5b9e6-105">Le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) est le modèle de déploiement le plus performant depuis la création de .net.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="5b9e6-106">Dans ce scénario, le développeur d’applications ne regroupe que l’application et les assemblys tiers dans l’attente que le Runtime .NET et les bibliothèques d’infrastructure soient disponibles sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="5b9e6-107">Ce modèle de déploiement est toujours le plus dominant dans .NET Core, mais dans certains scénarios, le modèle dépendant du Framework n’est pas optimal.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="5b9e6-108">L’alternative consiste à publier une [application autonome](index.md#publish-self-contained), où le Runtime .net Core et l’infrastructure sont regroupés avec l’application et les assemblys tiers.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="5b9e6-109">Le modèle Trim-self-contained Deployment est une version spécialisée du modèle de déploiement autonome qui est optimisé pour réduire la taille du déploiement.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="5b9e6-110">La réduction de la taille du déploiement est une condition essentielle pour certains scénarios côté client comme les applications éblouissantes.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="5b9e6-111">En fonction de la complexité de l’application, seul un sous-ensemble des assemblys de l’infrastructure est requis pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-111">Depending on the complexity of the application, only a subset of the framework assemblies are required to run the application.</span></span> <span data-ttu-id="5b9e6-112">Ces parties inutilisées de la bibliothèque ne sont pas nécessaires et peuvent être supprimées de l’application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-112">These unused parts of the library are unnecessary and can be trimmed from the packaged application.</span></span> <span data-ttu-id="5b9e6-113">Toutefois, il existe un risque que l’analyse du temps de génération de l’application puisse provoquer des échecs lors de l’exécution, en raison de l’impossibilité d’analyser de manière fiable divers modèles de code problématiques (principalement centrés sur l’utilisation de la réflexion).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="5b9e6-114">Étant donné que la fiabilité ne peut pas être garantie, ce modèle de déploiement est proposé sous la forme d’une fonctionnalité en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span> <span data-ttu-id="5b9e6-115">Le moteur d’analyse du temps de génération fournit des avertissements au développeur de modèles de code problématiques, dans l’attente que ces modèles de code soient corrigés.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic, with the expectation that these code patterns will be fixed.</span></span> <span data-ttu-id="5b9e6-116">Dans la mesure du possible, nous vous recommandons de déplacer toutes les dépendances de réflexion du runtime dans votre application pour créer du temps à l’aide d’un code qui répond aux mêmes exigences.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-116">Where possible, we recommend that you move any runtime reflection dependencies in your application to build time by using code that meets the same requirements.</span></span>

<span data-ttu-id="5b9e6-117">Le mode de découpage des applications peut être configuré via TrimMode et par défaut ( `copyused` ) pour regrouper les assemblys utilisés dans l’application.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-117">The trim mode for the applications can be configured via the TrimMode and will default (`copyused`) to bundle assemblies that are used in the application.</span></span> <span data-ttu-id="5b9e6-118">Les applications webassembly éblouissantes utilisent un mode plus agressif ( `link` ) qui découpera le code inutilisé dans les assemblys.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-118">Blazor WebAssembly applications will use a more aggressive mode (`link`) that will trim unused code within assemblies.</span></span> <span data-ttu-id="5b9e6-119">Les avertissements d’analyse de suppression fournissent des informations sur les modèles de code où une analyse de dépendance complète n’était pas possible.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-119">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="5b9e6-120">Ces avertissements sont supprimés par défaut et peuvent être activés en affectant à l’indicateur, la `SuppressTrimAnalysisWarnings` valeur false.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-120">These warnings are suppressed by default and can be turned on by setting the flag, `SuppressTrimAnalysisWarnings`, to false.</span></span> <span data-ttu-id="5b9e6-121">Vous trouverez plus d’informations sur les options de suppression disponibles sur la [page ILLinker](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-121">More information on the trim options available can be found at the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5b9e6-122">Le découpage est une fonctionnalité expérimentale de .NET Core 3,1, 5,0, qui est _uniquement_ disponible pour les applications qui sont publiées de façon autonome.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-122">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="5b9e6-123">Empêcher la troncation des assemblys</span><span class="sxs-lookup"><span data-stu-id="5b9e6-123">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="5b9e6-124">Il existe des scénarios dans lesquels la fonctionnalité de suppression ne parviendra pas à détecter les références.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-124">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="5b9e6-125">Par exemple, quand la réflexion est utilisée sur un assembly de Runtime, que ce soit par votre application ou une bibliothèque référencée par votre application, l’assembly n’est pas directement référencé.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-125">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="5b9e6-126">Le rognage ne tient pas compte de ces références indirectes et exclut la bibliothèque du dossier publié.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-126">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="5b9e6-127">Lorsque le code référence indirectement un assembly par le biais de la réflexion, vous pouvez empêcher la troncation de l’assembly avec le `<TrimmerRootAssembly>` paramètre.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-127">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="5b9e6-128">L’exemple suivant montre comment empêcher la troncation d’un assembly appelé `System.Security` assembly :</span><span class="sxs-lookup"><span data-stu-id="5b9e6-128">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="5b9e6-129">Découper votre application-CLI</span><span class="sxs-lookup"><span data-stu-id="5b9e6-129">Trim your app - CLI</span></span>

<span data-ttu-id="5b9e6-130">Découpez votre application à l’aide de la commande [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="5b9e6-130">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="5b9e6-131">Lorsque vous publiez votre application, définissez les trois paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="5b9e6-131">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="5b9e6-132">Publier comme autonome : `--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="5b9e6-132">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="5b9e6-133">Activer le découpage : `p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="5b9e6-133">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="5b9e6-134">L’exemple suivant publie une application pour Windows comme autonome et découpe la sortie.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-134">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<ItemGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
</ItemGroup>
```

<span data-ttu-id="5b9e6-135">L’exemple suivant publie une application en mode de découpage agressif où le code non utilisé avec des assemblys est tronqué et les avertissements de découpage sont activés.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-135">The following example publishes an app in the aggressive trim mode where unused code withing assemblies will be trimmed and  trimmer warnings enabled.</span></span>

```xml
<ItemGroup>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</ItemGroup>
```

<span data-ttu-id="5b9e6-136">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-136">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="5b9e6-137">Découper votre application-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5b9e6-137">Trim your app - Visual Studio</span></span>

<span data-ttu-id="5b9e6-138">Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-138">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="5b9e6-139">Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le projet que vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-139">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="5b9e6-140">Sélectionnez **publier...**.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-140">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

    <span data-ttu-id="5b9e6-142">Si vous ne disposez pas déjà d’un profil de publication, suivez les instructions pour en créer un et choisissez le type cible du **dossier** .</span><span class="sxs-lookup"><span data-stu-id="5b9e6-142">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="5b9e6-143">Choisissez **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-143">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Profil de publication Visual Studio avec le bouton modifier.":::

01. <span data-ttu-id="5b9e6-145">Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b9e6-145">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="5b9e6-146">Définissez **le** **mode de déploiement** sur autonome.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-146">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="5b9e6-147">Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-147">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="5b9e6-148">Sélectionnez **découper les assemblys inutilisés (en**préversion).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-148">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="5b9e6-149">Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .</span><span class="sxs-lookup"><span data-stu-id="5b9e6-149">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Boîte de dialogue Paramètres de profil avec les options mode de déploiement, Runtime cible et découper les assemblys inutilisés mis en surbrillance.":::

01. <span data-ttu-id="5b9e6-151">Choisissez **publier** pour publier votre application supprimée.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-151">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="5b9e6-152">Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-152">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="5b9e6-153">Découper votre application-Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="5b9e6-153">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="5b9e6-154">Visual Studio pour Mac ne fournit pas d’options pour découper votre application pendant la publication.</span><span class="sxs-lookup"><span data-stu-id="5b9e6-154">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="5b9e6-155">Vous devez publier manuellement en suivant les instructions de la section [Trim Your App-CLI](#trim-your-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="5b9e6-155">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="5b9e6-156">Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-156">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b9e6-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b9e6-157">See also</span></span>

- <span data-ttu-id="5b9e6-158">[Déploiement d’applications .net Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-158">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="5b9e6-159">[Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-159">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="5b9e6-160">[Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-160">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="5b9e6-161">[commande dotnet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="5b9e6-161">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
