---
title: Journalisation avec le kit de développement logiciel (SDK) Azure pour .NET
description: Découvrez comment activer la journalisation avec le kit de développement logiciel (SDK) Azure pour les bibliothèques clientes .NET
ms.date: 03/20/2020
ms.custom: devx-track-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 6adc485867e9bad401a15da19e6cb4424d2ddb13
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700708"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>Journalisation avec le kit de développement logiciel (SDK) Azure pour .NET

Le [Kit de développement logiciel (SDK) Azure](https://azure.microsoft.com/downloads/) pour les bibliothèques clientes .net offre la possibilité de journaliser les opérations de la bibliothèque cliente. Cela vous permet de surveiller les demandes d’e/s et les réponses que les bibliothèques clientes effectuent aux services Azure. En règle générale, les journaux sont utilisés pour déboguer ou diagnostiquer des problèmes de communication. Cet article décrit trois approches pour activer la journalisation avec le kit de développement logiciel (SDK) Azure pour .NET :

- Consigner dans la fenêtre de console
- Journalisation des traces de Diagnostics .NET
- Configurer la journalisation personnalisée

> [!IMPORTANT]
> Cet article s’applique aux bibliothèques clientes qui utilisent les versions les plus récentes du kit de développement logiciel (SDK) Azure pour .NET. Pour savoir si une bibliothèque est prise en charge, reportez-vous à la liste des [versions les plus récentes du SDK Azure](https://azure.github.io/azure-sdk/releases/latest/index.html). Si votre application utilise une version antérieure des bibliothèques de client du SDK Azure, reportez-vous aux instructions spécifiques de la documentation du service applicable.

## <a name="log-information"></a>Enregistrement d’informations

Le kit de développement logiciel (SDK) enregistre les informations suivantes, en assainiant les valeurs d’en-tête et de requête de paramètre pour supprimer les données personnelles.

Entrée du journal de la requête HTTP :

- ID unique
- HTTP method
- URI
- En-têtes de demande sortants

Entrée du journal de réponse HTTP :

- Durée de l’opération d’e/s (temps écoulé)
- ID de la demande
- Code d'état HTTP
- Phrase de raison HTTP
- En-têtes de réponse
- Informations sur l’erreur, le cas échéant

Pour le contenu de la demande et de la réponse :

- Flux de contenu sous forme de texte ou d’octets en fonction de l’en-tête Content-type.
     > [! Remarque} la journalisation du contenu est désactivée par défaut. Pour l’activer, affectez à la valeur `Diagnostics.IsLoggingContentEnabled` `true` dans `ClientOptions` .

Les journaux des événements sont généralement générés à l’un de ces trois niveaux :

- Informations pour les événements de demande et de réponse
- Avertissement pour les erreurs
- Commentaires pour les messages détaillés et la journalisation du contenu

## <a name="enable-logging-with-built-in-methods"></a>Activer la journalisation avec les méthodes intégrées

Le kit de développement logiciel (SDK) Azure pour les bibliothèques clientes .NET enregistre les événements à Suivi d’v nements pour Windows (ETW) via la [ `EventSource` classe](/dotnet/api/system.diagnostics.tracing.eventsource), qui est classique pour .net. Les sources d’événements vous permettent d’utiliser la journalisation structurée dans votre code d’application avec une surcharge de performances minimale. Pour accéder à ces journaux des événements, vous devez enregistrer les écouteurs d’événements.

Le kit de développement logiciel (SDK) inclut la `Azure.Core.Diagnostics.AzureEventSourceListener` classe (définie dans le package NuGet Azure. Core), qui contient deux méthodes statiques qui simplifient la journalisation complète de votre application .net : `CreateConsoleLogger` et `CreateTraceLogger` . Ces méthodes prennent un paramètre facultatif qui spécifie un niveau de journalisation.

### <a name="log-to-the-console-window"></a>Consigner dans la fenêtre de console

Un principe fondamental du kit de développement logiciel (SDK) Azure pour les bibliothèques clientes .NET est de simplifier la possibilité d’afficher des journaux complets en temps réel. La `CreateConsoleLogger` méthode vous permet d’envoyer des journaux à la fenêtre de console à l’aide d’une seule ligne de code :

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Consigner dans les suivis de diagnostic

Si vous implémentez des écouteurs de suivi, vous pouvez utiliser la `CreateTraceLogger` méthode pour vous connecter au mécanisme de suivi d’événements .NET standard ( [`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing) ). Pour plus d’informations sur le suivi d’événements dans .NET, consultez [écouteurs de suivi](../framework/debug-trace-profile/trace-listeners.md). Cet exemple spécifie un niveau de journal détaillé :

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Configurer la journalisation personnalisée

Comme indiqué ci-dessus, vous devez enregistrer les écouteurs d’événements pour recevoir des messages du journal à partir du kit de développement logiciel (SDK) Azure pour .NET. Si vous ne souhaitez pas implémenter une journalisation complète à l’aide d’une des méthodes simplifiées ci-dessus, vous pouvez construire une instance de la `AzureEventSourceListener` classe et la passer à une fonction de rappel que vous écrivez. Cette méthode recevra les messages du journal que vous pouvez traiter, mais vous devez le faire. En outre, lorsque vous construisez l’instance, vous pouvez spécifier les niveaux de journalisation à inclure.

L’exemple suivant crée un écouteur d’événements qui se connecte à la console à l’aide d’un message personnalisé, et est filtré en événements Azure Core de niveau détaillé.

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a>Étapes suivantes

- [Activer la journalisation des diagnostics pour les applications dans Azure App Service](/azure/app-service/troubleshoot-diagnostic-logs)
- Passer en revue [les options d’audit et de journalisation de sécurité Azure](/azure/security/fundamentals/log-audit)
- Découvrez comment utiliser les journaux de la [plateforme Azure](/azure/azure-monitor/platform/platform-logs-overview)
- En savoir plus sur la [journalisation et le suivi de .net Core](../core/diagnostics/logging-tracing.md)
