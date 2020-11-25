---
title: Modifications avec rupture ASP.NET Core
titleSuffix: ''
description: Répertorie les dernières modifications apportées à ASP.NET Core 3,0 et 3,1.
ms.date: 11/03/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 40dfda77dd51ed46366ec6cd8f6598070e8ce846
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "96032318"
---
# <a name="aspnet-core-breaking-changes-for-versions-30-and-31"></a><span data-ttu-id="238fd-103">ASP.NET Core modifications avec rupture pour les versions 3,0 et 3,1</span><span class="sxs-lookup"><span data-stu-id="238fd-103">ASP.NET Core breaking changes for versions 3.0 and 3.1</span></span>

<span data-ttu-id="238fd-104">ASP.NET Core fournit les fonctionnalités de développement d’applications Web utilisées par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="238fd-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="238fd-105">Sélectionnez l’un des liens suivants pour les modifications avec rupture dans une version spécifique :</span><span class="sxs-lookup"><span data-stu-id="238fd-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="238fd-106">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="238fd-106">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="238fd-107">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="238fd-107">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="238fd-108">Les modifications avec rupture suivantes dans ASP.NET Core 3,0 et 3,1 sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="238fd-108">The following breaking changes in ASP.NET Core 3.0 and 3.1 are documented on this page:</span></span>

