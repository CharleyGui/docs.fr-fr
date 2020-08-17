---
title: Modules, gestionnaires et intergiciel (middleware)
description: En savoir plus sur la gestion des requêtes HTTP avec les modules, les gestionnaires et l’intergiciel (middleware).
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 10/11/2019
ms.openlocfilehash: 639755dd78892df1b70ea5245a9584e575fbf691
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267878"
---
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="6b536-103">Modules, gestionnaires et intergiciel (middleware)</span><span class="sxs-lookup"><span data-stu-id="6b536-103">Modules, handlers, and middleware</span></span>

<span data-ttu-id="6b536-104">Une application ASP.NET Core est basée sur une série d' *intergiciels (middleware*).</span><span class="sxs-lookup"><span data-stu-id="6b536-104">An ASP.NET Core app is built upon a series of *middleware*.</span></span> <span data-ttu-id="6b536-105">L’intergiciel est un gestionnaire qui est organisé dans un pipeline pour gérer les demandes et les réponses.</span><span class="sxs-lookup"><span data-stu-id="6b536-105">Middleware is handlers that are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="6b536-106">Dans une application Web Forms, les modules et les gestionnaires HTTP résolvent des problèmes similaires.</span><span class="sxs-lookup"><span data-stu-id="6b536-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="6b536-107">Dans ASP.NET Core, les modules, les gestionnaires, *global.asax.cs*et le cycle de vie de l’application sont remplacés par un intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="6b536-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="6b536-108">Dans ce chapitre, vous allez découvrir l’intergiciel (middleware) dans le contexte d’une Blazor application.</span><span class="sxs-lookup"><span data-stu-id="6b536-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="6b536-109">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="6b536-109">Overview</span></span>

<span data-ttu-id="6b536-110">Le pipeline de requête ASP.NET Core est composé d’une séquence de délégués de requête, appelés l’un après l’autre.</span><span class="sxs-lookup"><span data-stu-id="6b536-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="6b536-111">Le diagramme suivant illustre le concept.</span><span class="sxs-lookup"><span data-stu-id="6b536-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="6b536-112">Le thread d’exécution suit les flèches noires.</span><span class="sxs-lookup"><span data-stu-id="6b536-112">The thread of execution follows the black arrows.</span></span>

