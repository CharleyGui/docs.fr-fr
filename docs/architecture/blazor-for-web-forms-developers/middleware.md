---
title: Modules, gestionnaires et intergiciel (middleware)
description: En savoir plus sur la gestion des requêtes HTTP avec les modules, les gestionnaires et l’intergiciel (middleware).
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 10/11/2019
ms.openlocfilehash: ff2b3fd41316a1c8c20a0eed9a585e5fd2733af3
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173183"
---
# <a name="modules-handlers-and-middleware"></a>Modules, gestionnaires et intergiciel (middleware)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Une application ASP.NET Core est basée sur une série d' *intergiciels (middleware*). L’intergiciel est un gestionnaire qui est organisé dans un pipeline pour gérer les demandes et les réponses. Dans une application Web Forms, les modules et les gestionnaires HTTP résolvent des problèmes similaires. Dans ASP.NET Core, les modules, les gestionnaires, *global.asax.cs*et le cycle de vie de l’application sont remplacés par un intergiciel (middleware). Dans ce chapitre, vous allez découvrir l’intergiciel (middleware) dans le contexte d’une Blazor application.

## <a name="overview"></a>Vue d’ensemble

Le pipeline de requête ASP.NET Core est composé d’une séquence de délégués de requête, appelés l’un après l’autre. Le diagramme suivant illustre le concept. Le thread d’exécution suit les flèches noires.

![pipeline](media/middleware/request-delegate-pipeline.png)

Le diagramme précédent n’a pas de concept d’événements de cycle de vie. Ce concept est fondamental pour gérer les demandes de ASP.NET Web Forms. Ce système facilite la définition du processus en cours et permet l’insertion d’un intergiciel (middleware) à tout moment. L’intergiciel s’exécute dans l’ordre dans lequel il est ajouté au pipeline de requête. Elles sont également ajoutées dans le code au lieu des fichiers de configuration, généralement dans *Startup.cs*.

## <a name="katana"></a>Katana

Les lecteurs connaissant Katana se sentent à l’aise dans ASP.NET Core. En fait, Katana est une infrastructure à partir de laquelle dérive ASP.NET Core. Il a introduit des modèles d’intergiciel et de pipeline similaires pour ASP.NET 4. x. Les intergiciels (middleware) conçus pour Katana peuvent être adaptés pour fonctionner avec le pipeline ASP.NET Core.

## <a name="common-middleware"></a>Intergiciel (middleware) commun

ASP.NET 4. x comprend de nombreux modules. De la même façon, ASP.NET Core possède également de nombreux composants d’intergiciel (middleware) disponibles. Les modules IIS peuvent être utilisés dans certains cas avec ASP.NET Core. Dans d’autres cas, l’intergiciel (middleware) ASP.NET Core natif peut être disponible.

Le tableau suivant répertorie les intergiciels et composants de remplacement dans ASP.NET Core.

|Module                 |Module ASP.NET 4. x           |Option ASP.NET Core|
|-----------------------|-----------------------------|-------------------|
|Erreurs HTTP            |`CustomErrorModule`          |[Middleware (intergiciel) de pages de codes d’état](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|Document par défaut       |`DefaultDocumentModule`      |[Middleware de fichiers par défaut](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|Exploration de répertoires     |`DirectoryListingModule`     |[Middleware d’exploration des répertoires](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|Compression dynamique    |`DynamicCompressionModule`   |[Middleware de compression des réponses](/aspnet/core/performance/response-compression)|
|Suivi des demandes ayant échoué|`FailedRequestsTracingModule`|[Journalisation ASP.NET Core](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|Mise en cache de fichiers           |`FileCacheModule`            |[Intergiciel (middleware) de mise en cache des réponses](/aspnet/core/performance/caching/middleware)|
|Mise en cache HTTP           |`HttpCacheModule`            |[Intergiciel (middleware) de mise en cache des réponses](/aspnet/core/performance/caching/middleware)|
|Journalisation HTTP           |`HttpLoggingModule`          |[Journalisation ASP.NET Core](/aspnet/core/fundamentals/logging/index)|
|Redirection HTTP       |`HttpRedirectionModule`      |[Intergiciel (middleware) de réécriture d’URL](/aspnet/core/fundamentals/url-rewriting)|
|Filtres ISAPI          |`IsapiFilterModule`          |[Middleware](/aspnet/core/fundamentals/middleware/index)|
|ISAPI                  |`IsapiModule`                |[Middleware](/aspnet/core/fundamentals/middleware/index)|
|Filtrage des demandes      |`RequestFilteringModule`     |[Intergiciel (middleware) de réécriture d’URL IRule](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|&#8224; de réécriture d’URL   |`RewriteModule`              |[Intergiciel (middleware) de réécriture d’URL](/aspnet/core/fundamentals/url-rewriting)|
|Compression statique     |`StaticCompressionModule`    |[Middleware de compression des réponses](/aspnet/core/performance/response-compression)|
|Contenu statique         |`StaticFileModule`           |[Middleware de fichiers statiques](/aspnet/core/fundamentals/static-files)|
|Autorisation d’URL      |`UrlAuthorizationModule`     |[Identité ASP.NET Core](/aspnet/core/security/authentication/identity)|

Cette liste n’est pas exhaustive, mais elle doit vous faire une idée du mappage existant entre les deux infrastructures. Pour obtenir une liste plus détaillée, consultez [modules IIS avec ASP.net Core](/aspnet/core/host-and-deploy/iis/modules).

## <a name="custom-middleware"></a>Intergiciel (middleware) personnalisé

Les intergiciels (middleware) intégrés ne gèrent pas tous les scénarios nécessaires pour une application. Dans ce cas, il est judicieux de créer votre propre intergiciel. Il existe plusieurs façons de définir des intergiciels (middleware), le plus simple étant un délégué simple. Examinez l’intergiciel (middleware) suivant, qui accepte une demande de culture d’une chaîne de requête :

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

L’intergiciel peut également être défini en tant que classe, soit en implémentant l’interface, soit `IMiddleware` en suivant la Convention d’intergiciel (middleware). Pour plus d’informations, consultez [Write custom ASP.net Core middleware](/aspnet/core/fundamentals/middleware/write).

>[!div class="step-by-step"]
>[Précédent](data.md) 
> [Suivant](config.md)
