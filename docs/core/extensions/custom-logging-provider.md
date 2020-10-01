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
# <a name="implement-a-custom-logging-provider-in-net"></a>Implémenter un fournisseur de journalisation personnalisé dans .NET

De nombreux [fournisseurs de journalisation](logging-providers.md) sont disponibles pour les besoins de journalisation courants. Vous devrez peut-être implémenter un personnalisé <xref:Microsoft.Extensions.Logging.ILoggerProvider> lorsque l’un des fournisseurs disponibles ne répond pas aux besoins de votre application. Dans cet article, vous allez apprendre à implémenter un fournisseur de journalisation personnalisé qui peut être utilisé pour coloriser les journaux dans la console.

### <a name="sample-custom-logger-configuration"></a>Exemple de configuration d’un enregistreur d’événements personnalisé

L’exemple crée différentes entrées de console couleur par niveau de journalisation et ID d’événement en utilisant le type de configuration suivant :

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

Le code précédent définit le niveau par défaut à `Information` , la couleur à `Green` et `EventId` est implicitement `0` .

### <a name="create-the-custom-logger"></a>Créer l’enregistreur d’événements personnalisé

Le `ILogger` nom de catégorie d’implémentation correspond généralement à la source de journalisation. Par exemple, le type dans lequel l’enregistreur d’événements est créé :

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

Le code précédent :

- Crée une instance d’enregistreur d’événements par nom de catégorie.
- Archive `logLevel == _config.LogLevel` `IsEnabled` , donc chaque `logLevel` a un enregistreur d’événements unique. Les journaux doivent également être activés pour tous les niveaux de journalisation plus élevés :

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a>Fournisseur d’enregistreur d’événements personnalisé

L' `ILoggerProvider` objet est chargé de créer des instances de journal. Il n’est peut-être pas nécessaire de créer une instance d’enregistreur d’événements par catégorie, mais cela est logique pour certains enregistreurs d’événements, tels que NLog ou log4net. En procédant ainsi, vous pouvez choisir différentes cibles de sortie de journalisation par catégorie, si nécessaire :

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

Dans le code précédent, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> crée une seule instance de `ColorConsoleLogger` par nom de catégorie et le stocke dans le [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) .

## <a name="usage-and-registration-of-the-custom-logger"></a>Utilisation et inscription de l’enregistreur d’événements personnalisé

Pour ajouter le fournisseur de journalisation personnalisé et le journal correspondant, ajoutez un <xref:Microsoft.Extensions.Logging.ILoggerProvider> avec <xref:Microsoft.Extensions.Logging.ILoggingBuilder> à partir de <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

Le `ILoggingBuilder` crée une ou plusieurs `ILogger` instances. Les `ILogger` instances sont utilisées par le Framework pour enregistrer les informations.

Pour le code précédent, fournissez au moins une méthode d’extension pour le `ILoggerFactory` :

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

L’exécution de cette application simple s’affiche comme dans la fenêtre de console suivante :

:::image type="content" source="media/color-console-logger.png" alt-text="Sortie de l’exemple de journal de console Color":::

## <a name="see-also"></a>Voir aussi

- [Journalisation dans .net](logging.md).
- [Fournisseurs de journalisation dans .net](logging-providers.md).
- [Journalisation hautes performances dans .net](high-performance-logging.md).
