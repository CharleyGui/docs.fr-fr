---
title: Modèle d’options dans .NET
author: IEvangelist
description: Découvrez comment utiliser le modèle d’options pour représenter des groupes de paramètres associés dans les applications .NET.
ms.author: dapine
ms.date: 01/06/2021
ms.openlocfilehash: 392b3abca01864349f8b1b25ffb3109132d2435a
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189730"
---
# <a name="options-pattern-in-net"></a><span data-ttu-id="44718-103">Modèle d’options dans .NET</span><span class="sxs-lookup"><span data-stu-id="44718-103">Options pattern in .NET</span></span>

<span data-ttu-id="44718-104">Le modèle d’options utilise des classes pour fournir un accès fortement typé aux groupes de paramètres associés.</span><span class="sxs-lookup"><span data-stu-id="44718-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="44718-105">Quand les [paramètres de configuration](configuration.md) sont isolés par scénario dans des classes distinctes, l’application est conforme à deux principes d’ingénierie logicielle importants :</span><span class="sxs-lookup"><span data-stu-id="44718-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="44718-106">Le [principe de séparation d’interface (ISP) ou l’encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): les scénarios (classes) qui dépendent des paramètres de configuration dépendent uniquement des paramètres de configuration qu’ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="44718-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="44718-107">[Séparation des préoccupations](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns) : les paramètres des différentes parties de l’application ne sont pas dépendants ou associés les uns aux autres.</span><span class="sxs-lookup"><span data-stu-id="44718-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="44718-108">Ces options fournissent également un mécanisme de validation des données de configuration.</span><span class="sxs-lookup"><span data-stu-id="44718-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="44718-109">Pour plus d'informations, reportez-vous à la section [Validation des options](#options-validation).</span><span class="sxs-lookup"><span data-stu-id="44718-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="44718-110">Liaison de la configuration hiérarchique</span><span class="sxs-lookup"><span data-stu-id="44718-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="44718-111">La méthode recommandée pour lire les valeurs de configuration associées utilise le modèle d’options.</span><span class="sxs-lookup"><span data-stu-id="44718-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="44718-112">Le modèle d’options est possible via l' <xref:Microsoft.Extensions.Options.IOptions%601> interface, où le paramètre de type générique `TOptions` est restreint à `class` .</span><span class="sxs-lookup"><span data-stu-id="44718-112">The options pattern is possible through the <xref:Microsoft.Extensions.Options.IOptions%601> interface, where the generic type parameter `TOptions` is constrained to `class`.</span></span> <span data-ttu-id="44718-113">Le `IOptions<TOptions>` peut être fourni ultérieurement via l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="44718-113">The `IOptions<TOptions>` can later be provided through dependency injection.</span></span> <span data-ttu-id="44718-114">Pour plus d’informations, consultez [injection de dépendances dans .net](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="44718-114">For more information, see [Dependency injection in .NET](dependency-injection.md).</span></span>

<span data-ttu-id="44718-115">Par exemple, pour lire les valeurs de configuration suivantes :</span><span class="sxs-lookup"><span data-stu-id="44718-115">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="44718-116">Créez la `TransientFaultHandlingOptions` classe suivante :</span><span class="sxs-lookup"><span data-stu-id="44718-116">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span data-ttu-id="44718-117"><span id="options-class"></span> Lorsque vous utilisez le modèle d’options, une classe d’options :</span><span class="sxs-lookup"><span data-stu-id="44718-117"><span id="options-class"></span> When using the options pattern, an options class:</span></span>

- <span data-ttu-id="44718-118">Doit être non abstract avec un constructeur sans paramètre public</span><span class="sxs-lookup"><span data-stu-id="44718-118">Must be non-abstract with a public parameterless constructor</span></span>
- <span data-ttu-id="44718-119">Contenir des propriétés publiques en lecture/écriture à lier (les champs **sont \* liés**)</span><span class="sxs-lookup"><span data-stu-id="44718-119">Contain public read-write properties to bind (fields are \***not** _ bound)</span></span>

<span data-ttu-id="44718-120">Le code suivant :</span><span class="sxs-lookup"><span data-stu-id="44718-120">The following code:</span></span>

