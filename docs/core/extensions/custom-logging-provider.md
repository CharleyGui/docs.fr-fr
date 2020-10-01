---
title: Implémenter un fournisseur de journalisation personnalisé dans .NET
description: Découvrez comment implémenter un fournisseur de journalisation personnalisé dans vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.topic: how-to
ms.openlocfilehash: 3a0af6296c2ade15ff1b75dce5a5f99bfe235ebf
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614701"
---
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="4eb4f-103">Implémenter un fournisseur de journalisation personnalisé dans .NET</span><span class="sxs-lookup"><span data-stu-id="4eb4f-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="4eb4f-104">De nombreux [fournisseurs de journalisation](logging-providers.md) sont disponibles pour les besoins de journalisation courants.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="4eb4f-105">Vous devrez peut-être implémenter un personnalisé <xref:Microsoft.Extensions.Logging.ILoggerProvider> lorsque l’un des fournisseurs disponibles ne répond pas aux besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="4eb4f-106">Dans cet article, vous allez apprendre à implémenter un fournisseur de journalisation personnalisé qui peut être utilisé pour coloriser les journaux dans la console.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="4eb4f-107">Exemple de configuration d’un enregistreur d’événements personnalisé</span><span class="sxs-lookup"><span data-stu-id="4eb4f-107">Sample custom logger configuration</span></span>

<span data-ttu-id="4eb4f-108">L’exemple crée différentes entrées de console couleur par niveau de journalisation et ID d’événement en utilisant le type de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="4eb4f-109">Le code précédent définit le niveau par défaut à `Information` , la couleur à `Green` et `EventId` est implicitement `0` .</span><span class="sxs-lookup"><span data-stu-id="4eb4f-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="4eb4f-110">Créer l’enregistreur d’événements personnalisé</span><span class="sxs-lookup"><span data-stu-id="4eb4f-110">Create the custom logger</span></span>

<span data-ttu-id="4eb4f-111">Le `ILogger` nom de catégorie d’implémentation correspond généralement à la source de journalisation.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="4eb4f-112">Par exemple, le type dans lequel l’enregistreur d’événements est créé :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="4eb4f-113">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-113">The preceding code:</span></span>

- <span data-ttu-id="4eb4f-114">Crée une instance d’enregistreur d’événements par nom de catégorie.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="4eb4f-115">Archive `logLevel == _config.LogLevel` `IsEnabled` , donc chaque `logLevel` a un enregistreur d’événements unique.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-115">Checks `logLevel == _config.LogLevel` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="4eb4f-116">Les journaux doivent également être activés pour tous les niveaux de journalisation plus élevés :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="4eb4f-117">Fournisseur d’enregistreur d’événements personnalisé</span><span class="sxs-lookup"><span data-stu-id="4eb4f-117">Custom logger provider</span></span>

<span data-ttu-id="4eb4f-118">L' `ILoggerProvider` objet est chargé de créer des instances de journal.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="4eb4f-119">Il n’est peut-être pas nécessaire de créer une instance d’enregistreur d’événements par catégorie, mais cela est logique pour certains enregistreurs d’événements, tels que NLog ou log4net.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="4eb4f-120">En procédant ainsi, vous pouvez choisir différentes cibles de sortie de journalisation par catégorie, si nécessaire :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="4eb4f-121">Dans le code précédent, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> crée une seule instance de `ColorConsoleLogger` par nom de catégorie et le stocke dans le [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) .</span><span class="sxs-lookup"><span data-stu-id="4eb4f-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="4eb4f-122">Utilisation et inscription de l’enregistreur d’événements personnalisé</span><span class="sxs-lookup"><span data-stu-id="4eb4f-122">Usage and registration of the custom logger</span></span>

<span data-ttu-id="4eb4f-123">Pour ajouter le fournisseur de journalisation personnalisé et le journal correspondant, ajoutez un <xref:Microsoft.Extensions.Logging.ILoggerProvider> avec <xref:Microsoft.Extensions.Logging.ILoggingBuilder> à partir de <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-123">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

<span data-ttu-id="4eb4f-124">Le `ILoggingBuilder` crée une ou plusieurs `ILogger` instances.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-124">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="4eb4f-125">Les `ILogger` instances sont utilisées par le Framework pour enregistrer les informations.</span><span class="sxs-lookup"><span data-stu-id="4eb4f-125">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="4eb4f-126">Pour le code précédent, fournissez au moins une méthode d’extension pour le `ILoggerFactory` :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-126">For the preceding code, provide at least one extension method for the `ILoggerFactory`:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="4eb4f-127">L’exécution de cette application simple s’affiche comme dans la fenêtre de console suivante :</span><span class="sxs-lookup"><span data-stu-id="4eb4f-127">Running this simple application will render similar to the following console window:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="Sortie de l’exemple de journal de console Color":::

## <a name="see-also"></a><span data-ttu-id="4eb4f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eb4f-129">See also</span></span>

- <span data-ttu-id="4eb4f-130">[Journalisation dans .net](logging.md).</span><span class="sxs-lookup"><span data-stu-id="4eb4f-130">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="4eb4f-131">[Fournisseurs de journalisation dans .net](logging-providers.md).</span><span class="sxs-lookup"><span data-stu-id="4eb4f-131">[Logging providers in .NET](logging-providers.md).</span></span>
- <span data-ttu-id="4eb4f-132">[Journalisation hautes performances dans .net](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="4eb4f-132">[High-performance logging in .NET](high-performance-logging.md).</span></span>