- [<span data-ttu-id="238fd-109">Anti-contrefaçon, CORS, diagnostics, MVC et API de routage obsolètes supprimés</span><span class="sxs-lookup"><span data-stu-id="238fd-109">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="238fd-110">Authentification : Google + Deprecated</span><span class="sxs-lookup"><span data-stu-id="238fd-110">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="238fd-111">Authentification : propriété HttpContext. Authentication supprimée</span><span class="sxs-lookup"><span data-stu-id="238fd-111">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="238fd-112">Authentification : Newtonsoft.Jssur les types remplacés</span><span class="sxs-lookup"><span data-stu-id="238fd-112">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="238fd-113">Authentification : OAuthHandler ExchangeCodeAsync signature a changé</span><span class="sxs-lookup"><span data-stu-id="238fd-113">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="238fd-114">Autorisation : surcharge AddAuthorization déplacée vers un assembly différent</span><span class="sxs-lookup"><span data-stu-id="238fd-114">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="238fd-115">Autorisation : IAllowAnonymous supprimé de AuthorizationFilterContext. filters</span><span class="sxs-lookup"><span data-stu-id="238fd-115">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="238fd-116">Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="238fd-116">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="238fd-117">Caching : propriété CompactOnMemoryPressure supprimée</span><span class="sxs-lookup"><span data-stu-id="238fd-117">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="238fd-118">Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient</span><span class="sxs-lookup"><span data-stu-id="238fd-118">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="238fd-119">Protection des données : DataProtection. blob utilise les nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="238fd-119">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [<span data-ttu-id="238fd-120">Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows</span><span class="sxs-lookup"><span data-stu-id="238fd-120">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="238fd-121">Hébergement : l’hôte générique limite l’injection du constructeur de démarrage</span><span class="sxs-lookup"><span data-stu-id="238fd-121">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="238fd-122">Hébergement : redirection HTTPs activée pour les applications hors processus IIS</span><span class="sxs-lookup"><span data-stu-id="238fd-122">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="238fd-123">Hébergement : types IHostingEnvironment et IApplicationLifetime remplacés</span><span class="sxs-lookup"><span data-stu-id="238fd-123">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="238fd-124">Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="238fd-124">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="238fd-125">HTTP : le navigateur SameSite les modifications d’impact sur l’authentification</span><span class="sxs-lookup"><span data-stu-id="238fd-125">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="238fd-126">HTTP : extensibilité de DefaultHttpContext supprimée</span><span class="sxs-lookup"><span data-stu-id="238fd-126">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="238fd-127">HTTP : les champs HeaderNames ont été modifiés en ReadOnly statique</span><span class="sxs-lookup"><span data-stu-id="238fd-127">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="238fd-128">HTTP : modifications de l’infrastructure du corps de la réponse</span><span class="sxs-lookup"><span data-stu-id="238fd-128">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="238fd-129">HTTP : certaines valeurs par défaut de SameSite de cookie ont été modifiées</span><span class="sxs-lookup"><span data-stu-id="238fd-129">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="238fd-130">HTTP : e/s synchrone désactivée par défaut</span><span class="sxs-lookup"><span data-stu-id="238fd-130">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="238fd-131">Identité : surcharge de la méthode AddDefaultUI supprimée</span><span class="sxs-lookup"><span data-stu-id="238fd-131">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="238fd-132">Identité : modification de la version du bootstrap de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="238fd-132">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="238fd-133">Identité : SignInAsync lève une exception pour l’identité non authentifiée</span><span class="sxs-lookup"><span data-stu-id="238fd-133">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="238fd-134">Identité : le constructeur SignInManager accepte le nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="238fd-134">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="238fd-135">Identité : l’interface utilisateur utilise la fonctionnalité de ressources Web statiques</span><span class="sxs-lookup"><span data-stu-id="238fd-135">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="238fd-136">Kestrel : adaptateurs de connexion supprimés</span><span class="sxs-lookup"><span data-stu-id="238fd-136">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="238fd-137">Kestrel : un assembly HTTPs vide a été supprimé</span><span class="sxs-lookup"><span data-stu-id="238fd-137">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="238fd-138">Kestrel : les en-têtes de demande de code de fin sont déplacés vers la nouvelle collection</span><span class="sxs-lookup"><span data-stu-id="238fd-138">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="238fd-139">Kestrel : modifications apportées à la couche d’abstraction de transport</span><span class="sxs-lookup"><span data-stu-id="238fd-139">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="238fd-140">Localisation : API marquées comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="238fd-140">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="238fd-141">Journalisation : classe DebugLogger rendue interne</span><span class="sxs-lookup"><span data-stu-id="238fd-141">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="238fd-142">MVC : suffixe asynchrone d’action de contrôleur supprimé</span><span class="sxs-lookup"><span data-stu-id="238fd-142">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="238fd-143">MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="238fd-143">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="238fd-144">MVC : outil de précompilation déconseillé</span><span class="sxs-lookup"><span data-stu-id="238fd-144">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="238fd-145">MVC : types modifiés en interne</span><span class="sxs-lookup"><span data-stu-id="238fd-145">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="238fd-146">MVC : Shim de compatibilité de l’API Web supprimé</span><span class="sxs-lookup"><span data-stu-id="238fd-146">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="238fd-147">Razor : l’API RazorTemplateEngine a été supprimée</span><span class="sxs-lookup"><span data-stu-id="238fd-147">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="238fd-148">Razor : la compilation du runtime a été déplacée vers un package</span><span class="sxs-lookup"><span data-stu-id="238fd-148">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="238fd-149">État de session : API obsolètes supprimées</span><span class="sxs-lookup"><span data-stu-id="238fd-149">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="238fd-150">Framework partagé : suppression d’assembly de Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="238fd-150">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="238fd-151">Framework partagé : Microsoft. AspNetCore. All supprimé</span><span class="sxs-lookup"><span data-stu-id="238fd-151">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="238fd-152">Signalr : HandshakeProtocol. SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="238fd-152">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="238fd-153">Signalr : méthodes HubConnection supprimées</span><span class="sxs-lookup"><span data-stu-id="238fd-153">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="238fd-154">Signalr : les constructeurs HubConnectionContext ont été modifiés</span><span class="sxs-lookup"><span data-stu-id="238fd-154">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="238fd-155">Signalr : modification du nom du package client JavaScript</span><span class="sxs-lookup"><span data-stu-id="238fd-155">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="238fd-156">Signalr : API obsolètes</span><span class="sxs-lookup"><span data-stu-id="238fd-156">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="238fd-157">SPAs : SpaServices et NodeServices-modification de l’enregistreur d’événements de console par défaut</span><span class="sxs-lookup"><span data-stu-id="238fd-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="238fd-158">SPAs : SpaServices et NodeServices marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="238fd-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="238fd-159">Framework cible : .NET Framework pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="238fd-159">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a><span data-ttu-id="238fd-160">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="238fd-160">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="238fd-161">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="238fd-161">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

<span data-ttu-id="238fd-162">\*\*_</span><span class="sxs-lookup"><span data-stu-id="238fd-162">\*\*_</span></span>

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

_*_

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

_*_

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

_*_

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

_*_

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

_*_

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

_*_

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

_*_

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

_*_

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

_*_

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

_*_

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

_*_

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

_*_

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

_*_

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

_*_

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

_*_

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

_*_

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

_*_

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

_*_

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

_*_

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

_*_

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

_*_

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

_*_

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

_*_

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

_*_

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

_*_

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

_*_

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

_*_

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

_*_

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

_*_

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

_*_

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

_*_

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

_*_

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

_*_

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

_*_

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

_*_

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

_*_

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

_*_

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

_*_

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

_*_

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

_*_

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

_*_

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

_*_

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

_*_

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

_*_

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

_*_

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

_*_

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

_*_

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

<span data-ttu-id="238fd-163">_\*\*</span><span class="sxs-lookup"><span data-stu-id="238fd-163">_\*\*</span></span>
