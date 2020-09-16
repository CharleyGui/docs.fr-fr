---
title: Modifications avec rupture ASP.NET Core
titleSuffix: ''
description: Répertorie les dernières modifications apportées à ASP.NET Core.
ms.date: 09/11/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 4c3167e9cad193b6a5a11be399e8be529df3be55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539581"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="38043-103">Modifications avec rupture ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="38043-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="38043-104">ASP.NET Core fournit les fonctionnalités de développement d’applications Web utilisées par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38043-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="38043-105">Sélectionnez l’un des liens suivants pour les modifications avec rupture dans une version spécifique :</span><span class="sxs-lookup"><span data-stu-id="38043-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="38043-106">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="38043-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="38043-107">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="38043-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="38043-108">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="38043-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="38043-109">Les modifications avec rupture suivantes dans ASP.NET Core 3,0, 3,1 et 5,0 sont documentées sur cette page :</span><span class="sxs-lookup"><span data-stu-id="38043-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="38043-110">Anti-contrefaçon, CORS, diagnostics, MVC et API de routage obsolètes supprimés</span><span class="sxs-lookup"><span data-stu-id="38043-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="38043-111">Authentification : AzureAD. UI et AzureADB2C. UI API et packages marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="38043-111">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>](#authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete)
- [<span data-ttu-id="38043-112">Authentification : Google + Deprecated</span><span class="sxs-lookup"><span data-stu-id="38043-112">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="38043-113">Authentification : propriété HttpContext. Authentication supprimée</span><span class="sxs-lookup"><span data-stu-id="38043-113">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="38043-114">Authentification : Newtonsoft.Jssur les types remplacés</span><span class="sxs-lookup"><span data-stu-id="38043-114">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="38043-115">Authentification : OAuthHandler ExchangeCodeAsync signature a changé</span><span class="sxs-lookup"><span data-stu-id="38043-115">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="38043-116">Autorisation : surcharge AddAuthorization déplacée vers un assembly différent</span><span class="sxs-lookup"><span data-stu-id="38043-116">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="38043-117">Autorisation : IAllowAnonymous supprimé de AuthorizationFilterContext. filters</span><span class="sxs-lookup"><span data-stu-id="38043-117">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="38043-118">Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode</span><span class="sxs-lookup"><span data-stu-id="38043-118">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="38043-119">Autorisation : la ressource dans le routage du point de terminaison est HttpContext</span><span class="sxs-lookup"><span data-stu-id="38043-119">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="38043-120">Azure : packages d’intégration Azure préfixés par Microsoft supprimés</span><span class="sxs-lookup"><span data-stu-id="38043-120">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="38043-121">Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET</span><span class="sxs-lookup"><span data-stu-id="38043-121">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="38043-122">Éblouissante : espace blanc non significatif tronqué des composants au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="38043-122">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="38043-123">Éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés</span><span class="sxs-lookup"><span data-stu-id="38043-123">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>](#blazor-rendertreeframe-readonly-public-fields-have-become-properties)
- [<span data-ttu-id="38043-124">Éblouissante : version cible du .NET Framework des packages NuGet modifiée</span><span class="sxs-lookup"><span data-stu-id="38043-124">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="38043-125">Caching : propriété CompactOnMemoryPressure supprimée</span><span class="sxs-lookup"><span data-stu-id="38043-125">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="38043-126">Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient</span><span class="sxs-lookup"><span data-stu-id="38043-126">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="38043-127">Mise en cache : les types « pubternal » ResponseCaching sont devenus internes</span><span class="sxs-lookup"><span data-stu-id="38043-127">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="38043-128">Protection des données : DataProtection. AzureStorage utilise les nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="38043-128">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="38043-129">Extensions : modifications de référence de package affectant certains packages NuGet</span><span class="sxs-lookup"><span data-stu-id="38043-129">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="38043-130">Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows</span><span class="sxs-lookup"><span data-stu-id="38043-130">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="38043-131">Hébergement : l’hôte générique limite l’injection du constructeur de démarrage</span><span class="sxs-lookup"><span data-stu-id="38043-131">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="38043-132">Hébergement : redirection HTTPs activée pour les applications hors processus IIS</span><span class="sxs-lookup"><span data-stu-id="38043-132">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="38043-133">Hébergement : types IHostingEnvironment et IApplicationLifetime remplacés</span><span class="sxs-lookup"><span data-stu-id="38043-133">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="38043-134">Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="38043-134">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="38043-135">HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés</span><span class="sxs-lookup"><span data-stu-id="38043-135">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="38043-136">HTTP : le navigateur SameSite les modifications d’impact sur l’authentification</span><span class="sxs-lookup"><span data-stu-id="38043-136">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="38043-137">HTTP : extensibilité de DefaultHttpContext supprimée</span><span class="sxs-lookup"><span data-stu-id="38043-137">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="38043-138">HTTP : les champs HeaderNames ont été modifiés en ReadOnly statique</span><span class="sxs-lookup"><span data-stu-id="38043-138">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="38043-139">HTTP : instances HttpClient créées par IHttpClientFactory enregistrer les codes d’état des entiers</span><span class="sxs-lookup"><span data-stu-id="38043-139">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="38043-140">HTTP : modifications de l’infrastructure du corps de la réponse</span><span class="sxs-lookup"><span data-stu-id="38043-140">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="38043-141">HTTP : certaines valeurs par défaut de SameSite de cookie ont été modifiées</span><span class="sxs-lookup"><span data-stu-id="38043-141">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="38043-142">HTTP : e/s synchrone désactivée par défaut</span><span class="sxs-lookup"><span data-stu-id="38043-142">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="38043-143">HttpSys : la renégociation de certificat client est désactivée par défaut</span><span class="sxs-lookup"><span data-stu-id="38043-143">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="38043-144">Identité : surcharge de la méthode AddDefaultUI supprimée</span><span class="sxs-lookup"><span data-stu-id="38043-144">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="38043-145">Identité : modification de la version du bootstrap de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="38043-145">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="38043-146">Identité : SignInAsync lève une exception pour l’identité non authentifiée</span><span class="sxs-lookup"><span data-stu-id="38043-146">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="38043-147">Identité : le constructeur SignInManager accepte le nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="38043-147">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="38043-148">Identité : l’interface utilisateur utilise la fonctionnalité de ressources Web statiques</span><span class="sxs-lookup"><span data-stu-id="38043-148">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="38043-149">IIS : les chaînes de requête d’intergiciel UrlRewrite sont conservées</span><span class="sxs-lookup"><span data-stu-id="38043-149">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="38043-150">Kestrel : modifications de configuration au moment de l’exécution détectées par défaut</span><span class="sxs-lookup"><span data-stu-id="38043-150">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="38043-151">Kestrel : adaptateurs de connexion supprimés</span><span class="sxs-lookup"><span data-stu-id="38043-151">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="38043-152">Kestrel : les versions de protocole TLS prises en charge par défaut ont été modifiées</span><span class="sxs-lookup"><span data-stu-id="38043-152">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="38043-153">Kestrel : un assembly HTTPs vide a été supprimé</span><span class="sxs-lookup"><span data-stu-id="38043-153">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="38043-154">Kestrel : HTTP/2 désactivé sur TLS sur des versions de Windows incompatibles</span><span class="sxs-lookup"><span data-stu-id="38043-154">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="38043-155">Kestrel : transport Libuv marqué comme obsolète</span><span class="sxs-lookup"><span data-stu-id="38043-155">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="38043-156">Kestrel : les en-têtes de demande de code de fin sont déplacés vers la nouvelle collection</span><span class="sxs-lookup"><span data-stu-id="38043-156">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="38043-157">Kestrel : modifications apportées à la couche d’abstraction de transport</span><span class="sxs-lookup"><span data-stu-id="38043-157">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="38043-158">Localisation : API marquées comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="38043-158">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="38043-159">Localisation : API « Pubternal » supprimées</span><span class="sxs-lookup"><span data-stu-id="38043-159">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="38043-160">Localisation : le constructeur obsolète a été supprimé de l’intergiciel (middleware) de localisation des demandes</span><span class="sxs-lookup"><span data-stu-id="38043-160">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="38043-161">Localisation : classe ResourceManagerWithCultureStringLocalizer et membre d’interface WithCulture supprimé</span><span class="sxs-lookup"><span data-stu-id="38043-161">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="38043-162">Journalisation : classe DebugLogger rendue interne</span><span class="sxs-lookup"><span data-stu-id="38043-162">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="38043-163">Intergiciel : page d’erreurs de base de données marquée comme obsolète</span><span class="sxs-lookup"><span data-stu-id="38043-163">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="38043-164">Intergiciel : l’intergiciel (middleware) du gestionnaire d’exceptions lève une exception d’origine si le gestionnaire est introuvable</span><span class="sxs-lookup"><span data-stu-id="38043-164">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>](#middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found)
- [<span data-ttu-id="38043-165">MVC : suffixe asynchrone d’action de contrôleur supprimé</span><span class="sxs-lookup"><span data-stu-id="38043-165">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="38043-166">MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="38043-166">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="38043-167">MVC : outil de précompilation déconseillé</span><span class="sxs-lookup"><span data-stu-id="38043-167">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="38043-168">MVC : types modifiés en interne</span><span class="sxs-lookup"><span data-stu-id="38043-168">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="38043-169">MVC : Shim de compatibilité de l’API Web supprimé</span><span class="sxs-lookup"><span data-stu-id="38043-169">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="38043-170">Razor : l’API RazorTemplateEngine a été supprimée</span><span class="sxs-lookup"><span data-stu-id="38043-170">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="38043-171">Razor : la compilation du runtime a été déplacée vers un package</span><span class="sxs-lookup"><span data-stu-id="38043-171">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="38043-172">Sécurité : encodage du nom du cookie supprimé</span><span class="sxs-lookup"><span data-stu-id="38043-172">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="38043-173">Sécurité : les versions du package NuGet IdentityModel ont été mises à jour</span><span class="sxs-lookup"><span data-stu-id="38043-173">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="38043-174">État de session : API obsolètes supprimées</span><span class="sxs-lookup"><span data-stu-id="38043-174">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="38043-175">Framework partagé : suppression d’assembly de Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="38043-175">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="38043-176">Framework partagé : Microsoft. AspNetCore. All supprimé</span><span class="sxs-lookup"><span data-stu-id="38043-176">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="38043-177">Signalr : HandshakeProtocol. SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="38043-177">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="38043-178">Signalr : méthodes HubConnection supprimées</span><span class="sxs-lookup"><span data-stu-id="38043-178">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="38043-179">Signalr : les constructeurs HubConnectionContext ont été modifiés</span><span class="sxs-lookup"><span data-stu-id="38043-179">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="38043-180">Signalr : modification du nom du package client JavaScript</span><span class="sxs-lookup"><span data-stu-id="38043-180">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="38043-181">Signalr : protocole MessagePack Hub déplacé vers le package MessagePack 2. x</span><span class="sxs-lookup"><span data-stu-id="38043-181">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="38043-182">Signalr : type d’options de protocole MessagePack Hub modifié</span><span class="sxs-lookup"><span data-stu-id="38043-182">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="38043-183">Signalr : API obsolètes</span><span class="sxs-lookup"><span data-stu-id="38043-183">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="38043-184">Signalr : les méthodes UseSignalR et UseConnections ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="38043-184">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="38043-185">SPAs : SpaServices et NodeServices-modification de l’enregistreur d’événements de console par défaut</span><span class="sxs-lookup"><span data-stu-id="38043-185">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="38043-186">SPAs : SpaServices et NodeServices marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="38043-186">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="38043-187">Fichiers statiques : le type de contenu CSV est passé à conforme aux normes</span><span class="sxs-lookup"><span data-stu-id="38043-187">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="38043-188">Framework cible : .NET Framework pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="38043-188">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="38043-189">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="38043-189">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete](~/includes/core-changes/aspnetcore/5.0/authentication-aad-packages-obsolete.md)]

***

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: RenderTreeFrame readonly public fields have become properties](~/includes/core-changes/aspnetcore/5.0/blazor-rendertreeframe-fields-become-properties.md)]

***

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

***

[!INCLUDE[Middleware: Exception Handler Middleware throws original exception if handler not found](~/includes/core-changes/aspnetcore/5.0/middleware-exception-handler-throws-original-exception.md)]

***

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

***

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="38043-190">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="38043-190">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="38043-191">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="38043-191">ASP.NET Core 3.0</span></span>

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

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

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
