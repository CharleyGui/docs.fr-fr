---
title: Aide sur les modèles d’options pour les auteurs de bibliothèques .NET
author: IEvangelist
description: Découvrez comment exposer le modèle d’options en tant qu’auteur de bibliothèque dans .NET.
ms.author: dapine
ms.date: 01/28/2021
ms.openlocfilehash: d0da94a8f25c9e5aba6093fab07ccca6a0a7c345
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217214"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a><span data-ttu-id="aea54-103">Aide sur les modèles d’options pour les auteurs de bibliothèques .NET</span><span class="sxs-lookup"><span data-stu-id="aea54-103">Options pattern guidance for .NET library authors</span></span>

<span data-ttu-id="aea54-104">Avec l’aide de l’injection de dépendances, l’inscription de vos services et de leurs configurations correspondantes peut utiliser le *modèle d’options*.</span><span class="sxs-lookup"><span data-stu-id="aea54-104">With the help of dependency injection, registering your services and their corresponding configurations can make use of the *options pattern*.</span></span> <span data-ttu-id="aea54-105">Le modèle d’options permet aux consommateurs de votre bibliothèque (et à vos services) de demander des instances d' [interfaces d’options](options.md#options-interfaces) où `TOptions` est votre classe d’options.</span><span class="sxs-lookup"><span data-stu-id="aea54-105">The options pattern enables consumers of your library (and your services) to require instances of [options interfaces](options.md#options-interfaces) where `TOptions` is your options class.</span></span> <span data-ttu-id="aea54-106">L’utilisation d’options de configuration par le biais d’objets fortement typés permet d’assurer une représentation cohérente des valeurs, et supprime la charge liée à l’analyse manuelle des valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="aea54-106">Consuming configuration options through strongly-typed objects helps to ensure consistent value representation, and removes the burden of manually parsing string values.</span></span> <span data-ttu-id="aea54-107">De nombreux [fournisseurs de configuration](configuration-providers.md) peuvent être utilisés par les consommateurs de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="aea54-107">There are many [configuration providers](configuration-providers.md) for consumers of your library to use.</span></span> <span data-ttu-id="aea54-108">Avec ces fournisseurs, les consommateurs peuvent configurer votre bibliothèque de nombreuses façons.</span><span class="sxs-lookup"><span data-stu-id="aea54-108">With these providers, consumers can configure your library in many ways.</span></span>

<span data-ttu-id="aea54-109">En tant qu’auteur de bibliothèque .NET, vous apprendrez des conseils généraux sur la façon d’exposer correctement le modèle d’options aux consommateurs de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="aea54-109">As a .NET library author, you'll learn general guidance on how to correctly expose the options pattern to consumers of your library.</span></span> <span data-ttu-id="aea54-110">Il existe plusieurs façons d’accomplir la même chose, et plusieurs considérations à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="aea54-110">There are various ways to achieve the same thing, and several considerations to make.</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="aea54-111">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="aea54-111">Naming conventions</span></span>

<span data-ttu-id="aea54-112">Par Convention, les méthodes d’extension responsables de l’inscription des services sont nommées `Add{Service}` , où `{Service}` est un nom explicite et descriptif.</span><span class="sxs-lookup"><span data-stu-id="aea54-112">By convention, extension methods responsible for registering services are named `Add{Service}`, where `{Service}` is a meaningful and descriptive name.</span></span> <span data-ttu-id="aea54-113">Selon le package, l’inscription des services peut être accompagnée de `Use{Service}` méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="aea54-113">Depending on the package, the registration of services may be accompanied by `Use{Service}` extension methods.</span></span> <span data-ttu-id="aea54-114">Les `Use{Service}` méthodes d’extension sont banales dans [ASP.net Core](/aspnet).</span><span class="sxs-lookup"><span data-stu-id="aea54-114">The `Use{Service}` extension methods are commonplace in [ASP.NET Core](/aspnet).</span></span>

<span data-ttu-id="aea54-115">✔️ PRENDRE en compte les noms qui lèvent une ambiguïté entre votre service et d’autres offres.</span><span class="sxs-lookup"><span data-stu-id="aea54-115">✔️ CONSIDER names that disambiguate your service from other offerings.</span></span>

