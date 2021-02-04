---
title: Traçage distribué-.NET
description: Présentation du traçage distribué .NET.
ms.date: 02/02/2021
ms.openlocfilehash: 573f749d7c3253499b6d01f5ba927dfa015e66a8
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99551575"
---
# <a name="net-distributed-tracing"></a><span data-ttu-id="f6316-103">Traçage distribué .NET</span><span class="sxs-lookup"><span data-stu-id="f6316-103">.NET Distributed Tracing</span></span>

<span data-ttu-id="f6316-104">Le traçage distribué permet de publier et d’observer les données de suivi dans un système distribué.</span><span class="sxs-lookup"><span data-stu-id="f6316-104">Distributed tracing is the way to publish and observe the tracing data in a distributed system.</span></span>
<span data-ttu-id="f6316-105">.NET Framework et .NET Core prennent en charge le suivi par le biais des <xref:System.Diagnostics> API.</span><span class="sxs-lookup"><span data-stu-id="f6316-105">.NET Framework and .NET Core has been supporting tracing through the <xref:System.Diagnostics> APIs.</span></span>

- <span data-ttu-id="f6316-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> classe qui autorise le stockage et l’accès au contexte de diagnostic et son utilisation avec le système de journalisation.</span><span class="sxs-lookup"><span data-stu-id="f6316-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> class which allows storing and accessing diagnostics context and consuming it with logging system.</span></span>
- <span data-ttu-id="f6316-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> Cela permet d’instrumenter du code pour la journalisation de la production des charges utiles de données enrichies à des fins de consommation au sein du processus qui a été instrumenté.</span><span class="sxs-lookup"><span data-stu-id="f6316-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> that allows code to be instrumented for production-time logging of rich data payloads for consumption within the process that was instrumented.</span></span>

<span data-ttu-id="f6316-108">Voici un exemple qui montre comment publier des données de suivi à partir des requêtes HTTP entrantes :</span><span class="sxs-lookup"><span data-stu-id="f6316-108">Here is an example shows how to publish tracing data from the HTTP incoming requests:</span></span>

```csharp
   public void OnIncomingRequest(DiagnosticListener httpListener, HttpContext context)
   {
       if (httpListener.IsEnabled("Http_In"))
       {
           var activity = new Activity("Http_In");

           //add tags, baggage, etc.
           activity.SetParentId(context.Request.headers["Request-id"])
           foreach (var pair in context.Request.Headers["Correlation-Context"])
           {
               var baggageItem = NameValueHeaderValue.Parse(pair);
               activity.AddBaggage(baggageItem.Key, baggageItem.Value);
           }
           httpListener.StartActivity(activity, new { context });
           try
           {
               //process request ...
           }
           finally
           {
               //stop activity
               httpListener.StopActivity(activity, new {context} );
           }
       }
   }
```

<span data-ttu-id="f6316-109">Voici un exemple d’écoute des événements d’activité :</span><span class="sxs-lookup"><span data-stu-id="f6316-109">Here is example for how to listen to the Activity events:</span></span>

```csharp
    DiagnosticListener.AllListeners.Subscribe(delegate (DiagnosticListener listener)
    {
        if (listener.Name == "MyActivitySource")
        {
            listener.Subscribe(delegate (KeyValuePair<string, object> value)
            {
                if (value.Key.EndsWith("Start", StringComparison.Ordinal))
                    LogActivityStart();
                else if (value.Key.EndsWith("Stop", StringComparison.Ordinal))
                    LogActivityStop();
            });
        }
    }
```