<span data-ttu-id="44718-121">_ Appelle [ConfigurationBinder. bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) pour lier la `TransientFaultHandlingOptions` classe à la `"TransientFaultHandlingOptions"` section.</span><span class="sxs-lookup"><span data-stu-id="44718-121">_ Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="44718-122">Affiche les données de configuration.</span><span class="sxs-lookup"><span data-stu-id="44718-122">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="44718-123">Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.</span><span class="sxs-lookup"><span data-stu-id="44718-123">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="44718-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) lie et retourne le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="44718-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="44718-125">`ConfigurationBinder.Get<T>` peut être plus pratique que l’utilisation de `ConfigurationBinder.Bind` .</span><span class="sxs-lookup"><span data-stu-id="44718-125">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="44718-126">Le code suivant montre comment utiliser `ConfigurationBinder.Get<T>` avec la `TransientFaultHandlingOptions` classe :</span><span class="sxs-lookup"><span data-stu-id="44718-126">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="44718-127">Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.</span><span class="sxs-lookup"><span data-stu-id="44718-127">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44718-128">La <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> classe expose plusieurs API, telles que `.Bind(object instance)` et, `.Get<T>()` qui ne sont **pas** _ restreintes à `class` .</span><span class="sxs-lookup"><span data-stu-id="44718-128">The <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> class exposes several APIs, such as `.Bind(object instance)` and `.Get<T>()` that are \***not** _ constrained to `class`.</span></span> <span data-ttu-id="44718-129">Lorsque vous utilisez l’une des [interfaces d’options](#options-interfaces), vous devez respecter les contraintes de classe d' [options](#options-class)mentionnées plus haut.</span><span class="sxs-lookup"><span data-stu-id="44718-129">When using any of the [Options interfaces](#options-interfaces), you must adhere to aforementioned [options class constraints](#options-class).</span></span>

