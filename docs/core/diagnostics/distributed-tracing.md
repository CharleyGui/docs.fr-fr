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
# <a name="net-distributed-tracing"></a>Traçage distribué .NET

Le traçage distribué permet de publier et d’observer les données de suivi dans un système distribué.
.NET Framework et .NET Core prennent en charge le suivi par le biais des <xref:System.Diagnostics> API.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classe qui autorise le stockage et l’accès au contexte de diagnostic et son utilisation avec le système de journalisation.
- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> Cela permet d’instrumenter du code pour la journalisation de la production des charges utiles de données enrichies à des fins de consommation au sein du processus qui a été instrumenté.

Voici un exemple qui montre comment publier des données de suivi à partir des requêtes HTTP entrantes :

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

Voici un exemple d’écoute des événements d’activité :

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

.NET 5,0 a étendu la capacité du traçage distribué à autoriser les scénarios de suivi de [OpenTelemetry](https://opentelemetry.io/) , à ajouter des fonctionnalités d’échantillonnage, à simplifier le modèle de codage de suivi et à rendre l’écoute des événements d’activité plus facile et flexible.

> [!NOTE]
> Pour accéder à toutes les fonctionnalités .NET 5,0 ajoutées, assurez-vous de faire référence au package NuGet [System. Diagnostics. DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5,0 ou ultérieure. Ce package peut être utilisé dans les bibliothèques et applications ciblant n’importe quelle version prise en charge du .NET Framework, .NET Core et .NET Standard. Si vous ciblez .NET 5,0 ou une version ultérieure, il n’est pas nécessaire de référencer manuellement le package, car il est inclus dans la bibliothèque partagée installée avec le kit de développement logiciel (SDK) .NET.

## <a name="getting-started-with-tracing"></a>Prise en main avec suivi

Les applications et les bibliothèques peuvent facilement publier des données de suivi en utilisant simplement les <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes et.

### <a name="activitysource"></a>ActivitySource

La première étape de publication des données de suivi consiste à créer une instance de la classe ActivitySource. Le ActivitySource est la classe fournit des API permettant de créer et de démarrer des objets d’activité et d’inscrire des objets ActivityListener pour écouter les événements d’activité.

```csharp
    internal static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a>Bonnes pratiques

- Créez le ActivitySource une fois et stockez-le dans une variable statique et utilisez cette instance aussi longtemps que nécessaire.

- Le nom de la source passé au constructeur doit être unique pour éviter les conflits avec d’autres sources. Il est recommandé d’utiliser le nom hiérarchique contenant les parties, le nom de la société, le nom du composant et le nom de la source. Par exemple : `Microsoft.System.HttpClient.HttpInOutRequests`.

- Le paramètre version est facultatif. Il est recommandé de fournir la version dans le cadre de la mise en service de plusieurs versions de la bibliothèque ou de l’application, et de faire la distinction entre les sources de différentes versions.

### <a name="activity-creation"></a>Création d’activité

L’objet ActivitySource créé peut maintenant être utilisé pour créer et démarrer des objets d’activité qui permettent de consigner des données de suivi à tous les emplacements souhaités dans le code.

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

Cet exemple de code tente de créer l’objet d’activité, puis d’enregistrer une étiquette `key` de suivi et `value` .

#### <a name="notes"></a>Remarques

- `ActivitySource.StartActivity` tente de créer et de démarrer l’activité en même temps. Le modèle de code indiqué utilise le `using` bloc qui supprime automatiquement l’objet d’activité créé après l’exécution du bloc. La suppression de l’objet d’activité arrêtera cette activité démarrée et le code n’a pas besoin d’arrêter explicitement l’activité de te. Qui simplifient le modèle de codage

- `ActivitySource.StartActivity` Déterminez en interne si un écouteur a des événements de ce type. S’il n’y a aucun écouteur inscrit ou qu’il existe un écouteur qui ne s’intéresse pas à ce type d’événement, `ActivitySource.StartActivity` retourne simplement `null` l’objet et évite de créer l’objet d’activité. C’est la raison pour laquelle le code a utilisé l’opérateur Nullable `?`  dans l’instruction `activity?.AddTag` . En général, à l’intérieur du `using` bloc, utilisez toujours l’opérateur Nullable `?` après le nom de l’objet d’activité.

## <a name="listening-to-the-activity-events"></a>Écoute des événements d’activité

.NET fournit la classe <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> qui peut être utilisée pour écouter les événements d’activité déclenchés à partir d’un ou de plusieurs ActivitySource.
L’écouteur peut être utilisé pour collecter des données de suivi, échantillonner ou forcer la création de l’objet d’activité.

La `ActivityListener` classe fournit des rappels différents pour gérer des événements différents.

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

- `ShouldListenTo` active l’écoute d’un `ActivitySource` objet spécifique. Dans l’exemple, il permet d’écouter l' `ActivitySource` objet que nous avons créé précédemment. Il existe une plus grande flexibilité pour écouter les autres `ActivitySource` objets en vérifiant les `Name` et `Version` de l’entrée `ActivitySource` .

- `ActivityStarted` et `ActivityStopped` activent l’obtention des `Activity` événements de démarrage et d’arrêt pour tous les `Activity` objets créés par les `ActivitySource` objets qui ont été activés pour écouter par `ShouldListenTo` rappel.

- `Sample` et `SampleUsingParentId` sont les rappels principaux qui sont destinés à l’échantillonnage. Ces deux rappels retournent la `ActivitySamplingResult` valeur enum qui peut demander à d’échantillonner ou d’extraire la `Activity` demande de création actuelle. Si le retour de rappel `ActivitySamplingResult.None` et aucun autre écouteur activé ne retournent une valeur différente, l’activité n’est pas créée et `ActivitySource.StartActivity` retourne `null` . Dans le cas contraire, l' `Activity` objet sera créé.

## <a name="net-50-new-features"></a>Nouvelles fonctionnalités de .NET 5,0

La classe for ablation `Activity` prend en charge le suivi des scénarios principaux. Il permettait de coller des balises qui sont des paires clé-valeur de données de suivi. Il prend en charge les bagages qui sont des balises clé-valeur destinées à être propagées sur le réseau.

.NET 5,0 prend en charge davantage de fonctionnalités principalement pour activer les scénarios OpenTelemetry.

### <a name="activitycontext"></a>ActivityContext

<xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> est le struct qui porte le contexte des opérations de suivi (par exemple, l’ID de trace, l’ID d’étendue, les indicateurs de trace et l’état de trace). Désormais, il est possible de créer un nouveau `Activity` en fournissant le contexte de suivi parent. En outre, il est facile d’extraire le contexte de suivi d’un `Activity` objet en appelant la `Activity.Context` propriété.

### <a name="activitylink"></a>ActivityLink

<xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> struct contenant l’instance de contexte de suivi qui peut être liée à un objet de liaison occasionnelle `Activity` . Des liens peuvent être ajoutés à l' `Activity` objet en passant la liste de liens à la `ActivitySource.StartActivity` méthode lors de la création du `Activity` . Les `Activity` liens associés à l’objet entier peuvent être récupérés à l’aide de la propriété `Activity.Links` .

### <a name="activityevent"></a>ActivityEvent

<xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> représente un événement contenant un nom et un horodateur, ainsi qu’une liste facultative de balises. Les événements peuvent être ajoutés à l' `Activity` objet en appelant la `Activity.AddEvent` méthode. La liste complète des `Activity` événements d’objet peut être récupérée à l’aide de la propriété `Activity.Events` .

### <a name="activitykind"></a>ActivityKind

<xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> décrit la relation entre l’activité, ses parents et ses enfants dans une trace. Le genre peut être défini sur l' `Activity` objet en passant le type value à la `ActivitySource.StartActivity` méthode lors de la création de `Activity` . Le `Activity` genre d’objet peut être récupéré à l’aide de la propriété `Activity.Kind` .

### <a name="isalldatarequested"></a>IsAllDataRequested

<xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> indique si cette activité doit être remplie avec toutes les informations de propagation, ainsi que toutes les autres propriétés, telles que les liens, les balises et les événements. La valeur de `IsAllDataRequested` est déterminée à partir du résultat retourné à partir de tous les écouteurs `Sample` et `SampleUsingParentId` rappels. La valeur peut être récupérée à l’aide de la `Activity.IsAllDataRequested` propriété.

### <a name="activitysource"></a>Activity. source

<xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> Obtient la source d’activité associée à cette activité.

### <a name="activitydisplayname"></a>Activity. DisplayName

<xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> permet d’obtenir ou de définir un nom complet pour l’activité.

### <a name="activitytagobjects"></a>Activity. TagObjects

`Activity` la classe a la propriété `Activity.Tags` qui retourne la liste de paires clé-valeur des balises de type chaîne pour la clé et la valeur. Ces balises peuvent être ajoutées au à l' `Activity` aide de la méthode `AddTag(string, string)` . `Activity` a étendu la prise en charge des balises en fournissant la méthode surchargée `AddTag(string, object)` qui permet d’avoir des valeurs de n’importe quel type.  La liste complète de ces balises peut être récupérée à l’aide de <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType> .

## <a name="sampling"></a>échantillonnage

L’échantillonnage est un mécanisme qui permet de contrôler le bruit et la surcharge en réduisant le nombre d’échantillons des traces collectées et envoyées au serveur principal. L’échantillonnage est un scénario OpenTelemetry important. Dans .NET 5,0, il est facile d’autoriser l’échantillonnage. Une bonne pratique consiste à créer les nouveaux `Activity` objets à l’aide de `ActivitySource.StartActivity` et à essayer de fournir toutes les données disponibles (par exemple, les balises, le genre, les liens, etc.). etc.) lors de l’appel de cette méthode. Le fait de fournir les données permet aux échantillonneurs qui ont été implémentés à l’aide d' `ActivityListener` d’avoir une décision d’échantillonnage appropriée. Si les performances sont essentielles pour éviter de créer des données avant de créer l' `Activity` objet, la propriété est `ActivitySource.HasListeners` utile pour vérifier s’il existe des écouteurs avant de créer les données nécessaires.

## <a name="opentelemetry"></a>OpenTelemetry

OpenTelemetry SDK est fourni avec de nombreuses fonctionnalités qui prennent en charge les scénarios de suivi distribués de bout en bout. Il fournit plusieurs échantillonneurs et exportateurs qui peuvent choisir parmi ceux-ci. Il permet également de créer des échantillonneurs et des exportateurs personnalisés.

OpenTelemetry prend en charge l’exportation des données de suivi collectées vers différents serveurs principaux (par exemple, Jaeger, Zipkin, New Relic,... etc.). Pour plus d’informations, reportez-vous à [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/) . pour plus d’informations, consultez la rubrique pour `OpenTelemetry.Exporter.` obtenir la liste des packages de l’exportateur à NuGet.org.

Voici un exemple de code porté à partir de [OpenTelemetry-dotnet Getting Started](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) , qui montre à quel point il est facile d’échantillonner et d’exporter des données de suivi vers la console.

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

L’exemple doit référencer le package [OpenTelemetry. exporter. console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).