<span data-ttu-id="aea54-116">❌ N’utilisez pas les noms qui font déjà partie de l’écosystème .NET des packages Microsoft officiels.</span><span class="sxs-lookup"><span data-stu-id="aea54-116">❌ DO NOT use names that are already part of the .NET ecosystem from official Microsoft packages.</span></span>

<span data-ttu-id="aea54-117">✔️ ENVISAGER de nommer des classes statiques qui exposent des méthodes d’extension en tant que `{Type}Extensions` , où `{Type}` est le type que vous étendez.</span><span class="sxs-lookup"><span data-stu-id="aea54-117">✔️ CONSIDER naming static classes that expose extension methods as `{Type}Extensions`, where `{Type}` is the type that you're extending.</span></span>

### <a name="namespace-guidance"></a><span data-ttu-id="aea54-118">Aide sur les espaces de noms</span><span class="sxs-lookup"><span data-stu-id="aea54-118">Namespace guidance</span></span>

<span data-ttu-id="aea54-119">Les packages Microsoft utilisent l' `Microsoft.Extensions.DependencyInjection` espace de noms pour unifier l’inscription de diverses offres de service.</span><span class="sxs-lookup"><span data-stu-id="aea54-119">Microsoft packages make use of the `Microsoft.Extensions.DependencyInjection` namespace to unify the registration of various service offerings.</span></span>

<span data-ttu-id="aea54-120">✔️ ENVISAGER un espace de noms qui identifie clairement votre offre de package.</span><span class="sxs-lookup"><span data-stu-id="aea54-120">✔️ CONSIDER a namespace that clearly identifies your package offering.</span></span>

<span data-ttu-id="aea54-121">❌ N’utilisez pas l' `Microsoft.Extensions.DependencyInjection` espace de noms pour les packages Microsoft non officiels.</span><span class="sxs-lookup"><span data-stu-id="aea54-121">❌ DO NOT use the `Microsoft.Extensions.DependencyInjection` namespace for non-official Microsoft packages.</span></span>

## <a name="parameterless"></a><span data-ttu-id="aea54-122">Sans paramètre</span><span class="sxs-lookup"><span data-stu-id="aea54-122">Parameterless</span></span>

<span data-ttu-id="aea54-123">Si votre service peut fonctionner avec une configuration minimale ou sans configuration explicite, pensez à une méthode d’extension sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="aea54-123">If your service can work with minimal or no explicit configuration, consider a parameterless extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

<span data-ttu-id="aea54-124">Dans le code précédent, `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="aea54-124">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="aea54-125">Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="aea54-125">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="aea54-126">Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> avec le paramètre de type de `LibraryOptions`</span><span class="sxs-lookup"><span data-stu-id="aea54-126">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="aea54-127">Chaîne un appel à <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> , qui spécifie les valeurs d’option par défaut</span><span class="sxs-lookup"><span data-stu-id="aea54-127">Chains a call to <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>, which specifies the default option values</span></span>

## <a name="iconfiguration-parameter"></a><span data-ttu-id="aea54-128">Paramètre `IConfiguration`</span><span class="sxs-lookup"><span data-stu-id="aea54-128">`IConfiguration` parameter</span></span>

<span data-ttu-id="aea54-129">Lorsque vous créez une bibliothèque qui expose de nombreuses options aux consommateurs, vous pouvez envisager d’exiger une `IConfiguration` méthode d’extension de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aea54-129">When you author a library that exposes many options to consumers, you may want to consider requiring an `IConfiguration` parameter extension method.</span></span> <span data-ttu-id="aea54-130">L’instance attendue `IConfiguration` doit être limitée à une section nommée de la configuration à l’aide de la <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> fonction.</span><span class="sxs-lookup"><span data-stu-id="aea54-130">The expected `IConfiguration` instance should be scoped to a named section of the configuration by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> function.</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-16":::

<span data-ttu-id="aea54-131">Dans le code précédent, `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="aea54-131">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="aea54-132">Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="aea54-132">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="aea54-133">Définit un <xref:Microsoft.Extensions.Configuration.IConfiguration> paramètre `namedConfigurationSection`</span><span class="sxs-lookup"><span data-stu-id="aea54-133">Defines an <xref:Microsoft.Extensions.Configuration.IConfiguration> parameter `namedConfigurationSection`</span></span>
- <span data-ttu-id="aea54-134">Appels <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> passant une instance d’options à laquelle la configuration est liée</span><span class="sxs-lookup"><span data-stu-id="aea54-134">Calls <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> passing an options instance that the configuration binds to</span></span>

