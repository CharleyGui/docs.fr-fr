---
ms.openlocfilehash: 44d33fb28e66e590e4604c6dd2c73616e4c5e943
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728305"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="314e5-101">HTTP : instances HttpClient créées par IHttpClientFactory enregistrer les codes d’état des entiers</span><span class="sxs-lookup"><span data-stu-id="314e5-101">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="314e5-102"><xref:System.Net.Http.HttpClient>instances créées par <xref:System.Net.Http.IHttpClientFactory> les codes d’État http du journal sous forme d’entiers au lieu de noms de code d’État.</span><span class="sxs-lookup"><span data-stu-id="314e5-102"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="314e5-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="314e5-103">Version introduced</span></span>

<span data-ttu-id="314e5-104">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="314e5-104">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="314e5-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="314e5-105">Old behavior</span></span>

<span data-ttu-id="314e5-106">La journalisation utilise les descriptions textuelles des codes d’état HTTP.</span><span class="sxs-lookup"><span data-stu-id="314e5-106">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="314e5-107">Prenez en compte les messages de journal suivants :</span><span class="sxs-lookup"><span data-stu-id="314e5-107">Consider the following log messages:</span></span>

```
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a><span data-ttu-id="314e5-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="314e5-108">New behavior</span></span>

<span data-ttu-id="314e5-109">La journalisation utilise les valeurs entières des codes d’état HTTP.</span><span class="sxs-lookup"><span data-stu-id="314e5-109">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="314e5-110">Prenez en compte les messages de journal suivants :</span><span class="sxs-lookup"><span data-stu-id="314e5-110">Consider the following log messages:</span></span>

```
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a><span data-ttu-id="314e5-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="314e5-111">Reason for change</span></span>

<span data-ttu-id="314e5-112">Le comportement d’origine de cette journalisation est incohérent avec d’autres parties de ASP.NET Core qui ont toujours utilisé des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="314e5-112">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="314e5-113">L’incohérence rend les journaux difficiles à interroger par le biais de systèmes de journalisation structurés tels que [Elasticsearch](https://www.elastic.co/elasticsearch/).</span><span class="sxs-lookup"><span data-stu-id="314e5-113">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="314e5-114">Pour plus de contexte, consultez [dotnet/extensions # 1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="314e5-114">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="314e5-115">L’utilisation de valeurs entières est plus souple que le texte, car elle autorise des requêtes sur des plages de valeurs.</span><span class="sxs-lookup"><span data-stu-id="314e5-115">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="314e5-116">L’ajout d’une autre valeur de journal pour capturer le code d’État entier a été pris en compte.</span><span class="sxs-lookup"><span data-stu-id="314e5-116">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="314e5-117">Malheureusement, cela introduirait une autre incohérence avec le reste de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="314e5-117">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="314e5-118">La journalisation HttpClient et la journalisation du serveur/de l’hébergement HTTP utilisent déjà le même `StatusCode` nom de clé.</span><span class="sxs-lookup"><span data-stu-id="314e5-118">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="314e5-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="314e5-119">Recommended action</span></span>

<span data-ttu-id="314e5-120">La meilleure option consiste à mettre à jour les requêtes de journalisation pour utiliser les valeurs entières des codes d’État.</span><span class="sxs-lookup"><span data-stu-id="314e5-120">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="314e5-121">Cette option peut entraîner des difficultés à écrire des requêtes sur plusieurs versions de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="314e5-121">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="314e5-122">Toutefois, l’utilisation d’entiers à cet effet est bien plus flexible pour l’interrogation des journaux.</span><span class="sxs-lookup"><span data-stu-id="314e5-122">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="314e5-123">Si vous devez forcer la compatibilité avec l’ancien comportement et utiliser des codes d’État textuels, remplacez la `IHttpClientFactory` journalisation par les vôtres :</span><span class="sxs-lookup"><span data-stu-id="314e5-123">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="314e5-124">Copiez les versions .NET Core 3,1 des classes suivantes dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="314e5-124">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="314e5-125">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="314e5-125">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="314e5-126">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="314e5-126">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="314e5-127">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="314e5-127">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="314e5-128">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="314e5-128">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="314e5-129">Renommez les classes pour éviter les conflits avec les types publics dans le package NuGet [Microsoft. extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) .</span><span class="sxs-lookup"><span data-stu-id="314e5-129">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="314e5-130">Remplacez l’implémentation intégrée de par le `LoggingHttpMessageHandlerBuilderFilter` vôtre dans la méthode du projet `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="314e5-130">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="314e5-131">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="314e5-131">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        var descriptors = services.Where(
            s => s.ServiceType == typeof(IHttpMessageHandlerBuilderFilter));
        foreach (var descriptor in descriptors)
        {
            services.Remove(descriptor);
        }

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

#### <a name="category"></a><span data-ttu-id="314e5-132">Category</span><span class="sxs-lookup"><span data-stu-id="314e5-132">Category</span></span>

<span data-ttu-id="314e5-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="314e5-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="314e5-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="314e5-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
