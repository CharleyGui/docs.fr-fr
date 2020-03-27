---
title: changements de rupture de ASP.NET Core
titleSuffix: ''
description: Répertorie les changements de rupture dans ASP.NET Core.
ms.date: 03/26/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 05272032f2b93c8ae89377a20e6fdafc2ff0eb7b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345326"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="be650-103">changements de rupture de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="be650-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="be650-104">ASP.NET Core fournit les fonctionnalités de développement d’applications Web utilisées par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be650-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="be650-105">Les modifications de rupture suivantes sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="be650-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="be650-106">L’antiforgerie obsolète, le CORS, le diagnostic, le MVC et les API de routage supprimés</span><span class="sxs-lookup"><span data-stu-id="be650-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="be650-107">Authentification : Dépréciation de Google</span><span class="sxs-lookup"><span data-stu-id="be650-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="be650-108">Authentification: HttpContext.Authentication propriété supprimée</span><span class="sxs-lookup"><span data-stu-id="be650-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="be650-109">Authentification: Newtonsoft.Json types remplacés</span><span class="sxs-lookup"><span data-stu-id="be650-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="be650-110">Authentification : La signature OAuthHandler ExchangeCodeAsync modifiée</span><span class="sxs-lookup"><span data-stu-id="be650-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="be650-111">Autorisation : AddAuthorization surcharge déplacée à différents assemblages</span><span class="sxs-lookup"><span data-stu-id="be650-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="be650-112">Autorisation: IAllowAnonymous retiré de AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="be650-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="be650-113">Autorisation: IAuthorizationPolicyProvider implémentations nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="be650-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="be650-114">Azure : Les paquets d’intégration Azure préfixés de Microsoft supprimés</span><span class="sxs-lookup"><span data-stu-id="be650-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="be650-115">Caching: CompactOnMemoryPressure propriété supprimée</span><span class="sxs-lookup"><span data-stu-id="be650-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="be650-116">Caching: Microsoft.Extensions.Caching.SqlServer utilise le nouveau paquet SqlClient</span><span class="sxs-lookup"><span data-stu-id="be650-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="be650-117">Caching: ResponseCaching "pubternal" types changés à l’interne</span><span class="sxs-lookup"><span data-stu-id="be650-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="be650-118">Protection des données : DataProtection.AzureStorage utilise de nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="be650-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="be650-119">Hébergement: AspNetCoreModule V1 supprimé de Windows Hosting Bundle</span><span class="sxs-lookup"><span data-stu-id="be650-119">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="be650-120">Hébergement: L’hôte générique restreint l’injection de constructeurs startup</span><span class="sxs-lookup"><span data-stu-id="be650-120">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="be650-121">Hébergement : Redirection HTTPS activée pour les applications hors-processus DE l’IIS</span><span class="sxs-lookup"><span data-stu-id="be650-121">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="be650-122">Hébergement: IHostingEnvironment et IApplicationLifetime types remplacés</span><span class="sxs-lookup"><span data-stu-id="be650-122">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="be650-123">Hébergement: ObjectPoolProvider supprimé des dépendances WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="be650-123">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="be650-124">HTTP: Navigateur SameSite changements d’impact authentification</span><span class="sxs-lookup"><span data-stu-id="be650-124">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="be650-125">HTTP: DefaultHttpContext extétabilité supprimée</span><span class="sxs-lookup"><span data-stu-id="be650-125">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="be650-126">HTTP: Champs HeaderNames changé à la lis-d’œur statique</span><span class="sxs-lookup"><span data-stu-id="be650-126">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="be650-127">HTTP : Changements dans l’infrastructure du corps d’intervention</span><span class="sxs-lookup"><span data-stu-id="be650-127">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="be650-128">HTTP: Certains cookie SameSite valeurs par défaut changé</span><span class="sxs-lookup"><span data-stu-id="be650-128">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="be650-129">HTTP: Synchronous IO désactivé par défaut</span><span class="sxs-lookup"><span data-stu-id="be650-129">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="be650-130">Identité : Surcharge de la méthode AddDefaultUI supprimée</span><span class="sxs-lookup"><span data-stu-id="be650-130">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="be650-131">Identité: UI Bootstrap version change</span><span class="sxs-lookup"><span data-stu-id="be650-131">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="be650-132">Identité: SignInAsync jette l’exception pour l’identité non authentique</span><span class="sxs-lookup"><span data-stu-id="be650-132">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="be650-133">Identité: SignInManager constructeur accepte un nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="be650-133">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="be650-134">Identité : L’interface utilisateur utilise la fonction d’actifs Web statiques</span><span class="sxs-lookup"><span data-stu-id="be650-134">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="be650-135">Kestrel: adaptateurs de connexion supprimés</span><span class="sxs-lookup"><span data-stu-id="be650-135">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="be650-136">Kestrel: L’assemblage HTTPS vide supprimé</span><span class="sxs-lookup"><span data-stu-id="be650-136">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="be650-137">Kestrel: En-têtes de remorque de demande déplacé à la nouvelle collection</span><span class="sxs-lookup"><span data-stu-id="be650-137">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="be650-138">Kestrel : Changements de couche d’abstraction de transport</span><span class="sxs-lookup"><span data-stu-id="be650-138">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="be650-139">Localisation : les API sont désuètes</span><span class="sxs-lookup"><span data-stu-id="be650-139">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="be650-140">Enregistrement: DebugLogger classe rendue interne</span><span class="sxs-lookup"><span data-stu-id="be650-140">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="be650-141">MVC: Action contrôleur Async suffixe supprimé</span><span class="sxs-lookup"><span data-stu-id="be650-141">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="be650-142">MVC: JsonResult a déménagé à Microsoft.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="be650-142">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="be650-143">MVC : Outil de précomplification déprécié</span><span class="sxs-lookup"><span data-stu-id="be650-143">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="be650-144">MVC : Types passés à l’interne</span><span class="sxs-lookup"><span data-stu-id="be650-144">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="be650-145">MVC: Web API cal de compatibilité supprimé</span><span class="sxs-lookup"><span data-stu-id="be650-145">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="be650-146">Razor: Compilation Runtime déplacé à un paquet</span><span class="sxs-lookup"><span data-stu-id="be650-146">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="be650-147">État de la session : Les API obsolètes supprimées</span><span class="sxs-lookup"><span data-stu-id="be650-147">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="be650-148">Cadre partagé : Suppression de l’assemblage de Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="be650-148">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="be650-149">Cadre partagé: Microsoft.AspNetCore.All supprimé</span><span class="sxs-lookup"><span data-stu-id="be650-149">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="be650-150">SignalR: HandshakeProtocol.SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="be650-150">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="be650-151">SignalR: Les méthodes HubConnection supprimées</span><span class="sxs-lookup"><span data-stu-id="be650-151">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="be650-152">SignalR : Les constructeurs HubConnectionContext ont changé</span><span class="sxs-lookup"><span data-stu-id="be650-152">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="be650-153">SignalR: Changement de nom du client JavaScript</span><span class="sxs-lookup"><span data-stu-id="be650-153">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="be650-154">SignalR: MessagePack Hub Protocol déplacé à MessagePack 2.x paquet</span><span class="sxs-lookup"><span data-stu-id="be650-154">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="be650-155">SignalR: API obsolètes</span><span class="sxs-lookup"><span data-stu-id="be650-155">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="be650-156">SignalR: UtilisationSignalR et UseConnections méthodes supprimées</span><span class="sxs-lookup"><span data-stu-id="be650-156">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="be650-157">SPAs: SpaServices et NodeServices console logger change de défaut de repli</span><span class="sxs-lookup"><span data-stu-id="be650-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="be650-158">SPAs: SpaServices et NodeServices marqués obsolètes</span><span class="sxs-lookup"><span data-stu-id="be650-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="be650-159">Cadre cible : .NET Framework non pris en charge</span><span class="sxs-lookup"><span data-stu-id="be650-159">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="be650-160">ASP.NET Noyau 5.0</span><span class="sxs-lookup"><span data-stu-id="be650-160">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="be650-161">ASP.NET Noyau 3.1</span><span class="sxs-lookup"><span data-stu-id="be650-161">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="be650-162">ASP.NET Noyau 3.0</span><span class="sxs-lookup"><span data-stu-id="be650-162">ASP.NET Core 3.0</span></span>

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