![pipeline](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="6b536-114">Le diagramme précédent n’a pas de concept d’événements de cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="6b536-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="6b536-115">Ce concept est fondamental pour gérer les demandes de ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="6b536-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="6b536-116">Ce système facilite la définition du processus en cours et permet l’insertion d’un intergiciel (middleware) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="6b536-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="6b536-117">L’intergiciel s’exécute dans l’ordre dans lequel il est ajouté au pipeline de requête.</span><span class="sxs-lookup"><span data-stu-id="6b536-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="6b536-118">Elles sont également ajoutées dans le code au lieu des fichiers de configuration, généralement dans *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="6b536-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="6b536-119">Katana</span><span class="sxs-lookup"><span data-stu-id="6b536-119">Katana</span></span>

<span data-ttu-id="6b536-120">Les lecteurs connaissant Katana se sentent à l’aise dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b536-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="6b536-121">En fait, Katana est une infrastructure à partir de laquelle dérive ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b536-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="6b536-122">Il a introduit des modèles d’intergiciel et de pipeline similaires pour ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="6b536-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="6b536-123">Les intergiciels (middleware) conçus pour Katana peuvent être adaptés pour fonctionner avec le pipeline ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b536-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="6b536-124">Intergiciel (middleware) commun</span><span class="sxs-lookup"><span data-stu-id="6b536-124">Common middleware</span></span>

<span data-ttu-id="6b536-125">ASP.NET 4. x comprend de nombreux modules.</span><span class="sxs-lookup"><span data-stu-id="6b536-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="6b536-126">De la même façon, ASP.NET Core possède également de nombreux composants d’intergiciel (middleware) disponibles.</span><span class="sxs-lookup"><span data-stu-id="6b536-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="6b536-127">Les modules IIS peuvent être utilisés dans certains cas avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b536-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="6b536-128">Dans d’autres cas, l’intergiciel (middleware) ASP.NET Core natif peut être disponible.</span><span class="sxs-lookup"><span data-stu-id="6b536-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="6b536-129">Le tableau suivant répertorie les intergiciels et composants de remplacement dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b536-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="6b536-130">Module</span><span class="sxs-lookup"><span data-stu-id="6b536-130">Module</span></span>                 |<span data-ttu-id="6b536-131">Module ASP.NET 4. x</span><span class="sxs-lookup"><span data-stu-id="6b536-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="6b536-132">Option ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b536-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="6b536-133">Erreurs HTTP</span><span class="sxs-lookup"><span data-stu-id="6b536-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="6b536-134">Middleware (intergiciel) de pages de codes d’état</span><span class="sxs-lookup"><span data-stu-id="6b536-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="6b536-135">Document par défaut</span><span class="sxs-lookup"><span data-stu-id="6b536-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="6b536-136">Middleware de fichiers par défaut</span><span class="sxs-lookup"><span data-stu-id="6b536-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="6b536-137">Exploration de répertoires</span><span class="sxs-lookup"><span data-stu-id="6b536-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="6b536-138">Middleware d’exploration des répertoires</span><span class="sxs-lookup"><span data-stu-id="6b536-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="6b536-139">Compression dynamique</span><span class="sxs-lookup"><span data-stu-id="6b536-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="6b536-140">Middleware de compression des réponses</span><span class="sxs-lookup"><span data-stu-id="6b536-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="6b536-141">Suivi des demandes ayant échoué</span><span class="sxs-lookup"><span data-stu-id="6b536-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="6b536-142">Journalisation ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b536-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="6b536-143">Mise en cache de fichiers</span><span class="sxs-lookup"><span data-stu-id="6b536-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="6b536-144">Intergiciel (middleware) de mise en cache des réponses</span><span class="sxs-lookup"><span data-stu-id="6b536-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="6b536-145">Mise en cache HTTP</span><span class="sxs-lookup"><span data-stu-id="6b536-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="6b536-146">Intergiciel (middleware) de mise en cache des réponses</span><span class="sxs-lookup"><span data-stu-id="6b536-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="6b536-147">Journalisation HTTP</span><span class="sxs-lookup"><span data-stu-id="6b536-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="6b536-148">Journalisation ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b536-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="6b536-149">Redirection HTTP</span><span class="sxs-lookup"><span data-stu-id="6b536-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="6b536-150">Intergiciel (middleware) de réécriture d’URL</span><span class="sxs-lookup"><span data-stu-id="6b536-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="6b536-151">Filtres ISAPI</span><span class="sxs-lookup"><span data-stu-id="6b536-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="6b536-152">Middleware</span><span class="sxs-lookup"><span data-stu-id="6b536-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="6b536-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="6b536-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="6b536-154">Middleware</span><span class="sxs-lookup"><span data-stu-id="6b536-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="6b536-155">Filtrage des demandes</span><span class="sxs-lookup"><span data-stu-id="6b536-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="6b536-156">Intergiciel (middleware) de réécriture d’URL IRule</span><span class="sxs-lookup"><span data-stu-id="6b536-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="6b536-157">&#8224; de réécriture d’URL</span><span class="sxs-lookup"><span data-stu-id="6b536-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="6b536-158">Intergiciel (middleware) de réécriture d’URL</span><span class="sxs-lookup"><span data-stu-id="6b536-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="6b536-159">Compression statique</span><span class="sxs-lookup"><span data-stu-id="6b536-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="6b536-160">Middleware de compression des réponses</span><span class="sxs-lookup"><span data-stu-id="6b536-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="6b536-161">Contenu statique</span><span class="sxs-lookup"><span data-stu-id="6b536-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="6b536-162">Middleware de fichiers statiques</span><span class="sxs-lookup"><span data-stu-id="6b536-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="6b536-163">Autorisation d’URL</span><span class="sxs-lookup"><span data-stu-id="6b536-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="6b536-164">Identité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b536-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="6b536-165">Cette liste n’est pas exhaustive, mais elle doit vous faire une idée du mappage existant entre les deux infrastructures.</span><span class="sxs-lookup"><span data-stu-id="6b536-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="6b536-166">Pour obtenir une liste plus détaillée, consultez [modules IIS avec ASP.net Core](/aspnet/core/host-and-deploy/iis/modules).</span><span class="sxs-lookup"><span data-stu-id="6b536-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="6b536-167">Intergiciel (middleware) personnalisé</span><span class="sxs-lookup"><span data-stu-id="6b536-167">Custom middleware</span></span>

<span data-ttu-id="6b536-168">Les intergiciels (middleware) intégrés ne gèrent pas tous les scénarios nécessaires pour une application.</span><span class="sxs-lookup"><span data-stu-id="6b536-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="6b536-169">Dans ce cas, il est judicieux de créer votre propre intergiciel.</span><span class="sxs-lookup"><span data-stu-id="6b536-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="6b536-170">Il existe plusieurs façons de définir des intergiciels (middleware), le plus simple étant un délégué simple.</span><span class="sxs-lookup"><span data-stu-id="6b536-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="6b536-171">Examinez l’intergiciel (middleware) suivant, qui accepte une demande de culture d’une chaîne de requête :</span><span class="sxs-lookup"><span data-stu-id="6b536-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

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

<span data-ttu-id="6b536-172">L’intergiciel peut également être défini en tant que classe, soit en implémentant l’interface, soit `IMiddleware` en suivant la Convention d’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="6b536-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="6b536-173">Pour plus d’informations, consultez [Write custom ASP.net Core middleware](/aspnet/core/fundamentals/middleware/write).</span><span class="sxs-lookup"><span data-stu-id="6b536-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6b536-174">[Précédent](data.md) 
> [Suivant](config.md)</span><span class="sxs-lookup"><span data-stu-id="6b536-174">[Previous](data.md)
[Next](config.md)</span></span>
