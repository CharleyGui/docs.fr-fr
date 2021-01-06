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
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="57979-103">Journalisation avec le kit de développement logiciel (SDK) Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="57979-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="57979-104">Le [Kit de développement logiciel (SDK) Azure](https://azure.microsoft.com/downloads/) pour les bibliothèques clientes .net offre la possibilité de journaliser les opérations de la bibliothèque cliente.</span><span class="sxs-lookup"><span data-stu-id="57979-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="57979-105">Cela vous permet de surveiller les demandes d’e/s et les réponses que les bibliothèques clientes effectuent aux services Azure.</span><span class="sxs-lookup"><span data-stu-id="57979-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="57979-106">En règle générale, les journaux sont utilisés pour déboguer ou diagnostiquer des problèmes de communication.</span><span class="sxs-lookup"><span data-stu-id="57979-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="57979-107">Cet article décrit trois approches pour activer la journalisation avec le kit de développement logiciel (SDK) Azure pour .NET :</span><span class="sxs-lookup"><span data-stu-id="57979-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="57979-108">Consigner dans la fenêtre de console</span><span class="sxs-lookup"><span data-stu-id="57979-108">Log to the console window</span></span>
- <span data-ttu-id="57979-109">Journalisation des traces de Diagnostics .NET</span><span class="sxs-lookup"><span data-stu-id="57979-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="57979-110">Configurer la journalisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="57979-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57979-111">Cet article s’applique aux bibliothèques clientes qui utilisent les versions les plus récentes du kit de développement logiciel (SDK) Azure pour .NET.</span><span class="sxs-lookup"><span data-stu-id="57979-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="57979-112">Pour savoir si une bibliothèque est prise en charge, reportez-vous à la liste des [versions les plus récentes du SDK Azure](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="57979-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="57979-113">Si votre application utilise une version antérieure des bibliothèques de client du SDK Azure, reportez-vous aux instructions spécifiques de la documentation du service applicable.</span><span class="sxs-lookup"><span data-stu-id="57979-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="57979-114">Enregistrement d’informations</span><span class="sxs-lookup"><span data-stu-id="57979-114">Log information</span></span>

<span data-ttu-id="57979-115">Le kit de développement logiciel (SDK) enregistre les informations suivantes, en assainiant les valeurs d’en-tête et de requête de paramètre pour supprimer les données personnelles.</span><span class="sxs-lookup"><span data-stu-id="57979-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="57979-116">Entrée du journal de la requête HTTP :</span><span class="sxs-lookup"><span data-stu-id="57979-116">HTTP request log entry:</span></span>

- <span data-ttu-id="57979-117">ID unique</span><span class="sxs-lookup"><span data-stu-id="57979-117">Unique ID</span></span>
- <span data-ttu-id="57979-118">HTTP method</span><span class="sxs-lookup"><span data-stu-id="57979-118">HTTP method</span></span>
- <span data-ttu-id="57979-119">URI</span><span class="sxs-lookup"><span data-stu-id="57979-119">URI</span></span>
- <span data-ttu-id="57979-120">En-têtes de demande sortants</span><span class="sxs-lookup"><span data-stu-id="57979-120">Outgoing request headers</span></span>

<span data-ttu-id="57979-121">Entrée du journal de réponse HTTP :</span><span class="sxs-lookup"><span data-stu-id="57979-121">HTTP response log entry:</span></span>

- <span data-ttu-id="57979-122">Durée de l’opération d’e/s (temps écoulé)</span><span class="sxs-lookup"><span data-stu-id="57979-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="57979-123">ID de la demande</span><span class="sxs-lookup"><span data-stu-id="57979-123">Request ID</span></span>
- <span data-ttu-id="57979-124">Code d'état HTTP</span><span class="sxs-lookup"><span data-stu-id="57979-124">HTTP status code</span></span>
- <span data-ttu-id="57979-125">Phrase de raison HTTP</span><span class="sxs-lookup"><span data-stu-id="57979-125">HTTP reason phrase</span></span>
- <span data-ttu-id="57979-126">En-têtes de réponse</span><span class="sxs-lookup"><span data-stu-id="57979-126">Response headers</span></span>
- <span data-ttu-id="57979-127">Informations sur l’erreur, le cas échéant</span><span class="sxs-lookup"><span data-stu-id="57979-127">Error information, when applicable</span></span>

<span data-ttu-id="57979-128">Pour le contenu de la demande et de la réponse :</span><span class="sxs-lookup"><span data-stu-id="57979-128">For request and response content:</span></span>

- <span data-ttu-id="57979-129">Flux de contenu sous forme de texte ou d’octets en fonction de l’en-tête Content-type.</span><span class="sxs-lookup"><span data-stu-id="57979-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="57979-130">[! Remarque} la journalisation du contenu est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="57979-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="57979-131">Pour l’activer, affectez à la valeur `Diagnostics.IsLoggingContentEnabled` `true` dans `ClientOptions` .</span><span class="sxs-lookup"><span data-stu-id="57979-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="57979-132">Les journaux des événements sont généralement générés à l’un de ces trois niveaux :</span><span class="sxs-lookup"><span data-stu-id="57979-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="57979-133">Informations pour les événements de demande et de réponse</span><span class="sxs-lookup"><span data-stu-id="57979-133">Informational for request and response events</span></span>
- <span data-ttu-id="57979-134">Avertissement pour les erreurs</span><span class="sxs-lookup"><span data-stu-id="57979-134">Warning for errors</span></span>
- <span data-ttu-id="57979-135">Commentaires pour les messages détaillés et la journalisation du contenu</span><span class="sxs-lookup"><span data-stu-id="57979-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="57979-136">Activer la journalisation avec les méthodes intégrées</span><span class="sxs-lookup"><span data-stu-id="57979-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="57979-137">Le kit de développement logiciel (SDK) Azure pour les bibliothèques clientes .NET enregistre les événements à Suivi d’v nements pour Windows (ETW) via la [ `EventSource` classe](/dotnet/api/system.diagnostics.tracing.eventsource), qui est classique pour .net.</span><span class="sxs-lookup"><span data-stu-id="57979-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="57979-138">Les sources d’événements vous permettent d’utiliser la journalisation structurée dans votre code d’application avec une surcharge de performances minimale.</span><span class="sxs-lookup"><span data-stu-id="57979-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="57979-139">Pour accéder à ces journaux des événements, vous devez enregistrer les écouteurs d’événements.</span><span class="sxs-lookup"><span data-stu-id="57979-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="57979-140">Le kit de développement logiciel (SDK) inclut la `Azure.Core.Diagnostics.AzureEventSourceListener` classe (définie dans le package NuGet Azure. Core), qui contient deux méthodes statiques qui simplifient la journalisation complète de votre application .net : `CreateConsoleLogger` et `CreateTraceLogger` .</span><span class="sxs-lookup"><span data-stu-id="57979-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="57979-141">Ces méthodes prennent un paramètre facultatif qui spécifie un niveau de journalisation.</span><span class="sxs-lookup"><span data-stu-id="57979-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="57979-142">Consigner dans la fenêtre de console</span><span class="sxs-lookup"><span data-stu-id="57979-142">Log to the console window</span></span>

<span data-ttu-id="57979-143">Un principe fondamental du kit de développement logiciel (SDK) Azure pour les bibliothèques clientes .NET est de simplifier la possibilité d’afficher des journaux complets en temps réel.</span><span class="sxs-lookup"><span data-stu-id="57979-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="57979-144">La `CreateConsoleLogger` méthode vous permet d’envoyer des journaux à la fenêtre de console à l’aide d’une seule ligne de code :</span><span class="sxs-lookup"><span data-stu-id="57979-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="57979-145">Consigner dans les suivis de diagnostic</span><span class="sxs-lookup"><span data-stu-id="57979-145">Log to diagnostic traces</span></span>

<span data-ttu-id="57979-146">Si vous implémentez des écouteurs de suivi, vous pouvez utiliser la `CreateTraceLogger` méthode pour vous connecter au mécanisme de suivi d’événements .NET standard ( [`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing) ).</span><span class="sxs-lookup"><span data-stu-id="57979-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="57979-147">Pour plus d’informations sur le suivi d’événements dans .NET, consultez [écouteurs de suivi](../framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="57979-147">For more information on event tracing in .NET, see [Trace Listeners](../framework/debug-trace-profile/trace-listeners.md).</span></span> <span data-ttu-id="57979-148">Cet exemple spécifie un niveau de journal détaillé :</span><span class="sxs-lookup"><span data-stu-id="57979-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="57979-149">Configurer la journalisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="57979-149">Configure custom logging</span></span>

<span data-ttu-id="57979-150">Comme indiqué ci-dessus, vous devez enregistrer les écouteurs d’événements pour recevoir des messages du journal à partir du kit de développement logiciel (SDK) Azure pour .NET.</span><span class="sxs-lookup"><span data-stu-id="57979-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="57979-151">Si vous ne souhaitez pas implémenter une journalisation complète à l’aide d’une des méthodes simplifiées ci-dessus, vous pouvez construire une instance de la `AzureEventSourceListener` classe et la passer à une fonction de rappel que vous écrivez.</span><span class="sxs-lookup"><span data-stu-id="57979-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="57979-152">Cette méthode recevra les messages du journal que vous pouvez traiter, mais vous devez le faire.</span><span class="sxs-lookup"><span data-stu-id="57979-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="57979-153">En outre, lorsque vous construisez l’instance, vous pouvez spécifier les niveaux de journalisation à inclure.</span><span class="sxs-lookup"><span data-stu-id="57979-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="57979-154">L’exemple suivant crée un écouteur d’événements qui se connecte à la console à l’aide d’un message personnalisé, et est filtré en événements Azure Core de niveau détaillé.</span><span class="sxs-lookup"><span data-stu-id="57979-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="57979-155">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="57979-155">Next steps</span></span>

- [<span data-ttu-id="57979-156">Activer la journalisation des diagnostics pour les applications dans Azure App Service</span><span class="sxs-lookup"><span data-stu-id="57979-156">Enable diagnostics logging for apps in Azure App Service</span></span>](/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="57979-157">Passer en revue [les options d’audit et de journalisation de sécurité Azure](/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="57979-157">Review [Azure security logging and auditing](/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="57979-158">Découvrez comment utiliser les journaux de la [plateforme Azure](/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="57979-158">Learn how to work with [Azure platform logs](/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="57979-159">En savoir plus sur la [journalisation et le suivi de .net Core](../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="57979-159">Read more about [.NET Core logging and tracing](../core/diagnostics/logging-tracing.md)</span></span>
