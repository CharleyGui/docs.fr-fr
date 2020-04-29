---
title: Modifications avec rupture ASP.NET Core
titleSuffix: ''
description: Répertorie les dernières modifications apportées à ASP.NET Core.
ms.date: 04/28/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 454735028f8c0923b99e85ade30f498f13dd6cab
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507142"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="c0c6c-103">Modifications avec rupture ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c0c6c-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="c0c6c-104">ASP.NET Core fournit les fonctionnalités de développement d’applications Web utilisées par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0c6c-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="c0c6c-105">Les modifications avec rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="c0c6c-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="c0c6c-106">Anti-contrefaçon, CORS, diagnostics, MVC et API de routage obsolètes supprimés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="c0c6c-107">Authentification : Google + Deprecated</span><span class="sxs-lookup"><span data-stu-id="c0c6c-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="c0c6c-108">Authentification : propriété HttpContext. Authentication supprimée</span><span class="sxs-lookup"><span data-stu-id="c0c6c-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="c0c6c-109">Authentification : types Newtonsoft. JSON remplacés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="c0c6c-110">Authentification : OAuthHandler ExchangeCodeAsync signature a changé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="c0c6c-111">Autorisation : surcharge AddAuthorization déplacée vers un assembly différent</span><span class="sxs-lookup"><span data-stu-id="c0c6c-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="c0c6c-112">Autorisation : IAllowAnonymous supprimé de AuthorizationFilterContext. filters</span><span class="sxs-lookup"><span data-stu-id="c0c6c-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="c0c6c-113">Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="c0c6c-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="c0c6c-114">Azure : packages d’intégration Azure préfixés par Microsoft supprimés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="c0c6c-115">Caching : propriété CompactOnMemoryPressure supprimée</span><span class="sxs-lookup"><span data-stu-id="c0c6c-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="c0c6c-116">Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient</span><span class="sxs-lookup"><span data-stu-id="c0c6c-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="c0c6c-117">Mise en cache : les types « pubternal » ResponseCaching sont devenus internes</span><span class="sxs-lookup"><span data-stu-id="c0c6c-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c0c6c-118">Protection des données : DataProtection. AzureStorage utilise les nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="c0c6c-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="c0c6c-119">Extensions : modifications de référence de package affectant certains packages NuGet</span><span class="sxs-lookup"><span data-stu-id="c0c6c-119">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="c0c6c-120">Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows</span><span class="sxs-lookup"><span data-stu-id="c0c6c-120">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="c0c6c-121">Hébergement : l’hôte générique limite l’injection du constructeur de démarrage</span><span class="sxs-lookup"><span data-stu-id="c0c6c-121">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="c0c6c-122">Hébergement : redirection HTTPs activée pour les applications hors processus IIS</span><span class="sxs-lookup"><span data-stu-id="c0c6c-122">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="c0c6c-123">Hébergement : types IHostingEnvironment et IApplicationLifetime remplacés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-123">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="c0c6c-124">Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="c0c6c-124">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="c0c6c-125">HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-125">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="c0c6c-126">HTTP : le navigateur SameSite les modifications d’impact sur l’authentification</span><span class="sxs-lookup"><span data-stu-id="c0c6c-126">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="c0c6c-127">HTTP : extensibilité de DefaultHttpContext supprimée</span><span class="sxs-lookup"><span data-stu-id="c0c6c-127">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="c0c6c-128">HTTP : les champs HeaderNames ont été modifiés en ReadOnly statique</span><span class="sxs-lookup"><span data-stu-id="c0c6c-128">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="c0c6c-129">HTTP : modifications de l’infrastructure du corps de la réponse</span><span class="sxs-lookup"><span data-stu-id="c0c6c-129">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="c0c6c-130">HTTP : certaines valeurs par défaut de SameSite de cookie ont été modifiées</span><span class="sxs-lookup"><span data-stu-id="c0c6c-130">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="c0c6c-131">HTTP : e/s synchrone désactivée par défaut</span><span class="sxs-lookup"><span data-stu-id="c0c6c-131">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="c0c6c-132">Identité : surcharge de la méthode AddDefaultUI supprimée</span><span class="sxs-lookup"><span data-stu-id="c0c6c-132">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="c0c6c-133">Identité : modification de la version du bootstrap de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="c0c6c-133">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="c0c6c-134">Identité : SignInAsync lève une exception pour l’identité non authentifiée</span><span class="sxs-lookup"><span data-stu-id="c0c6c-134">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="c0c6c-135">Identité : le constructeur SignInManager accepte le nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="c0c6c-135">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="c0c6c-136">Identité : l’interface utilisateur utilise la fonctionnalité de ressources Web statiques</span><span class="sxs-lookup"><span data-stu-id="c0c6c-136">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="c0c6c-137">Kestrel : adaptateurs de connexion supprimés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-137">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="c0c6c-138">Kestrel : un assembly HTTPs vide a été supprimé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-138">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="c0c6c-139">Kestrel : les en-têtes de demande de code de fin sont déplacés vers la nouvelle collection</span><span class="sxs-lookup"><span data-stu-id="c0c6c-139">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="c0c6c-140">Kestrel : modifications apportées à la couche d’abstraction de transport</span><span class="sxs-lookup"><span data-stu-id="c0c6c-140">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="c0c6c-141">Localisation : API marquées comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="c0c6c-141">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="c0c6c-142">Journalisation : classe DebugLogger rendue interne</span><span class="sxs-lookup"><span data-stu-id="c0c6c-142">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="c0c6c-143">MVC : suffixe asynchrone d’action de contrôleur supprimé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-143">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="c0c6c-144">MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="c0c6c-144">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="c0c6c-145">MVC : outil de précompilation déconseillé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-145">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="c0c6c-146">MVC : types modifiés en interne</span><span class="sxs-lookup"><span data-stu-id="c0c6c-146">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c0c6c-147">MVC : Shim de compatibilité de l’API Web supprimé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-147">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="c0c6c-148">Razor : la compilation du runtime a été déplacée vers un package</span><span class="sxs-lookup"><span data-stu-id="c0c6c-148">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="c0c6c-149">État de session : API obsolètes supprimées</span><span class="sxs-lookup"><span data-stu-id="c0c6c-149">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="c0c6c-150">Framework partagé : suppression d’assembly de Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="c0c6c-150">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="c0c6c-151">Framework partagé : Microsoft. AspNetCore. All supprimé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-151">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="c0c6c-152">Signalr : HandshakeProtocol. SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="c0c6c-152">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="c0c6c-153">Signalr : méthodes HubConnection supprimées</span><span class="sxs-lookup"><span data-stu-id="c0c6c-153">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="c0c6c-154">Signalr : les constructeurs HubConnectionContext ont été modifiés</span><span class="sxs-lookup"><span data-stu-id="c0c6c-154">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="c0c6c-155">Signalr : modification du nom du package client JavaScript</span><span class="sxs-lookup"><span data-stu-id="c0c6c-155">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="c0c6c-156">Signalr : protocole MessagePack Hub déplacé vers le package MessagePack 2. x</span><span class="sxs-lookup"><span data-stu-id="c0c6c-156">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="c0c6c-157">Signalr : type d’options de protocole MessagePack Hub modifié</span><span class="sxs-lookup"><span data-stu-id="c0c6c-157">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="c0c6c-158">Signalr : API obsolètes</span><span class="sxs-lookup"><span data-stu-id="c0c6c-158">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="c0c6c-159">Signalr : les méthodes UseSignalR et UseConnections ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="c0c6c-159">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="c0c6c-160">SPAs : SpaServices et NodeServices-modification de l’enregistreur d’événements de console par défaut</span><span class="sxs-lookup"><span data-stu-id="c0c6c-160">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="c0c6c-161">SPAs : SpaServices et NodeServices marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="c0c6c-161">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="c0c6c-162">Fichiers statiques : le type de contenu CSV est passé à conforme aux normes</span><span class="sxs-lookup"><span data-stu-id="c0c6c-162">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="c0c6c-163">Framework cible : .NET Framework pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="c0c6c-163">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="c0c6c-164">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="c0c6c-164">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="c0c6c-165">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c0c6c-165">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="c0c6c-166">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="c0c6c-166">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