<span data-ttu-id="f6316-110">.NET 5,0 a étendu la capacité du traçage distribué à autoriser les scénarios de suivi de [OpenTelemetry](https://opentelemetry.io/) , à ajouter des fonctionnalités d’échantillonnage, à simplifier le modèle de codage de suivi et à rendre l’écoute des événements d’activité plus facile et flexible.</span><span class="sxs-lookup"><span data-stu-id="f6316-110">.NET 5.0 has extended the capability of the distributed tracing to allow the [OpenTelemetry](https://opentelemetry.io/) tracing scenarios, added Sampling capabilities, simplified the tracing coding pattern, and made the listening to the Activity events easier and flexible.</span></span>

> [!NOTE]
> <span data-ttu-id="f6316-111">Pour accéder à toutes les fonctionnalités .NET 5,0 ajoutées, assurez-vous de faire référence au package NuGet [System. Diagnostics. DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f6316-111">To access all added .NET 5.0 capabilities, ensure referencing the [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet package version 5.0 or later.</span></span> <span data-ttu-id="f6316-112">Ce package peut être utilisé dans les bibliothèques et applications ciblant n’importe quelle version prise en charge du .NET Framework, .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f6316-112">This package can be used in libraries and apps targeting any supported version of the .NET Framework, .NET Core, and .NET Standard.</span></span> <span data-ttu-id="f6316-113">Si vous ciblez .NET 5,0 ou une version ultérieure, il n’est pas nécessaire de référencer manuellement le package, car il est inclus dans la bibliothèque partagée installée avec le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="f6316-113">If targeting .NET 5.0 or later, no need to manually reference the package as it is included in the shared library installed with the .NET SDK.</span></span>

## <a name="getting-started-with-tracing"></a><span data-ttu-id="f6316-114">Prise en main avec suivi</span><span class="sxs-lookup"><span data-stu-id="f6316-114">Getting Started With Tracing</span></span>

<span data-ttu-id="f6316-115">Les applications et les bibliothèques peuvent facilement publier des données de suivi en utilisant simplement les <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes et.</span><span class="sxs-lookup"><span data-stu-id="f6316-115">The applications and the libraries can easily publish tracing data by simply using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="f6316-116">ActivitySource</span><span class="sxs-lookup"><span data-stu-id="f6316-116">ActivitySource</span></span>

<span data-ttu-id="f6316-117">La première étape de publication des données de suivi consiste à créer une instance de la classe ActivitySource.</span><span class="sxs-lookup"><span data-stu-id="f6316-117">First step to publish tracing data is to create instance of the ActivitySource class.</span></span> <span data-ttu-id="f6316-118">Le ActivitySource est la classe fournit des API permettant de créer et de démarrer des objets d’activité et d’inscrire des objets ActivityListener pour écouter les événements d’activité.</span><span class="sxs-lookup"><span data-stu-id="f6316-118">The ActivitySource is the class provides APIs to create and start Activity objects and to register ActivityListener objects to listen to the Activity events.</span></span>

```csharp
    internal static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a><span data-ttu-id="f6316-119">Bonnes pratiques</span><span class="sxs-lookup"><span data-stu-id="f6316-119">Best Practices</span></span>

- <span data-ttu-id="f6316-120">Créez le ActivitySource une fois et stockez-le dans une variable statique et utilisez cette instance aussi longtemps que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f6316-120">Create the ActivitySource once and store it in a static variable and use that instance as long as needed.</span></span>

- <span data-ttu-id="f6316-121">Le nom de la source passé au constructeur doit être unique pour éviter les conflits avec d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="f6316-121">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span> <span data-ttu-id="f6316-122">Il est recommandé d’utiliser le nom hiérarchique contenant les parties, le nom de la société, le nom du composant et le nom de la source.</span><span class="sxs-lookup"><span data-stu-id="f6316-122">It is recommended to use hierarchical name contains the parts, the company name, the component name, and the source name.</span></span> <span data-ttu-id="f6316-123">Par exemple : `Microsoft.System.HttpClient.HttpInOutRequests`.</span><span class="sxs-lookup"><span data-stu-id="f6316-123">For example, `Microsoft.System.HttpClient.HttpInOutRequests`.</span></span>

- <span data-ttu-id="f6316-124">Le paramètre version est facultatif.</span><span class="sxs-lookup"><span data-stu-id="f6316-124">The version parameter is optional.</span></span> <span data-ttu-id="f6316-125">Il est recommandé de fournir la version dans le cadre de la mise en service de plusieurs versions de la bibliothèque ou de l’application, et de faire la distinction entre les sources de différentes versions.</span><span class="sxs-lookup"><span data-stu-id="f6316-125">It is recommended to provide the version in case plan to release multiple versions of the library or the application and want to distinguish between the sources of different versions.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="f6316-126">Création d’activité</span><span class="sxs-lookup"><span data-stu-id="f6316-126">Activity Creation</span></span>

<span data-ttu-id="f6316-127">L’objet ActivitySource créé peut maintenant être utilisé pour créer et démarrer des objets d’activité qui permettent de consigner des données de suivi à tous les emplacements souhaités dans le code.</span><span class="sxs-lookup"><span data-stu-id="f6316-127">Now the created ActivitySource object can be used to create and start Activity objects which used to log any tracing data in any desired places in the code.</span></span>

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

<span data-ttu-id="f6316-128">Cet exemple de code tente de créer l’objet d’activité, puis d’enregistrer une étiquette `key` de suivi et `value` .</span><span class="sxs-lookup"><span data-stu-id="f6316-128">This sample code try to create the Activity object and then log some tracing tag `key` and `value`.</span></span>

#### <a name="notes"></a><span data-ttu-id="f6316-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6316-129">Notes</span></span>

- <span data-ttu-id="f6316-130">`ActivitySource.StartActivity` tente de créer et de démarrer l’activité en même temps.</span><span class="sxs-lookup"><span data-stu-id="f6316-130">`ActivitySource.StartActivity` tries to create and start the activity in same time.</span></span> <span data-ttu-id="f6316-131">Le modèle de code indiqué utilise le `using` bloc qui supprime automatiquement l’objet d’activité créé après l’exécution du bloc.</span><span class="sxs-lookup"><span data-stu-id="f6316-131">The listed code pattern is using the `using` block which automatically dispose the created Activity object after executing the block.</span></span> <span data-ttu-id="f6316-132">La suppression de l’objet d’activité arrêtera cette activité démarrée et le code n’a pas besoin d’arrêter explicitement l’activité de te.</span><span class="sxs-lookup"><span data-stu-id="f6316-132">Disposing the Activity object will stop this started activity and the code doesn't have to explicitly stop te activity.</span></span> <span data-ttu-id="f6316-133">Qui simplifient le modèle de codage</span><span class="sxs-lookup"><span data-stu-id="f6316-133">That simplify the coding pattern</span></span>

- <span data-ttu-id="f6316-134">`ActivitySource.StartActivity` Déterminez en interne si un écouteur a des événements de ce type.</span><span class="sxs-lookup"><span data-stu-id="f6316-134">`ActivitySource.StartActivity` internally figure out if there any listener to such events.</span></span> <span data-ttu-id="f6316-135">S’il n’y a aucun écouteur inscrit ou qu’il existe un écouteur qui ne s’intéresse pas à ce type d’événement, `ActivitySource.StartActivity` retourne simplement `null` l’objet et évite de créer l’objet d’activité.</span><span class="sxs-lookup"><span data-stu-id="f6316-135">If there is no registered listeners or there is a listeners which not interested in such event, `ActivitySource.StartActivity` simply will return `null` object and avoid creating the Activity object.</span></span> <span data-ttu-id="f6316-136">C’est la raison pour laquelle le code a utilisé l’opérateur Nullable `?`  dans l’instruction `activity?.AddTag` .</span><span class="sxs-lookup"><span data-stu-id="f6316-136">That is why the code used the nullable operator `?`  in the statement `activity?.AddTag`.</span></span> <span data-ttu-id="f6316-137">En général, à l’intérieur du `using` bloc, utilisez toujours l’opérateur Nullable `?` après le nom de l’objet d’activité.</span><span class="sxs-lookup"><span data-stu-id="f6316-137">In general, inside the `using` block, always use the nullable operator `?` after the activity object name.</span></span>

## <a name="listening-to-the-activity-events"></a><span data-ttu-id="f6316-138">Écoute des événements d’activité</span><span class="sxs-lookup"><span data-stu-id="f6316-138">Listening to the Activity Events</span></span>

<span data-ttu-id="f6316-139">.NET fournit la classe <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> qui peut être utilisée pour écouter les événements d’activité déclenchés à partir d’un ou de plusieurs ActivitySource.</span><span class="sxs-lookup"><span data-stu-id="f6316-139">.NET provide the class <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> which can be used to listen to the Activity events triggered from one or more ActivitySource.</span></span>
<span data-ttu-id="f6316-140">L’écouteur peut être utilisé pour collecter des données de suivi, échantillonner ou forcer la création de l’objet d’activité.</span><span class="sxs-lookup"><span data-stu-id="f6316-140">The listener can be used collecting tracing data, sampling, or forcing creating the Activity object.</span></span>

<span data-ttu-id="f6316-141">La `ActivityListener` classe fournit des rappels différents pour gérer des événements différents.</span><span class="sxs-lookup"><span data-stu-id="f6316-141">The `ActivityListener` class provides a different callbacks to handle different events.</span></span>

```csharp

ActivityListener listener = new ActivityListener()

ShouldListenTo = (activitySource) => object.ReferenceEquals(source, activitySource),
ActivityStarted = activity => /* Handle the Activity start event here */ DoSomething(),
ActivityStopped = activity => /* Handle the Activity stop event here */ DoSomething(),
SampleUsingParentId = (ref ActivityCreationOptions<string> activityOptions) => ActivitySamplingResult.AllData,
Sample = (ref ActivityCreationOptions<ActivityContext> activityOptions) => ActivitySamplingResult.AllData

// Enable the listener
ActivitySource.AddActivityListener(listener);
```

- <span data-ttu-id="f6316-142">`ShouldListenTo` active l’écoute d’un `ActivitySource` objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="f6316-142">`ShouldListenTo` enables listening to a specific `ActivitySource` objects.</span></span> <span data-ttu-id="f6316-143">Dans l’exemple, il permet d’écouter l' `ActivitySource` objet que nous avons créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="f6316-143">In the example, it enables listening to the `ActivitySource` object we have previously created.</span></span> <span data-ttu-id="f6316-144">Il existe une plus grande flexibilité pour écouter les autres `ActivitySource` objets en vérifiant les `Name` et `Version` de l’entrée `ActivitySource` .</span><span class="sxs-lookup"><span data-stu-id="f6316-144">There is more flexibility to listen to any other `ActivitySource` objects by checking the `Name` and `Version` of the input `ActivitySource`.</span></span>

- <span data-ttu-id="f6316-145">`ActivityStarted` et `ActivityStopped` activent l’obtention des `Activity` événements de démarrage et d’arrêt pour tous les `Activity` objets créés par les `ActivitySource` objets qui ont été activés pour écouter par `ShouldListenTo` rappel.</span><span class="sxs-lookup"><span data-stu-id="f6316-145">`ActivityStarted` and `ActivityStopped` enable getting the `Activity` Start and Stop events for all `Activity` objects created by the `ActivitySource` objects which was enabled to listen to by `ShouldListenTo` callback.</span></span>

- <span data-ttu-id="f6316-146">`Sample` et `SampleUsingParentId` sont les rappels principaux qui sont destinés à l’échantillonnage.</span><span class="sxs-lookup"><span data-stu-id="f6316-146">`Sample` and `SampleUsingParentId` are the main callbacks which intended for sampling.</span></span> <span data-ttu-id="f6316-147">Ces deux rappels retournent la `ActivitySamplingResult` valeur enum qui peut demander à d’échantillonner ou d’extraire la `Activity` demande de création actuelle.</span><span class="sxs-lookup"><span data-stu-id="f6316-147">These two callbacks return the `ActivitySamplingResult` enum value which can tell either to sample in or out the current `Activity` creation request.</span></span> <span data-ttu-id="f6316-148">Si le retour de rappel `ActivitySamplingResult.None` et aucun autre écouteur activé ne retournent une valeur différente, l’activité n’est pas créée et `ActivitySource.StartActivity` retourne `null` .</span><span class="sxs-lookup"><span data-stu-id="f6316-148">If the callback return `ActivitySamplingResult.None` and no other enabled listeners return different value, then the Activity wil not get created and `ActivitySource.StartActivity` will return `null`.</span></span> <span data-ttu-id="f6316-149">Dans le cas contraire, l' `Activity` objet sera créé.</span><span class="sxs-lookup"><span data-stu-id="f6316-149">Otherwise, the `Activity` object will get created.</span></span>

## <a name="net-50-new-features"></a><span data-ttu-id="f6316-150">Nouvelles fonctionnalités de .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f6316-150">.NET 5.0 New Features</span></span>

<span data-ttu-id="f6316-151">La classe for ablation `Activity` prend en charge le suivi des scénarios principaux.</span><span class="sxs-lookup"><span data-stu-id="f6316-151">For awhile `Activity` class has been supporting tracing main scenarios.</span></span> <span data-ttu-id="f6316-152">Il permettait de coller des balises qui sont des paires clé-valeur de données de suivi.</span><span class="sxs-lookup"><span data-stu-id="f6316-152">It allowed sticking tags which is key-value pairs of tracing data.</span></span> <span data-ttu-id="f6316-153">Il prend en charge les bagages qui sont des balises clé-valeur destinées à être propagées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="f6316-153">It has been supporting Baggages which is a key-value tags intended to be propagated across the wire.</span></span>

<span data-ttu-id="f6316-154">.NET 5,0 prend en charge davantage de fonctionnalités principalement pour activer les scénarios OpenTelemetry.</span><span class="sxs-lookup"><span data-stu-id="f6316-154">.NET 5.0 supports more features mainly to enable OpenTelemetry scenarios.</span></span>

### <a name="activitycontext"></a><span data-ttu-id="f6316-155">ActivityContext</span><span class="sxs-lookup"><span data-stu-id="f6316-155">ActivityContext</span></span>

<span data-ttu-id="f6316-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> est le struct qui porte le contexte des opérations de suivi (par exemple, l’ID de trace, l’ID d’étendue, les indicateurs de trace et l’état de trace).</span><span class="sxs-lookup"><span data-stu-id="f6316-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> is the struct carrying the context of the tracing operations (e.g. the trace Id, Span Id, trace flags, and trace state).</span></span> <span data-ttu-id="f6316-157">Désormais, il est possible de créer un nouveau `Activity` en fournissant le contexte de suivi parent.</span><span class="sxs-lookup"><span data-stu-id="f6316-157">Now it is possible to create a new `Activity` with providing the parent tracing context.</span></span> <span data-ttu-id="f6316-158">En outre, il est facile d’extraire le contexte de suivi d’un `Activity` objet en appelant la `Activity.Context` propriété.</span><span class="sxs-lookup"><span data-stu-id="f6316-158">Also, it is easy to extract the tracing context from any `Activity` object by calling `Activity.Context` property.</span></span>

### <a name="activitylink"></a><span data-ttu-id="f6316-159">ActivityLink</span><span class="sxs-lookup"><span data-stu-id="f6316-159">ActivityLink</span></span>

<span data-ttu-id="f6316-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> struct contenant l’instance de contexte de suivi qui peut être liée à un objet de liaison occasionnelle `Activity` .</span><span class="sxs-lookup"><span data-stu-id="f6316-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> is the struct containing the tracing context instance which can be linked to casually related `Activity` object.</span></span> <span data-ttu-id="f6316-161">Des liens peuvent être ajoutés à l' `Activity` objet en passant la liste de liens à la `ActivitySource.StartActivity` méthode lors de la création du `Activity` .</span><span class="sxs-lookup"><span data-stu-id="f6316-161">Links can be added to the `Activity` object by passing the links list to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="f6316-162">Les `Activity` liens associés à l’objet entier peuvent être récupérés à l’aide de la propriété `Activity.Links` .</span><span class="sxs-lookup"><span data-stu-id="f6316-162">The whole `Activity` object attached links can be  retrieved using the property `Activity.Links`.</span></span>

### <a name="activityevent"></a><span data-ttu-id="f6316-163">ActivityEvent</span><span class="sxs-lookup"><span data-stu-id="f6316-163">ActivityEvent</span></span>

<span data-ttu-id="f6316-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> représente un événement contenant un nom et un horodateur, ainsi qu’une liste facultative de balises.</span><span class="sxs-lookup"><span data-stu-id="f6316-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> represents an event containing a name and a timestamp, as well as an optional list of tags.</span></span> <span data-ttu-id="f6316-165">Les événements peuvent être ajoutés à l' `Activity` objet en appelant la `Activity.AddEvent` méthode.</span><span class="sxs-lookup"><span data-stu-id="f6316-165">Events can be added to the `Activity` object by calling `Activity.AddEvent` method.</span></span> <span data-ttu-id="f6316-166">La liste complète des `Activity` événements d’objet peut être récupérée à l’aide de la propriété `Activity.Events` .</span><span class="sxs-lookup"><span data-stu-id="f6316-166">The whole list of the `Activity` object Events can be retrieved using the property `Activity.Events`.</span></span>

### <a name="activitykind"></a><span data-ttu-id="f6316-167">ActivityKind</span><span class="sxs-lookup"><span data-stu-id="f6316-167">ActivityKind</span></span>

<span data-ttu-id="f6316-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> décrit la relation entre l’activité, ses parents et ses enfants dans une trace.</span><span class="sxs-lookup"><span data-stu-id="f6316-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> describes the relationship between the activity, its parents and its children in a trace.</span></span> <span data-ttu-id="f6316-169">Le genre peut être défini sur l' `Activity` objet en passant le type value à la `ActivitySource.StartActivity` méthode lors de la création de `Activity` .</span><span class="sxs-lookup"><span data-stu-id="f6316-169">Kind can be set  to the `Activity` object by passing the kind value to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="f6316-170">Le `Activity` genre d’objet peut être récupéré à l’aide de la propriété `Activity.Kind` .</span><span class="sxs-lookup"><span data-stu-id="f6316-170">The `Activity` object kind can be retrieved using the property `Activity.Kind`.</span></span>

### <a name="isalldatarequested"></a><span data-ttu-id="f6316-171">IsAllDataRequested</span><span class="sxs-lookup"><span data-stu-id="f6316-171">IsAllDataRequested</span></span>

<span data-ttu-id="f6316-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> indique si cette activité doit être remplie avec toutes les informations de propagation, ainsi que toutes les autres propriétés, telles que les liens, les balises et les événements.</span><span class="sxs-lookup"><span data-stu-id="f6316-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> indicates whether this activity should be populated with all the propagation information, as well as all the other properties, such as links, tags, and events.</span></span> <span data-ttu-id="f6316-173">La valeur de `IsAllDataRequested` est déterminée à partir du résultat retourné à partir de tous les écouteurs `Sample` et `SampleUsingParentId` rappels.</span><span class="sxs-lookup"><span data-stu-id="f6316-173">The value of `IsAllDataRequested` is determined from the result returned from all listeners `Sample` and `SampleUsingParentId` callbacks.</span></span> <span data-ttu-id="f6316-174">La valeur peut être récupérée à l’aide de la `Activity.IsAllDataRequested` propriété.</span><span class="sxs-lookup"><span data-stu-id="f6316-174">The value can be retrieved using `Activity.IsAllDataRequested` property.</span></span>

### <a name="activitysource"></a><span data-ttu-id="f6316-175">Activity. source</span><span class="sxs-lookup"><span data-stu-id="f6316-175">Activity.Source</span></span>

<span data-ttu-id="f6316-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> Obtient la source d’activité associée à cette activité.</span><span class="sxs-lookup"><span data-stu-id="f6316-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> gets the activity source associated with this activity.</span></span>

### <a name="activitydisplayname"></a><span data-ttu-id="f6316-177">Activity. DisplayName</span><span class="sxs-lookup"><span data-stu-id="f6316-177">Activity.DisplayName</span></span>

<span data-ttu-id="f6316-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> permet d’obtenir ou de définir un nom complet pour l’activité.</span><span class="sxs-lookup"><span data-stu-id="f6316-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> allows getting or setting a display name to the activity.</span></span>

### <a name="activitytagobjects"></a><span data-ttu-id="f6316-179">Activity. TagObjects</span><span class="sxs-lookup"><span data-stu-id="f6316-179">Activity.TagObjects</span></span>

<span data-ttu-id="f6316-180">`Activity` la classe a la propriété `Activity.Tags` qui retourne la liste de paires clé-valeur des balises de type chaîne pour la clé et la valeur.</span><span class="sxs-lookup"><span data-stu-id="f6316-180">`Activity` class has the property `Activity.Tags` which return the a key-value pair list of the tags of type string for the key and value.</span></span> <span data-ttu-id="f6316-181">Ces balises peuvent être ajoutées au à l' `Activity` aide de la méthode `AddTag(string, string)` .</span><span class="sxs-lookup"><span data-stu-id="f6316-181">Such Tags can be added to the `Activity` using the method `AddTag(string, string)`.</span></span> <span data-ttu-id="f6316-182">`Activity` a étendu la prise en charge des balises en fournissant la méthode surchargée `AddTag(string, object)` qui permet d’avoir des valeurs de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="f6316-182">`Activity` has extended the support of tags by providing the overloaded method `AddTag(string, object)` allowing to have values of any type.</span></span>  <span data-ttu-id="f6316-183">La liste complète de ces balises peut être récupérée à l’aide de <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f6316-183">The complete list of such tags can be retrieved using <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType>.</span></span>

## <a name="sampling"></a><span data-ttu-id="f6316-184">échantillonnage</span><span class="sxs-lookup"><span data-stu-id="f6316-184">Sampling</span></span>

<span data-ttu-id="f6316-185">L’échantillonnage est un mécanisme qui permet de contrôler le bruit et la surcharge en réduisant le nombre d’échantillons des traces collectées et envoyées au serveur principal.</span><span class="sxs-lookup"><span data-stu-id="f6316-185">Sampling is a mechanism to control the noise and overhead by reducing the number of samples of traces collected and sent to the backend.</span></span> <span data-ttu-id="f6316-186">L’échantillonnage est un scénario OpenTelemetry important.</span><span class="sxs-lookup"><span data-stu-id="f6316-186">Sampling is important OpenTelemetry scenario.</span></span> <span data-ttu-id="f6316-187">Dans .NET 5,0, il est facile d’autoriser l’échantillonnage.</span><span class="sxs-lookup"><span data-stu-id="f6316-187">In .NET 5.0 it is easy to allow sampling.</span></span> <span data-ttu-id="f6316-188">Une bonne pratique consiste à créer les nouveaux `Activity` objets à l’aide de `ActivitySource.StartActivity` et à essayer de fournir toutes les données disponibles (par exemple, les balises, le genre, les liens, etc.). etc.) lors de l’appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f6316-188">A good practice is create the  new `Activity` objects using `ActivitySource.StartActivity` and try to provide all possible available data (e.g. tags, kind, links, ...etc.) when calling this method.</span></span> <span data-ttu-id="f6316-189">Le fait de fournir les données permet aux échantillonneurs qui ont été implémentés à l’aide d' `ActivityListener` d’avoir une décision d’échantillonnage appropriée.</span><span class="sxs-lookup"><span data-stu-id="f6316-189">Providing the data will allow the samplers which implemented using the `ActivityListener` to have proper sampling decision.</span></span> <span data-ttu-id="f6316-190">Si les performances sont essentielles pour éviter de créer des données avant de créer l' `Activity` objet, la propriété est `ActivitySource.HasListeners` utile pour vérifier s’il existe des écouteurs avant de créer les données nécessaires.</span><span class="sxs-lookup"><span data-stu-id="f6316-190">If the performance is critical to avoid creating the data before creating the `Activity` object, the property `ActivitySource.HasListeners` comes handy to check if there is any listeners before creating the needed data.</span></span>

## <a name="opentelemetry"></a><span data-ttu-id="f6316-191">OpenTelemetry</span><span class="sxs-lookup"><span data-stu-id="f6316-191">OpenTelemetry</span></span>

<span data-ttu-id="f6316-192">OpenTelemetry SDK est fourni avec de nombreuses fonctionnalités qui prennent en charge les scénarios de suivi distribués de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="f6316-192">OpenTelemetry SDK comes with many features that support end-to-end distributed tracing scenarios.</span></span> <span data-ttu-id="f6316-193">Il fournit plusieurs échantillonneurs et exportateurs qui peuvent choisir parmi ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="f6316-193">It provides multiple samplers and exporters which can choose from.</span></span> <span data-ttu-id="f6316-194">Il permet également de créer des échantillonneurs et des exportateurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f6316-194">It allows creating a custom samplers and exporters too.</span></span>

<span data-ttu-id="f6316-195">OpenTelemetry prend en charge l’exportation des données de suivi collectées vers différents serveurs principaux (par exemple, Jaeger, Zipkin, New Relic,... etc.).</span><span class="sxs-lookup"><span data-stu-id="f6316-195">OpenTelemetry supports exporting the collected tracing data to different backends (e.g. Jaeger, Zipkin, New Relic,...etc.).</span></span> <span data-ttu-id="f6316-196">Pour plus d’informations, reportez-vous à [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/) . pour plus d’informations, consultez la rubrique pour `OpenTelemetry.Exporter.` obtenir la liste des packages de l’exportateur à NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="f6316-196">Refer to [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/) for more details and search Nuget.org for packages starts with `OpenTelemetry.Exporter.` to get the exporter packages list.</span></span>

<span data-ttu-id="f6316-197">Voici un exemple de code porté à partir de [OpenTelemetry-dotnet Getting Started](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) , qui montre à quel point il est facile d’échantillonner et d’exporter des données de suivi vers la console.</span><span class="sxs-lookup"><span data-stu-id="f6316-197">Here is a sample code ported from [OpenTelemetry-dotnet getting started](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) showing how easy can sample and export tracing data to the console.</span></span>

```csharp
// <copyright file="Program.cs" company="OpenTelemetry Authors">
// Copyright The OpenTelemetry Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
// </copyright>

using System.Diagnostics;
using OpenTelemetry;
using OpenTelemetry.Trace;

public class Program
{
    private static readonly ActivitySource MyActivitySource = new ActivitySource(
        "MyCompany.MyProduct.MyLibrary");

    public static void Main()
    {
        using var tracerProvider = Sdk.CreateTracerProviderBuilder()
            .SetSampler(new AlwaysOnSampler())
            .AddSource("MyCompany.MyProduct.MyLibrary")
            .AddConsoleExporter()
            .Build();

        using (var activity = MyActivitySource.StartActivity("SayHello"))
        {
            activity?.SetTag("foo", 1);
            activity?.SetTag("bar", "Hello, World!");
            activity?.SetTag("baz", new int[] { 1, 2, 3 });
        }
    }
}
```

<span data-ttu-id="f6316-198">L’exemple doit référencer le package [OpenTelemetry. exporter. console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).</span><span class="sxs-lookup"><span data-stu-id="f6316-198">The sample needs to reference the package [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).</span></span>