<span data-ttu-id="aea54-135">Les consommateurs dans ce modèle fournissent l' `IConfiguration` instance étendue de la section nommée :</span><span class="sxs-lookup"><span data-stu-id="aea54-135">Consumers in this pattern provide the scoped `IConfiguration` instance of the named section:</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

<span data-ttu-id="aea54-136">L’appel à `.AddMyLibraryService` est effectué dans la <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="aea54-136">The call to `.AddMyLibraryService` is made in the <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> method.</span></span> <span data-ttu-id="aea54-137">Il en va de même pour l’utilisation d’une `Startup` classe, l’ajout de services en cours d’inscription dans `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="aea54-137">The same is true when using a `Startup` class, the addition of services being registered occurs in `ConfigureServices`.</span></span>

<span data-ttu-id="aea54-138">En tant qu’auteur de bibliothèque, il vous revient de spécifier les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="aea54-138">As the library author, specifying default values is up to you.</span></span>

> [!NOTE]
> <span data-ttu-id="aea54-139">Il est possible de lier la configuration à une instance d’options.</span><span class="sxs-lookup"><span data-stu-id="aea54-139">It is possible to bind configuration to an options instance.</span></span> <span data-ttu-id="aea54-140">Toutefois, il existe un risque de collisions de noms, ce qui entraîne des erreurs.</span><span class="sxs-lookup"><span data-stu-id="aea54-140">However, there is a risk of name collisions - which will cause errors.</span></span> <span data-ttu-id="aea54-141">En outre, lors de la liaison manuelle de cette manière, vous limitez la consommation de votre modèle d’options à la lecture une fois.</span><span class="sxs-lookup"><span data-stu-id="aea54-141">Additionally, when manually binding in this way, you limit the consumption of your options pattern to read-once.</span></span> <span data-ttu-id="aea54-142">Les modifications apportées aux paramètres ne seront pas reliées, car ces consommateurs ne pourront pas utiliser l’interface [IOptionsMonitor](options.md#ioptionsmonitor) .</span><span class="sxs-lookup"><span data-stu-id="aea54-142">Changes to settings will not be re-bound, as such consumers will not be able to use the [IOptionsMonitor](options.md#ioptionsmonitor) interface.</span></span>
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a><span data-ttu-id="aea54-143">Paramètre `Action<TOptions>`</span><span class="sxs-lookup"><span data-stu-id="aea54-143">`Action<TOptions>` parameter</span></span>

<span data-ttu-id="aea54-144">Les consommateurs de votre bibliothèque peuvent souhaiter fournir une expression lambda qui produit une instance de votre classe d’options.</span><span class="sxs-lookup"><span data-stu-id="aea54-144">Consumers of your library may be interested in providing a lambda expression that yields an instance of your options class.</span></span> <span data-ttu-id="aea54-145">Dans ce scénario, vous définissez un `Action<LibraryOptions>` paramètre dans votre méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="aea54-145">In this scenario, you define an `Action<LibraryOptions>` parameter in your extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="aea54-146">Dans le code précédent, `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="aea54-146">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="aea54-147">Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="aea54-147">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="aea54-148">Définit un <xref:System.Action%601> `T` paramètre Where `LibraryOptions``configureOptions`</span><span class="sxs-lookup"><span data-stu-id="aea54-148">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="aea54-149">Appelle en <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> fonction de l' `configureOptions` action</span><span class="sxs-lookup"><span data-stu-id="aea54-149">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="aea54-150">Dans ce modèle, les consommateurs fournissent une expression lambda (ou un délégué qui satisfait au `Action<LibraryOptions>` paramètre) :</span><span class="sxs-lookup"><span data-stu-id="aea54-150">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter):</span></span>

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a><span data-ttu-id="aea54-151">Paramètre d’instance options</span><span class="sxs-lookup"><span data-stu-id="aea54-151">Options instance parameter</span></span>

