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
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="5c8c2-103">Modules, gestionnaires et intergiciel (middleware)</span><span class="sxs-lookup"><span data-stu-id="5c8c2-103">Modules, handlers, and middleware</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5c8c2-104">Une application ASP.NET Core est basée sur une série d' *intergiciels (middleware*).</span><span class="sxs-lookup"><span data-stu-id="5c8c2-104">An ASP.NET Core app is built upon a series of *middleware*.</span></span> <span data-ttu-id="5c8c2-105">L’intergiciel est un gestionnaire qui est organisé dans un pipeline pour gérer les demandes et les réponses.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-105">Middleware is handlers that are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="5c8c2-106">Dans une application Web Forms, les modules et les gestionnaires HTTP résolvent des problèmes similaires.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="5c8c2-107">Dans ASP.NET Core, les modules, les gestionnaires, *global.asax.cs*et le cycle de vie de l’application sont remplacés par un intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="5c8c2-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="5c8c2-108">Dans ce chapitre, vous allez découvrir l’intergiciel (middleware) dans le contexte d’une Blazor application.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="5c8c2-109">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="5c8c2-109">Overview</span></span>

<span data-ttu-id="5c8c2-110">Le pipeline de requête ASP.NET Core est composé d’une séquence de délégués de requête, appelés l’un après l’autre.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="5c8c2-111">Le diagramme suivant illustre le concept.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="5c8c2-112">Le thread d’exécution suit les flèches noires.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-112">The thread of execution follows the black arrows.</span></span>

