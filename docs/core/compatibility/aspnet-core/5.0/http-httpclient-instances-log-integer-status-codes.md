---
title: 'Modification avec rupture : instances HTTP : HttpClient créées par IHttpClientFactory journaux des codes d’état des entiers'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée HTTP : instances HttpClient créées par les codes d’État entier du journal IHttpClientFactory'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 964c0a65a07816acea8016d42a66a6bf84aba7c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760840"
---
# <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="2b7fe-103">HTTP : instances HttpClient créées par IHttpClientFactory enregistrer les codes d’état des entiers</span><span class="sxs-lookup"><span data-stu-id="2b7fe-103">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="2b7fe-104"><xref:System.Net.Http.HttpClient> instances créées par <xref:System.Net.Http.IHttpClientFactory> les codes d’État http du journal sous forme d’entiers au lieu de noms de code d’État.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-104"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2b7fe-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2b7fe-105">Version introduced</span></span>

<span data-ttu-id="2b7fe-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="2b7fe-106">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="2b7fe-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="2b7fe-107">Old behavior</span></span>

<span data-ttu-id="2b7fe-108">La journalisation utilise les descriptions textuelles des codes d’état HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-108">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="2b7fe-109">Prenez en compte les messages de journal suivants :</span><span class="sxs-lookup"><span data-stu-id="2b7fe-109">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

## <a name="new-behavior"></a><span data-ttu-id="2b7fe-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="2b7fe-110">New behavior</span></span>

<span data-ttu-id="2b7fe-111">La journalisation utilise les valeurs entières des codes d’état HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-111">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="2b7fe-112">Prenez en compte les messages de journal suivants :</span><span class="sxs-lookup"><span data-stu-id="2b7fe-112">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

## <a name="reason-for-change"></a><span data-ttu-id="2b7fe-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2b7fe-113">Reason for change</span></span>

<span data-ttu-id="2b7fe-114">Le comportement d’origine de cette journalisation est incohérent avec d’autres parties de ASP.NET Core qui ont toujours utilisé des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-114">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="2b7fe-115">L’incohérence rend les journaux difficiles à interroger par le biais de systèmes de journalisation structurés tels que [Elasticsearch](https://www.elastic.co/elasticsearch/).</span><span class="sxs-lookup"><span data-stu-id="2b7fe-115">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="2b7fe-116">Pour plus de contexte, consultez [dotnet/extensions # 1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="2b7fe-116">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="2b7fe-117">L’utilisation de valeurs entières est plus souple que le texte, car elle autorise des requêtes sur des plages de valeurs.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-117">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="2b7fe-118">L’ajout d’une autre valeur de journal pour capturer le code d’État entier a été pris en compte.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-118">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="2b7fe-119">Malheureusement, cela introduirait une autre incohérence avec le reste de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-119">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="2b7fe-120">La journalisation HttpClient et la journalisation du serveur/de l’hébergement HTTP utilisent déjà le même `StatusCode` nom de clé.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-120">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2b7fe-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2b7fe-121">Recommended action</span></span>

<span data-ttu-id="2b7fe-122">La meilleure option consiste à mettre à jour les requêtes de journalisation pour utiliser les valeurs entières des codes d’État.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-122">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="2b7fe-123">Cette option peut entraîner des difficultés à écrire des requêtes sur plusieurs versions de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-123">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="2b7fe-124">Toutefois, l’utilisation d’entiers à cet effet est bien plus flexible pour l’interrogation des journaux.</span><span class="sxs-lookup"><span data-stu-id="2b7fe-124">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="2b7fe-125">Si vous devez forcer la compatibilité avec l’ancien comportement et utiliser des codes d’État textuels, remplacez la `IHttpClientFactory` journalisation par les vôtres :</span><span class="sxs-lookup"><span data-stu-id="2b7fe-125">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="2b7fe-126">Copiez les versions .NET Core 3,1 des classes suivantes dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="2b7fe-126">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="2b7fe-127">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="2b7fe-127">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="2b7fe-128">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="2b7fe-128">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="2b7fe-129">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="2b7fe-129">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="2b7fe-130">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="2b7fe-130">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="2b7fe-131">Renommez les classes pour éviter les conflits avec les types publics dans le package NuGet [Microsoft. extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) .</span><span class="sxs-lookup"><span data-stu-id="2b7fe-131">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="2b7fe-132">Remplacez l’implémentation intégrée de par le `LoggingHttpMessageHandlerBuilderFilter` vôtre dans la méthode du projet `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="2b7fe-132">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="2b7fe-133">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2b7fe-133">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        services.RemoveAll<IHttpMessageHandlerBuilderFilter>();

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="2b7fe-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="2b7fe-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:System.Net.Http.HttpClient`

-->