<span data-ttu-id="44718-130">Une autre approche de l’utilisation du modèle options consiste à lier la `"TransientFaultHandlingOptions"` section et à l’ajouter au [conteneur du service d’injection de dépendances](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="44718-130">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="44718-131">Dans le code suivant, `TransientFaultHandlingOptions` est ajouté au conteneur de services avec <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> et lié à la configuration :</span><span class="sxs-lookup"><span data-stu-id="44718-131">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="44718-132">Le `key` paramètre est le nom de la section de configuration à rechercher.</span><span class="sxs-lookup"><span data-stu-id="44718-132">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="44718-133">Elle ne _not \* doit correspondre au nom du type qui la représente.</span><span class="sxs-lookup"><span data-stu-id="44718-133">It does _not\* have to match the name of the type that represents it.</span></span> <span data-ttu-id="44718-134">Par exemple, vous pouvez avoir une section nommée `"FaultHandling"` et elle peut être représentée par la `TransientFaultHandlingOptions` classe.</span><span class="sxs-lookup"><span data-stu-id="44718-134">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="44718-135">Dans ce cas, vous devez passer `"FaultHandling"` à la <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> fonction à la place.</span><span class="sxs-lookup"><span data-stu-id="44718-135">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="44718-136">L' `nameof` opérateur est utilisé à des fins pratiques lorsque la section nommée correspond au type auquel elle correspond.</span><span class="sxs-lookup"><span data-stu-id="44718-136">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="44718-137">À l’aide du code précédent, le code suivant lit les options de position :</span><span class="sxs-lookup"><span data-stu-id="44718-137">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="44718-138">Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont \***non** _ Read.</span><span class="sxs-lookup"><span data-stu-id="44718-138">In the preceding code, changes to the JSON configuration file after the app has started are \***not** _ read.</span></span> <span data-ttu-id="44718-139">Pour lire les modifications une fois l’application démarrée, utilisez [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="44718-139">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="44718-140">Interfaces d’options</span><span class="sxs-lookup"><span data-stu-id="44718-140">Options interfaces</span></span>

<span data-ttu-id="44718-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="44718-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="44718-142">Ne prend _*_pas_*_ en charge :</span><span class="sxs-lookup"><span data-stu-id="44718-142">Does _*_not_*_ support:</span></span>
  - <span data-ttu-id="44718-143">Lecture des données de configuration après le démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="44718-143">Reading of configuration data after the app has started.</span></span>
  - [<span data-ttu-id="44718-144">Options nommées</span><span class="sxs-lookup"><span data-stu-id="44718-144">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
- <span data-ttu-id="44718-145">Est inscrit en tant que [Singleton](dependency-injection.md#singleton) et peut être injecté dans n’importe quelle [durée de vie de service](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="44718-145">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="44718-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="44718-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="44718-147">Est utile dans les scénarios où les options doivent être recalculées à chaque résolution d’injection, dans des [durées de vie délimitées ou transitoires](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="44718-147">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="44718-148">Pour plus d’informations, consultez [utiliser IOptionsSnapshot pour lire des données mises à jour](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="44718-148">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="44718-149">Est inscrit en tant qu' [étendue](dependency-injection.md#scoped) et ne peut donc pas être injecté dans un service Singleton.</span><span class="sxs-lookup"><span data-stu-id="44718-149">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="44718-150">Prend en charge les [options nommées](#named-options-support-using-iconfigurenamedoptions)</span><span class="sxs-lookup"><span data-stu-id="44718-150">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="44718-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="44718-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="44718-152">Est utilisé pour récupérer des options et gérer les notifications d’options pour les `TOptions` instances.</span><span class="sxs-lookup"><span data-stu-id="44718-152">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="44718-153">Est inscrit en tant que [Singleton](dependency-injection.md#singleton) et peut être injecté dans n’importe quelle [durée de vie de service](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="44718-153">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="44718-154">Prend en charge :</span><span class="sxs-lookup"><span data-stu-id="44718-154">Supports:</span></span>
  - <span data-ttu-id="44718-155">Notifications de modifications</span><span class="sxs-lookup"><span data-stu-id="44718-155">Change notifications</span></span>
  - [<span data-ttu-id="44718-156">Options nommées</span><span class="sxs-lookup"><span data-stu-id="44718-156">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
  - [<span data-ttu-id="44718-157">Configuration rechargeable</span><span class="sxs-lookup"><span data-stu-id="44718-157">Reloadable configuration</span></span>](#use-ioptionssnapshot-to-read-updated-data)
  - <span data-ttu-id="44718-158">Invalidation sélective des options (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span><span class="sxs-lookup"><span data-stu-id="44718-158">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>
  
<span data-ttu-id="44718-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> est chargée de créer les instances d’options.</span><span class="sxs-lookup"><span data-stu-id="44718-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="44718-160">Elle dispose d’une seule méthode <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A>.</span><span class="sxs-lookup"><span data-stu-id="44718-160">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="44718-161">L’implémentation par défaut prend toutes les <xref:Microsoft.Extensions.Options.IConfigureOptions%601> et <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> inscrites et exécute toutes les configurations, puis les post-configurations.</span><span class="sxs-lookup"><span data-stu-id="44718-161">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="44718-162">Elle fait la distinction entre <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> et <xref:Microsoft.Extensions.Options.IConfigureOptions%601> et n’appelle que l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="44718-162">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="44718-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> est utilisée par <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> pour mettre en cache les instances `TOptions`.</span><span class="sxs-lookup"><span data-stu-id="44718-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="44718-164"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalide les instances des options dans le moniteur afin que la valeur soit recalculée (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span><span class="sxs-lookup"><span data-stu-id="44718-164">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="44718-165">Les valeurs peuvent aussi être introduites manuellement avec <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span><span class="sxs-lookup"><span data-stu-id="44718-165">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="44718-166">La méthode <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> est utilisée quand toutes les instances nommées doivent être recréées à la demande.</span><span class="sxs-lookup"><span data-stu-id="44718-166">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="44718-167">Utiliser IOptionsSnapshot pour lire les données mises à jour</span><span class="sxs-lookup"><span data-stu-id="44718-167">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="44718-168">Lorsque vous utilisez <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> , les options sont calculées une fois par demande lorsque vous y accédez et sont mises en cache pour la durée de vie de la demande.</span><span class="sxs-lookup"><span data-stu-id="44718-168">When you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="44718-169">Les modifications apportées à la configuration sont lues après le démarrage de l’application lors de l’utilisation de fournisseurs de configuration qui prennent en charge la lecture des valeurs de configuration mises</span><span class="sxs-lookup"><span data-stu-id="44718-169">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="44718-170">La différence entre `IOptionsMonitor` et `IOptionsSnapshot` est que :</span><span class="sxs-lookup"><span data-stu-id="44718-170">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="44718-171">`IOptionsMonitor` est un [service Singleton](dependency-injection.md#singleton) qui récupère les valeurs d’option actuelles à tout moment, ce qui est particulièrement utile dans les dépendances Singleton.</span><span class="sxs-lookup"><span data-stu-id="44718-171">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="44718-172">`IOptionsSnapshot` est un [service étendu](dependency-injection.md#scoped) et fournit un instantané des options au moment de la construction de l' `IOptionsSnapshot<T>` objet.</span><span class="sxs-lookup"><span data-stu-id="44718-172">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="44718-173">Les instantanés d’options sont conçus pour être utilisés avec des dépendances transitoires et délimitées.</span><span class="sxs-lookup"><span data-stu-id="44718-173">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="44718-174">Le code suivant utilise <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> .</span><span class="sxs-lookup"><span data-stu-id="44718-174">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="44718-175">Le code suivant inscrit une instance de configuration qui se `TransientFaultHandlingOptions` lie à :</span><span class="sxs-lookup"><span data-stu-id="44718-175">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="44718-176">Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.</span><span class="sxs-lookup"><span data-stu-id="44718-176">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="44718-177">IOptionsMonitor</span><span class="sxs-lookup"><span data-stu-id="44718-177">IOptionsMonitor</span></span>

<span data-ttu-id="44718-178">Le code suivant inscrit une instance de configuration qui est `TransientFaultHandlingOptions` liée à.</span><span class="sxs-lookup"><span data-stu-id="44718-178">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="44718-179">L'exemple suivant utilise <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> :</span><span class="sxs-lookup"><span data-stu-id="44718-179">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="44718-180">Dans le code précédent, les modifications apportées au fichier de configuration JSON après le démarrage de l’application sont lues.</span><span class="sxs-lookup"><span data-stu-id="44718-180">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="44718-181">Prise en charge des options nommées à l’aide de IConfigureNamedOptions</span><span class="sxs-lookup"><span data-stu-id="44718-181">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="44718-182">Options nommées :</span><span class="sxs-lookup"><span data-stu-id="44718-182">Named options:</span></span>

- <span data-ttu-id="44718-183">Sont utiles lorsque plusieurs sections de configuration sont liées aux mêmes propriétés.</span><span class="sxs-lookup"><span data-stu-id="44718-183">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="44718-184">Respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="44718-184">Are case-sensitive.</span></span>

<span data-ttu-id="44718-185">Prenez en compte les _appsettings.jssuivantes sur le fichier \* :</span><span class="sxs-lookup"><span data-stu-id="44718-185">Consider the following _appsettings.json\* file:</span></span>

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

<span data-ttu-id="44718-186">Au lieu de créer deux classes pour lier `Features:Personalize` et `Features:WeatherStation` , la classe suivante est utilisée pour chaque section :</span><span class="sxs-lookup"><span data-stu-id="44718-186">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="44718-187">Le code suivant configure les options nommées :</span><span class="sxs-lookup"><span data-stu-id="44718-187">The following code configures the named options:</span></span>

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

<span data-ttu-id="44718-188">Le code suivant affiche les options nommées :</span><span class="sxs-lookup"><span data-stu-id="44718-188">The following code displays the named options:</span></span>

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

<span data-ttu-id="44718-189">Toutes les options sont des instances nommées.</span><span class="sxs-lookup"><span data-stu-id="44718-189">All options are named instances.</span></span> <span data-ttu-id="44718-190"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> les instances sont traitées comme ciblant l' `Options.DefaultName` instance, qui est `string.Empty` .</span><span class="sxs-lookup"><span data-stu-id="44718-190"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="44718-191">En outre, <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> implémente <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span><span class="sxs-lookup"><span data-stu-id="44718-191"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="44718-192">L’implémentation par défaut de <xref:Microsoft.Extensions.Options.IOptionsFactory%601> possède une logique qui utilise chaque élément de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="44718-192">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="44718-193">L' `null` option nommée est utilisée pour cibler toutes les instances nommées au lieu d’une instance nommée spécifique.</span><span class="sxs-lookup"><span data-stu-id="44718-193">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="44718-194"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> et <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> utilisent cette Convention.</span><span class="sxs-lookup"><span data-stu-id="44718-194"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="44718-195">API OptionsBuilder</span><span class="sxs-lookup"><span data-stu-id="44718-195">OptionsBuilder API</span></span>

<span data-ttu-id="44718-196"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> permet de configurer des instances `TOptions`.</span><span class="sxs-lookup"><span data-stu-id="44718-196"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="44718-197">`OptionsBuilder` simplifie la création d’options nommées. En effet, il est le seul paramètre de l’appel `AddOptions<TOptions>(string optionsName)` initial et n’apparaît pas dans les appels ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="44718-197">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="44718-198">La validation des options et les surcharges `ConfigureOptions` qui acceptent des dépendances de service sont uniquement disponibles avec `OptionsBuilder`.</span><span class="sxs-lookup"><span data-stu-id="44718-198">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="44718-199">`OptionsBuilder` est utilisé dans la section des [options de validation](#options-validation) .</span><span class="sxs-lookup"><span data-stu-id="44718-199">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="44718-200">Utiliser les services d’injection de dépendances (DI) pour configurer des options</span><span class="sxs-lookup"><span data-stu-id="44718-200">Use DI services to configure options</span></span>

<span data-ttu-id="44718-201">Les services sont accessibles à partir de l’injection de dépendances lors de la configuration des options de deux manières :</span><span class="sxs-lookup"><span data-stu-id="44718-201">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="44718-202">Transmettez un délégué de configuration à [configurer](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) sur [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span><span class="sxs-lookup"><span data-stu-id="44718-202">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="44718-203">`OptionsBuilder<TOptions>` fournit des surcharges de la [configuration](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) qui autorisent l’utilisation de cinq services au maximum pour configurer des options :</span><span class="sxs-lookup"><span data-stu-id="44718-203">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="44718-204">Créez un type qui implémente <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ou <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> et inscrit le type en tant que service.</span><span class="sxs-lookup"><span data-stu-id="44718-204">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="44718-205">Nous vous recommandons de transmettre un délégué de configuration à [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), car il est plus complexe de créer un service.</span><span class="sxs-lookup"><span data-stu-id="44718-205">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="44718-206">La création d’un type équivaut à ce que fait l’infrastructure lors de l’appel de [configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span><span class="sxs-lookup"><span data-stu-id="44718-206">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="44718-207">L’appel de [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) a pour effet d’inscrire une instance générique temporaire de <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, dont l’un des constructeurs accepte les types de service génériques spécifiés.</span><span class="sxs-lookup"><span data-stu-id="44718-207">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="44718-208">Validation des options</span><span class="sxs-lookup"><span data-stu-id="44718-208">Options validation</span></span>

<span data-ttu-id="44718-209">La validation des options permet de valider les valeurs d’option.</span><span class="sxs-lookup"><span data-stu-id="44718-209">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="44718-210">Prenez en compte les *appsettings.jssuivantes sur* le fichier :</span><span class="sxs-lookup"><span data-stu-id="44718-210">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="44718-211">La classe suivante crée une liaison avec la `"Settings"` section de configuration et applique deux `DataAnnotations` règles :</span><span class="sxs-lookup"><span data-stu-id="44718-211">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="44718-212">Le code suivant :</span><span class="sxs-lookup"><span data-stu-id="44718-212">The following code:</span></span>

- <span data-ttu-id="44718-213">Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> pour recevoir un [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) qui crée une liaison avec la `SettingsOptions` classe.</span><span class="sxs-lookup"><span data-stu-id="44718-213">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="44718-214">Appelle <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> pour activer la validation à l’aide de `DataAnnotations` .</span><span class="sxs-lookup"><span data-stu-id="44718-214">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="44718-215">La `ValidateDataAnnotations` méthode d’extension est définie dans le package NuGet [Microsoft. extensions. options. DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) .</span><span class="sxs-lookup"><span data-stu-id="44718-215">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="44718-216">Le code suivant affiche les valeurs de configuration ou les erreurs de validation :</span><span class="sxs-lookup"><span data-stu-id="44718-216">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="44718-217">Le code suivant applique une règle de validation plus complexe à l’aide d’un délégué :</span><span class="sxs-lookup"><span data-stu-id="44718-217">The following code applies a more complex validation rule using a delegate:</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="44718-218">IValidateOptions pour la validation complexe</span><span class="sxs-lookup"><span data-stu-id="44718-218">IValidateOptions for complex validation</span></span>

<span data-ttu-id="44718-219">La classe suivante implémente <xref:Microsoft.Extensions.Options.IValidateOptions%601> :</span><span class="sxs-lookup"><span data-stu-id="44718-219">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="44718-220">`IValidateOptions` permet de déplacer le code de validation dans une classe.</span><span class="sxs-lookup"><span data-stu-id="44718-220">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="44718-221">À l’aide du code précédent, la validation est activée dans `ConfigureServices` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="44718-221">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="44718-222">Options de post-configuration</span><span class="sxs-lookup"><span data-stu-id="44718-222">Options post-configuration</span></span>

<span data-ttu-id="44718-223">Définissez la post-configuration avec <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span><span class="sxs-lookup"><span data-stu-id="44718-223">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="44718-224">Après l’exécution de la configuration, une fois la configuration <xref:Microsoft.Extensions.Options.IConfigureOptions%601> effectuée, elle peut être utile dans les scénarios où vous devez remplacer la configuration :</span><span class="sxs-lookup"><span data-stu-id="44718-224">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="44718-225"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> permet de post-configurer les options nommées :</span><span class="sxs-lookup"><span data-stu-id="44718-225"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="44718-226">Utilisez <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> pour post-configurer toutes les instances de configuration :</span><span class="sxs-lookup"><span data-stu-id="44718-226">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="44718-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44718-227">See also</span></span>

- [<span data-ttu-id="44718-228">Configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="44718-228">Configuration in .NET</span></span>](configuration.md)
