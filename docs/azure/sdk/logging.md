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
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="1feb9-103">Enregistrement avec l’Azure SDK pour .NET</span><span class="sxs-lookup"><span data-stu-id="1feb9-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="1feb9-104">Le [Azure SDK](https://azure.microsoft.com/downloads/) pour les bibliothèques clients .NET inclut la possibilité de connecter les opérations de bibliothèque client.</span><span class="sxs-lookup"><span data-stu-id="1feb9-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="1feb9-105">Cela vous permet de surveiller les demandes et les réponses I/O que les bibliothèques clientes font aux services Azure.</span><span class="sxs-lookup"><span data-stu-id="1feb9-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="1feb9-106">En règle générale, les journaux sont utilisés pour débocher ou diagnostiquer les problèmes de communication.</span><span class="sxs-lookup"><span data-stu-id="1feb9-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="1feb9-107">Cet article décrit trois approches pour permettre l’enregistrement avec l’Azure SDK pour .NET:</span><span class="sxs-lookup"><span data-stu-id="1feb9-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="1feb9-108">Connectez-vous à la fenêtre de la console</span><span class="sxs-lookup"><span data-stu-id="1feb9-108">Log to the console window</span></span>
- <span data-ttu-id="1feb9-109">Log to .NET diagnostics traces</span><span class="sxs-lookup"><span data-stu-id="1feb9-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="1feb9-110">Configurer l’enregistrement personnalisé</span><span class="sxs-lookup"><span data-stu-id="1feb9-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1feb9-111">Cet article s’applique aux bibliothèques de clients qui utilisent les versions les plus récentes de l’Azure SDK pour .NET.</span><span class="sxs-lookup"><span data-stu-id="1feb9-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="1feb9-112">Pour voir si une bibliothèque est prise en charge, consultez la liste des [dernières versions azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="1feb9-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="1feb9-113">Si votre application utilise une ancienne version des bibliothèques de clients Azure SDK, consultez des instructions spécifiques dans la documentation de service applicable.</span><span class="sxs-lookup"><span data-stu-id="1feb9-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="1feb9-114">Enregistrement d’informations</span><span class="sxs-lookup"><span data-stu-id="1feb9-114">Log information</span></span>

<span data-ttu-id="1feb9-115">Le SDK enregistre les informations suivantes, désinfectant les requêtes paramètres et les valeurs d’en-tête pour supprimer les données personnelles.</span><span class="sxs-lookup"><span data-stu-id="1feb9-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="1feb9-116">HTTP demande d’entrée de journal:</span><span class="sxs-lookup"><span data-stu-id="1feb9-116">HTTP request log entry:</span></span>

- <span data-ttu-id="1feb9-117">ID unique</span><span class="sxs-lookup"><span data-stu-id="1feb9-117">Unique ID</span></span>
- <span data-ttu-id="1feb9-118">HTTP method</span><span class="sxs-lookup"><span data-stu-id="1feb9-118">HTTP method</span></span>
- <span data-ttu-id="1feb9-119">URI</span><span class="sxs-lookup"><span data-stu-id="1feb9-119">URI</span></span>
- <span data-ttu-id="1feb9-120">En-têtes de demande sortants</span><span class="sxs-lookup"><span data-stu-id="1feb9-120">Outgoing request headers</span></span>

<span data-ttu-id="1feb9-121">Entrée de journal de réponse HTTP :</span><span class="sxs-lookup"><span data-stu-id="1feb9-121">HTTP response log entry:</span></span>

- <span data-ttu-id="1feb9-122">Durée de l’opération I/O (temps écoulé)</span><span class="sxs-lookup"><span data-stu-id="1feb9-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="1feb9-123">ID de la demande</span><span class="sxs-lookup"><span data-stu-id="1feb9-123">Request ID</span></span>
- <span data-ttu-id="1feb9-124">Code d'état HTTP</span><span class="sxs-lookup"><span data-stu-id="1feb9-124">HTTP status code</span></span>
- <span data-ttu-id="1feb9-125">PHRASE de raison HTTP</span><span class="sxs-lookup"><span data-stu-id="1feb9-125">HTTP reason phrase</span></span>
- <span data-ttu-id="1feb9-126">En-têtes de réponse</span><span class="sxs-lookup"><span data-stu-id="1feb9-126">Response headers</span></span>
- <span data-ttu-id="1feb9-127">Informations sur les erreurs, le cas échéant</span><span class="sxs-lookup"><span data-stu-id="1feb9-127">Error information, when applicable</span></span>

<span data-ttu-id="1feb9-128">Pour le contenu de demande et de réponse :</span><span class="sxs-lookup"><span data-stu-id="1feb9-128">For request and response content:</span></span>

- <span data-ttu-id="1feb9-129">Flux de contenu sous forme de texte ou d’octets en fonction de l’en-tête content-type.</span><span class="sxs-lookup"><span data-stu-id="1feb9-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="1feb9-130">[! NoteMD L’enregistrement de contenu est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="1feb9-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="1feb9-131">Pour le permettre, `true` `ClientOptions`set `Diagnostics.IsLoggingContentEnabled` à .</span><span class="sxs-lookup"><span data-stu-id="1feb9-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="1feb9-132">Les journaux d’événements sont généralement en sortie à l’un de ces trois niveaux :</span><span class="sxs-lookup"><span data-stu-id="1feb9-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="1feb9-133">Informations sur les événements de demande et d’intervention</span><span class="sxs-lookup"><span data-stu-id="1feb9-133">Informational for request and response events</span></span>
- <span data-ttu-id="1feb9-134">Avertissement pour les erreurs</span><span class="sxs-lookup"><span data-stu-id="1feb9-134">Warning for errors</span></span>
- <span data-ttu-id="1feb9-135">Verbose pour les messages détaillés et l’enregistrement de contenu</span><span class="sxs-lookup"><span data-stu-id="1feb9-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="1feb9-136">Activer l’exploitation forestière avec des méthodes intégrées</span><span class="sxs-lookup"><span data-stu-id="1feb9-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="1feb9-137">L’Azure SDK pour .NET bibliothèques client journaux événements à [ `EventSource` ](/dotnet/api/system.diagnostics.tracing.eventsource)Event Tracing for Windows (ETW) via la classe , ce qui est typique pour .NET.</span><span class="sxs-lookup"><span data-stu-id="1feb9-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="1feb9-138">Les sources d’événements vous permettent d’utiliser la connexion structurée dans votre code d’application avec un minimum de performances aériennes.</span><span class="sxs-lookup"><span data-stu-id="1feb9-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="1feb9-139">Pour avoir accès à ces journaux d’événements, vous devez vous inscrire aux auditeurs de l’événement.</span><span class="sxs-lookup"><span data-stu-id="1feb9-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="1feb9-140">Le SDK `Azure.Core.Diagnostics.AzureEventSourceListener` comprend la classe (définie dans le paquet Azure.Core NuGet), qui contient deux `CreateConsoleLogger` `CreateTraceLogger`méthodes statiques qui simplifient la connexion complète pour votre application .NET: et .</span><span class="sxs-lookup"><span data-stu-id="1feb9-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="1feb9-141">Ces méthodes prennent un paramètre facultatif qui spécifie un niveau de journal.</span><span class="sxs-lookup"><span data-stu-id="1feb9-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="1feb9-142">Connectez-vous à la fenêtre de la console</span><span class="sxs-lookup"><span data-stu-id="1feb9-142">Log to the console window</span></span>

<span data-ttu-id="1feb9-143">Un principe central de l’Azure SDK pour les bibliothèques clients .NET est de simplifier la possibilité de visualiser les journaux complets en temps réel.</span><span class="sxs-lookup"><span data-stu-id="1feb9-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="1feb9-144">La `CreateConsoleLogger` méthode vous permet d’envoyer des journaux à la fenêtre de la console avec une seule ligne de code :</span><span class="sxs-lookup"><span data-stu-id="1feb9-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="1feb9-145">Connexion aux traces diagnostiques</span><span class="sxs-lookup"><span data-stu-id="1feb9-145">Log to diagnostic traces</span></span>

<span data-ttu-id="1feb9-146">Si vous implémentez des `CreateTraceLogger` auditeurs de trace, vous pouvez[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)utiliser la méthode pour vous connecter au mécanisme standard de traçage d’événements .NET ().</span><span class="sxs-lookup"><span data-stu-id="1feb9-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="1feb9-147">Pour plus d’informations sur le traçage des événements en .NET, voir [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span><span class="sxs-lookup"><span data-stu-id="1feb9-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="1feb9-148">Cet exemple spécifie un niveau de journal de verbose :</span><span class="sxs-lookup"><span data-stu-id="1feb9-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="1feb9-149">Configurer l’enregistrement personnalisé</span><span class="sxs-lookup"><span data-stu-id="1feb9-149">Configure custom logging</span></span>

<span data-ttu-id="1feb9-150">Comme mentionné ci-dessus, vous devez enregistrer les auditeurs de l’événement pour recevoir des messages journal de la SDK Azure pour .NET.</span><span class="sxs-lookup"><span data-stu-id="1feb9-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="1feb9-151">Si vous ne souhaitez pas implémenter la connexion complète en utilisant `AzureEventSourceListener` l’une des méthodes simplifiées ci-dessus, vous pouvez construire une instance de la classe et lui passer une fonction de rappel que vous écrivez.</span><span class="sxs-lookup"><span data-stu-id="1feb9-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="1feb9-152">Cette méthode recevra des messages journalaux que vous pouvez traiter comme vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="1feb9-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="1feb9-153">En outre, lorsque vous construisez l’instance, vous pouvez spécifier les niveaux de journal à inclure.</span><span class="sxs-lookup"><span data-stu-id="1feb9-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="1feb9-154">L’exemple suivant crée un auditeur d’événements qui se connecte à la console avec un message personnalisé, et est filtré pour les événements de base Azure du verbose de niveau.</span><span class="sxs-lookup"><span data-stu-id="1feb9-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="1feb9-155">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1feb9-155">Next steps</span></span>

- [<span data-ttu-id="1feb9-156">Activer la journalisation des diagnostics pour les applications dans Azure App Service</span><span class="sxs-lookup"><span data-stu-id="1feb9-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="1feb9-157">Examiner les options [d’enregistrement et d’audit de sécurité Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="1feb9-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="1feb9-158">Apprenez à travailler avec [les journaux de la plate-forme Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="1feb9-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="1feb9-159">Lire la suite de [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="1feb9-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
