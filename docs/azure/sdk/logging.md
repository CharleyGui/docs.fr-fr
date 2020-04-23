---
title: Enregistrement avec l’Azure SDK pour .NET
description: Découvrez comment activer la connexion avec l’Azure SDK pour les bibliothèques clients .NET
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071989"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>Enregistrement avec l’Azure SDK pour .NET

Le [Azure SDK](https://azure.microsoft.com/downloads/) pour les bibliothèques clients .NET inclut la possibilité de connecter les opérations de bibliothèque client. Cela vous permet de surveiller les demandes et les réponses I/O que les bibliothèques clientes font aux services Azure. En règle générale, les journaux sont utilisés pour débocher ou diagnostiquer les problèmes de communication. Cet article décrit trois approches pour permettre l’enregistrement avec l’Azure SDK pour .NET:

- Connectez-vous à la fenêtre de la console
- Log to .NET diagnostics traces
- Configurer l’enregistrement personnalisé

> [!IMPORTANT]
> Cet article s’applique aux bibliothèques de clients qui utilisent les versions les plus récentes de l’Azure SDK pour .NET. Pour voir si une bibliothèque est prise en charge, consultez la liste des [dernières versions azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html). Si votre application utilise une ancienne version des bibliothèques de clients Azure SDK, consultez des instructions spécifiques dans la documentation de service applicable.

## <a name="log-information"></a>Enregistrement d’informations

Le SDK enregistre les informations suivantes, désinfectant les requêtes paramètres et les valeurs d’en-tête pour supprimer les données personnelles.

HTTP demande d’entrée de journal:

- ID unique
- HTTP method
- URI
- En-têtes de demande sortants

Entrée de journal de réponse HTTP :

- Durée de l’opération I/O (temps écoulé)
- ID de la demande
- Code d'état HTTP
- PHRASE de raison HTTP
- En-têtes de réponse
- Informations sur les erreurs, le cas échéant

Pour le contenu de demande et de réponse :

- Flux de contenu sous forme de texte ou d’octets en fonction de l’en-tête content-type.
     > [! NoteMD L’enregistrement de contenu est désactivé par défaut. Pour le permettre, `true` `ClientOptions`set `Diagnostics.IsLoggingContentEnabled` à .

Les journaux d’événements sont généralement en sortie à l’un de ces trois niveaux :

- Informations sur les événements de demande et d’intervention
- Avertissement pour les erreurs
- Verbose pour les messages détaillés et l’enregistrement de contenu

## <a name="enable-logging-with-built-in-methods"></a>Activer l’exploitation forestière avec des méthodes intégrées

L’Azure SDK pour .NET bibliothèques client journaux événements à [ `EventSource` ](/dotnet/api/system.diagnostics.tracing.eventsource)Event Tracing for Windows (ETW) via la classe , ce qui est typique pour .NET. Les sources d’événements vous permettent d’utiliser la connexion structurée dans votre code d’application avec un minimum de performances aériennes. Pour avoir accès à ces journaux d’événements, vous devez vous inscrire aux auditeurs de l’événement.

Le SDK `Azure.Core.Diagnostics.AzureEventSourceListener` comprend la classe (définie dans le paquet Azure.Core NuGet), qui contient deux `CreateConsoleLogger` `CreateTraceLogger`méthodes statiques qui simplifient la connexion complète pour votre application .NET: et . Ces méthodes prennent un paramètre facultatif qui spécifie un niveau de journal.

### <a name="log-to-the-console-window"></a>Connectez-vous à la fenêtre de la console

Un principe central de l’Azure SDK pour les bibliothèques clients .NET est de simplifier la possibilité de visualiser les journaux complets en temps réel. La `CreateConsoleLogger` méthode vous permet d’envoyer des journaux à la fenêtre de la console avec une seule ligne de code :

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Connexion aux traces diagnostiques

Si vous implémentez des `CreateTraceLogger` auditeurs de trace, vous pouvez[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)utiliser la méthode pour vous connecter au mécanisme standard de traçage d’événements .NET (). Pour plus d’informations sur le traçage des événements en .NET, voir [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners). Cet exemple spécifie un niveau de journal de verbose :

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Configurer l’enregistrement personnalisé

Comme mentionné ci-dessus, vous devez enregistrer les auditeurs de l’événement pour recevoir des messages journal de la SDK Azure pour .NET. Si vous ne souhaitez pas implémenter la connexion complète en utilisant `AzureEventSourceListener` l’une des méthodes simplifiées ci-dessus, vous pouvez construire une instance de la classe et lui passer une fonction de rappel que vous écrivez. Cette méthode recevra des messages journalaux que vous pouvez traiter comme vous en avez besoin. En outre, lorsque vous construisez l’instance, vous pouvez spécifier les niveaux de journal à inclure.

L’exemple suivant crée un auditeur d’événements qui se connecte à la console avec un message personnalisé, et est filtré pour les événements de base Azure du verbose de niveau.

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

- [Activer la journalisation des diagnostics pour les applications dans Azure App Service](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- Examiner les options [d’enregistrement et d’audit de sécurité Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)
- Apprenez à travailler avec [les journaux de la plate-forme Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)
- Lire la suite de [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)