![pipeline](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="5c8c2-114">Le diagramme précédent n’a pas de concept d’événements de cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="5c8c2-115">Ce concept est fondamental pour gérer les demandes de ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="5c8c2-116">Ce système facilite la définition du processus en cours et permet l’insertion d’un intergiciel (middleware) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="5c8c2-117">L’intergiciel s’exécute dans l’ordre dans lequel il est ajouté au pipeline de requête.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="5c8c2-118">Elles sont également ajoutées dans le code au lieu des fichiers de configuration, généralement dans *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="5c8c2-119">Katana</span><span class="sxs-lookup"><span data-stu-id="5c8c2-119">Katana</span></span>

<span data-ttu-id="5c8c2-120">Les lecteurs connaissant Katana se sentent à l’aise dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="5c8c2-121">En fait, Katana est une infrastructure à partir de laquelle dérive ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="5c8c2-122">Il a introduit des modèles d’intergiciel et de pipeline similaires pour ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="5c8c2-123">Les intergiciels (middleware) conçus pour Katana peuvent être adaptés pour fonctionner avec le pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="5c8c2-124">Intergiciel (middleware) commun</span><span class="sxs-lookup"><span data-stu-id="5c8c2-124">Common middleware</span></span>

<span data-ttu-id="5c8c2-125">ASP.NET 4. x comprend de nombreux modules.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="5c8c2-126">De la même façon, ASP.NET Core possède également de nombreux composants d’intergiciel (middleware) disponibles.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="5c8c2-127">Les modules IIS peuvent être utilisés dans certains cas avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="5c8c2-128">Dans d’autres cas, l’intergiciel (middleware) ASP.NET Core natif peut être disponible.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="5c8c2-129">Le tableau suivant répertorie les intergiciels et composants de remplacement dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="5c8c2-130">Module</span><span class="sxs-lookup"><span data-stu-id="5c8c2-130">Module</span></span>                 |<span data-ttu-id="5c8c2-131">Module ASP.NET 4. x</span><span class="sxs-lookup"><span data-stu-id="5c8c2-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="5c8c2-132">Option ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c8c2-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="5c8c2-133">Erreurs HTTP</span><span class="sxs-lookup"><span data-stu-id="5c8c2-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="5c8c2-134">Middleware (intergiciel) de pages de codes d’état</span><span class="sxs-lookup"><span data-stu-id="5c8c2-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="5c8c2-135">Document par défaut</span><span class="sxs-lookup"><span data-stu-id="5c8c2-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="5c8c2-136">Middleware de fichiers par défaut</span><span class="sxs-lookup"><span data-stu-id="5c8c2-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="5c8c2-137">Exploration de répertoires</span><span class="sxs-lookup"><span data-stu-id="5c8c2-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="5c8c2-138">Middleware d’exploration des répertoires</span><span class="sxs-lookup"><span data-stu-id="5c8c2-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="5c8c2-139">Compression dynamique</span><span class="sxs-lookup"><span data-stu-id="5c8c2-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="5c8c2-140">Middleware de compression des réponses</span><span class="sxs-lookup"><span data-stu-id="5c8c2-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="5c8c2-141">Suivi des demandes ayant échoué</span><span class="sxs-lookup"><span data-stu-id="5c8c2-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="5c8c2-142">Journalisation ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c8c2-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="5c8c2-143">Mise en cache de fichiers</span><span class="sxs-lookup"><span data-stu-id="5c8c2-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="5c8c2-144">Intergiciel (middleware) de mise en cache des réponses</span><span class="sxs-lookup"><span data-stu-id="5c8c2-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="5c8c2-145">Mise en cache HTTP</span><span class="sxs-lookup"><span data-stu-id="5c8c2-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="5c8c2-146">Intergiciel (middleware) de mise en cache des réponses</span><span class="sxs-lookup"><span data-stu-id="5c8c2-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="5c8c2-147">Journalisation HTTP</span><span class="sxs-lookup"><span data-stu-id="5c8c2-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="5c8c2-148">Journalisation ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c8c2-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="5c8c2-149">Redirection HTTP</span><span class="sxs-lookup"><span data-stu-id="5c8c2-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="5c8c2-150">Intergiciel (middleware) de réécriture d’URL</span><span class="sxs-lookup"><span data-stu-id="5c8c2-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="5c8c2-151">Filtres ISAPI</span><span class="sxs-lookup"><span data-stu-id="5c8c2-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="5c8c2-152">Middleware</span><span class="sxs-lookup"><span data-stu-id="5c8c2-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="5c8c2-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="5c8c2-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="5c8c2-154">Middleware</span><span class="sxs-lookup"><span data-stu-id="5c8c2-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="5c8c2-155">Filtrage des demandes</span><span class="sxs-lookup"><span data-stu-id="5c8c2-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="5c8c2-156">Intergiciel (middleware) de réécriture d’URL IRule</span><span class="sxs-lookup"><span data-stu-id="5c8c2-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="5c8c2-157">&#8224; de réécriture d’URL</span><span class="sxs-lookup"><span data-stu-id="5c8c2-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="5c8c2-158">Intergiciel (middleware) de réécriture d’URL</span><span class="sxs-lookup"><span data-stu-id="5c8c2-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="5c8c2-159">Compression statique</span><span class="sxs-lookup"><span data-stu-id="5c8c2-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="5c8c2-160">Middleware de compression des réponses</span><span class="sxs-lookup"><span data-stu-id="5c8c2-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="5c8c2-161">Contenu statique</span><span class="sxs-lookup"><span data-stu-id="5c8c2-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="5c8c2-162">Middleware de fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="5c8c2-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="5c8c2-163">Autorisation d’URL</span><span class="sxs-lookup"><span data-stu-id="5c8c2-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="5c8c2-164">Identité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c8c2-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="5c8c2-165">Cette liste n’est pas exhaustive, mais elle doit vous faire une idée du mappage existant entre les deux infrastructures.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="5c8c2-166">Pour obtenir une liste plus détaillée, consultez [modules IIS avec ASP.net Core](/aspnet/core/host-and-deploy/iis/modules).</span><span class="sxs-lookup"><span data-stu-id="5c8c2-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="5c8c2-167">Intergiciel (middleware) personnalisé</span><span class="sxs-lookup"><span data-stu-id="5c8c2-167">Custom middleware</span></span>

<span data-ttu-id="5c8c2-168">Les intergiciels (middleware) intégrés ne gèrent pas tous les scénarios nécessaires pour une application.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="5c8c2-169">Dans ce cas, il est judicieux de créer votre propre intergiciel.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="5c8c2-170">Il existe plusieurs façons de définir des intergiciels (middleware), le plus simple étant un délégué simple.</span><span class="sxs-lookup"><span data-stu-id="5c8c2-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="5c8c2-171">Examinez l’intergiciel (middleware) suivant, qui accepte une demande de culture d’une chaîne de requête :</span><span class="sxs-lookup"><span data-stu-id="5c8c2-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

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

<span data-ttu-id="5c8c2-172">L’intergiciel peut également être défini en tant que classe, soit en implémentant l’interface, soit `IMiddleware` en suivant la Convention d’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="5c8c2-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="5c8c2-173">Pour plus d’informations, consultez [Write custom ASP.net Core middleware](/aspnet/core/fundamentals/middleware/write).</span><span class="sxs-lookup"><span data-stu-id="5c8c2-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5c8c2-174">[Précédent](data.md) 
> [Suivant](config.md)</span><span class="sxs-lookup"><span data-stu-id="5c8c2-174">[Previous](data.md)
[Next](config.md)</span></span>