<span data-ttu-id="aea54-152">Les consommateurs de votre bibliothèque préfèrent peut-être fournir une instance d’options inline.</span><span class="sxs-lookup"><span data-stu-id="aea54-152">Consumers of your library might prefer to provide an inlined options instance.</span></span> <span data-ttu-id="aea54-153">Dans ce scénario, vous exposez une méthode d’extension qui prend une instance de votre objet d’options, `LibraryOptions` .</span><span class="sxs-lookup"><span data-stu-id="aea54-153">In this scenario, you expose an extension method that takes an instance of your options object, `LibraryOptions`.</span></span>

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

<span data-ttu-id="aea54-154">Dans le code précédent, `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="aea54-154">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="aea54-155">Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="aea54-155">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="aea54-156">Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> avec le paramètre de type de `LibraryOptions`</span><span class="sxs-lookup"><span data-stu-id="aea54-156">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="aea54-157">Chaîne un appel à <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> , qui spécifie les valeurs d’option par défaut qui peuvent être substituées à partir de l' `userOptions` instance donnée</span><span class="sxs-lookup"><span data-stu-id="aea54-157">Chains a call to <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, which specifies default option values that can be overridden from the given `userOptions` instance</span></span>

<span data-ttu-id="aea54-158">Dans ce modèle, les consommateurs fournissent une instance de la `LibraryOptions` classe, en définissant les valeurs de propriété souhaitées inline :</span><span class="sxs-lookup"><span data-stu-id="aea54-158">Consumers in this pattern provide an instance of the `LibraryOptions` class, defining desired property values inline:</span></span>

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a><span data-ttu-id="aea54-159">Après la configuration</span><span class="sxs-lookup"><span data-stu-id="aea54-159">Post configuration</span></span>

<span data-ttu-id="aea54-160">Une fois que toutes les valeurs d’option de configuration sont liées ou spécifiées, la fonctionnalité de configuration de la publication est disponible.</span><span class="sxs-lookup"><span data-stu-id="aea54-160">After all configuration option values are bound or specified, post configuration functionality is available.</span></span> <span data-ttu-id="aea54-161">En exposant le même [ `Action<TOptions>` paramètre](#actiontoptions-parameter) détaillé précédemment, vous pouvez choisir d’appeler <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> .</span><span class="sxs-lookup"><span data-stu-id="aea54-161">Exposing the same [`Action<TOptions>` parameter](#actiontoptions-parameter) detailed earlier, you could choose to call <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>.</span></span> <span data-ttu-id="aea54-162">La commande après la configuration s’exécute après tous les `.Configure` appels.</span><span class="sxs-lookup"><span data-stu-id="aea54-162">Post configure runs after all `.Configure` calls.</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="aea54-163">Dans le code précédent, `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="aea54-163">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="aea54-164">Étend une instance de <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="aea54-164">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="aea54-165">Définit un <xref:System.Action%601> `T` paramètre Where `LibraryOptions``configureOptions`</span><span class="sxs-lookup"><span data-stu-id="aea54-165">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="aea54-166">Appelle en <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> fonction de l' `configureOptions` action</span><span class="sxs-lookup"><span data-stu-id="aea54-166">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="aea54-167">Dans ce modèle, les consommateurs fournissent une expression lambda (ou un délégué qui répond au `Action<LibraryOptions>` paramètre), comme ils le feraient avec [ `Action<TOptions>` paramètre] dans un scénario de non-publication de configuration :</span><span class="sxs-lookup"><span data-stu-id="aea54-167">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter), just as they would with the [`Action<TOptions>` parameter] in a non-post configuration scenario:</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a><span data-ttu-id="aea54-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aea54-168">See also</span></span>

- [<span data-ttu-id="aea54-169">Modèle d’options dans .NET</span><span class="sxs-lookup"><span data-stu-id="aea54-169">Options pattern in .NET</span></span>](options.md)
- [<span data-ttu-id="aea54-170">Injection de dépendances dans .NET</span><span class="sxs-lookup"><span data-stu-id="aea54-170">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="aea54-171">Recommandations relatives à l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="aea54-171">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
