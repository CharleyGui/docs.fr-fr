---
title: Modifications avec rupture ASP.NET Core
titleSuffix: ''
description: Répertorie les dernières modifications apportées à ASP.NET Core.
ms.date: 04/29/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 2e89a14c948365da1e7a04fc8d5ca4008842f8d8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446967"
---
# <a name="aspnet-core-breaking-changes"></a>Modifications avec rupture ASP.NET Core

ASP.NET Core fournit les fonctionnalités de développement d’applications Web utilisées par .NET Core.

Les modifications avec rupture suivantes sont documentées sur cette page :

- [Anti-contrefaçon, CORS, diagnostics, MVC et API de routage obsolètes supprimés](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Authentification : Google + Deprecated](#authentication-google-deprecated-and-replaced)
- [Authentification : propriété HttpContext. Authentication supprimée](#authentication-httpcontextauthentication-property-removed)
- [Authentification : types Newtonsoft. JSON remplacés](#authentication-newtonsoftjson-types-replaced)
- [Authentification : OAuthHandler ExchangeCodeAsync signature a changé](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autorisation : surcharge AddAuthorization déplacée vers un assembly différent](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autorisation : IAllowAnonymous supprimé de AuthorizationFilterContext. filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure : packages d’intégration Azure préfixés par Microsoft supprimés](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Caching : propriété CompactOnMemoryPressure supprimée](#caching-compactonmemorypressure-property-removed)
- [Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Mise en cache : les types « pubternal » ResponseCaching sont devenus internes](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Protection des données : DataProtection. AzureStorage utilise les nouvelles API de stockage Azure](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Extensions : modifications de référence de package affectant certains packages NuGet](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hébergement : l’hôte générique limite l’injection du constructeur de démarrage](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hébergement : redirection HTTPs activée pour les applications hors processus IIS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hébergement : types IHostingEnvironment et IApplicationLifetime remplacés](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [HTTP : le navigateur SameSite les modifications d’impact sur l’authentification](#http-browser-samesite-changes-impact-authentication)
- [HTTP : extensibilité de DefaultHttpContext supprimée](#http-defaulthttpcontext-extensibility-removed)
- [HTTP : les champs HeaderNames ont été modifiés en ReadOnly statique](#http-headernames-constants-changed-to-static-readonly)
- [HTTP : instances HttpClient créées par IHttpClientFactory enregistrer les codes d’état des entiers](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [HTTP : modifications de l’infrastructure du corps de la réponse](#http-response-body-infrastructure-changes)
- [HTTP : certaines valeurs par défaut de SameSite de cookie ont été modifiées](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP : e/s synchrone désactivée par défaut](#http-synchronous-io-disabled-in-all-servers)
- [Identité : surcharge de la méthode AddDefaultUI supprimée](#identity-adddefaultui-method-overload-removed)
- [Identité : modification de la version du bootstrap de l’interface utilisateur](#identity-default-bootstrap-version-of-ui-changed)
- [Identité : SignInAsync lève une exception pour l’identité non authentifiée](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Identité : le constructeur SignInManager accepte le nouveau paramètre](#identity-signinmanager-constructor-accepts-new-parameter)
- [Identité : l’interface utilisateur utilise la fonctionnalité de ressources Web statiques](#identity-ui-uses-static-web-assets-feature)
- [Kestrel : adaptateurs de connexion supprimés](#kestrel-connection-adapters-removed)
- [Kestrel : un assembly HTTPs vide a été supprimé](#kestrel-empty-https-assembly-removed)
- [Kestrel : les en-têtes de demande de code de fin sont déplacés vers la nouvelle collection](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel : modifications apportées à la couche d’abstraction de transport](#kestrel-transport-abstractions-removed-and-made-public)
- [Localisation : API marquées comme obsolètes](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Localisation : API « Pubternal » supprimées](#localization-pubternal-apis-removed)
- [Localisation : classe ResourceManagerWithCultureStringLocalizer et membre d’interface WithCulture supprimé](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [Journalisation : classe DebugLogger rendue interne](#logging-debuglogger-class-made-internal)
- [MVC : suffixe asynchrone d’action de contrôleur supprimé](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC : outil de précompilation déconseillé](#mvc-precompilation-tool-deprecated)
- [MVC : types modifiés en interne](#mvc-pubternal-types-changed-to-internal)
- [MVC : Shim de compatibilité de l’API Web supprimé](#mvc-web-api-compatibility-shim-removed)
- [Razor : la compilation du runtime a été déplacée vers un package](#razor-runtime-compilation-moved-to-a-package)
- [État de session : API obsolètes supprimées](#session-state-obsolete-apis-removed)
- [Framework partagé : suppression d’assembly de Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Framework partagé : Microsoft. AspNetCore. All supprimé](#shared-framework-removed-microsoftaspnetcoreall)
- [Signalr : HandshakeProtocol. SuccessHandshakeData remplacé](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [Signalr : méthodes HubConnection supprimées](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [Signalr : les constructeurs HubConnectionContext ont été modifiés](#signalr-hubconnectioncontext-constructors-changed)
- [Signalr : modification du nom du package client JavaScript](#signalr-javascript-client-package-name-changed)
- [Signalr : protocole MessagePack Hub déplacé vers le package MessagePack 2. x](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [Signalr : type d’options de protocole MessagePack Hub modifié](#signalr-messagepack-hub-protocol-options-type-changed)
- [Signalr : API obsolètes](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [Signalr : les méthodes UseSignalR et UseConnections ont été supprimées](#signalr-usesignalr-and-useconnections-methods-removed)
- [SPAs : SpaServices et NodeServices-modification de l’enregistreur d’événements de console par défaut](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [SPAs : SpaServices et NodeServices marqués comme obsolètes](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Fichiers statiques : le type de contenu CSV est passé à conforme aux normes](#static-files-csv-content-type-changed-to-standards-compliant)
- [Framework cible : .NET Framework pas pris en charge](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Core 5,0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE [Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Core 3,1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3,0

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
