---
title: changements de rupture de ASP.NET Core
titleSuffix: ''
description: Répertorie les changements de rupture dans ASP.NET Core.
ms.date: 01/10/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: c54735cd53fb9cb48eb84045791ccc559fe683cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093173"
---
# <a name="aspnet-core-breaking-changes"></a>changements de rupture de ASP.NET Core

ASP.NET Core fournit les fonctionnalités de développement d’applications Web utilisées par .NET Core.

Les modifications de rupture suivantes sont documentées sur cette page :

- [HTTP: Navigateur SameSite changements d’impact authentification](#http-browser-samesite-changes-impact-authentication)
- [L’antiforgerie obsolète, le CORS, le diagnostic, le MVC et les API de routage supprimés](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Authentification : Dépréciation de Google](#authentication-google-deprecated-and-replaced)
- [Authentification: HttpContext.Authentication propriété supprimée](#authentication-httpcontextauthentication-property-removed)
- [Authentification: Newtonsoft.Json types remplacés](#authentication-newtonsoftjson-types-replaced)
- [Authentification : La signature OAuthHandler ExchangeCodeAsync modifiée](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autorisation : AddAuthorization surcharge déplacée à différents assemblages](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autorisation: IAllowAnonymous retiré de AuthorizationFilterContext.Filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autorisation: IAuthorizationPolicyProvider implémentations nécessitent une nouvelle méthode](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Caching: CompactOnMemoryPressure propriété supprimée](#caching-compactonmemorypressure-property-removed)
- [Caching: Microsoft.Extensions.Caching.SqlServer utilise le nouveau paquet SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Caching: ResponseCaching "pubternal" types changés à l’interne](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Protection des données : DataProtection.AzureStorage utilise de nouvelles API de stockage Azure](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Hébergement: AspNetCoreModule V1 supprimé de Windows Hosting Bundle](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hébergement: L’hôte générique restreint l’injection de constructeurs startup](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hébergement : Redirection HTTPS activée pour les applications hors-processus DE l’IIS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hébergement: IHostingEnvironment et IApplicationLifetime types remplacés](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hébergement: ObjectPoolProvider supprimé des dépendances WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: DefaultHttpContext extétabilité supprimée](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: Champs HeaderNames changé à la lis-d’œur statique](#http-headernames-constants-changed-to-static-readonly)
- [HTTP : Changements dans l’infrastructure du corps d’intervention](#http-response-body-infrastructure-changes)
- [HTTP: Certains cookie SameSite valeurs par défaut changé](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: Synchronous IO désactivé par défaut](#http-synchronous-io-disabled-in-all-servers)
- [Identité : Surcharge de la méthode AddDefaultUI supprimée](#identity-adddefaultui-method-overload-removed)
- [Identité: UI Bootstrap version change](#identity-default-bootstrap-version-of-ui-changed)
- [Identité: SignInAsync jette l’exception pour l’identité non authentique](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Identité: SignInManager constructeur accepte un nouveau paramètre](#identity-signinmanager-constructor-accepts-new-parameter)
- [Identité : L’interface utilisateur utilise la fonction d’actifs Web statiques](#identity-ui-uses-static-web-assets-feature)
- [Kestrel: adaptateurs de connexion supprimés](#kestrel-connection-adapters-removed)
- [Kestrel: L’assemblage HTTPS vide supprimé](#kestrel-empty-https-assembly-removed)
- [Kestrel: En-têtes de remorque de demande déplacé à la nouvelle collection](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel : Changements de couche d’abstraction de transport](#kestrel-transport-abstractions-removed-and-made-public)
- [Localisation : les API sont désuètes](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Enregistrement: DebugLogger classe rendue interne](#logging-debuglogger-class-made-internal)
- [MVC: Action contrôleur Async suffixe supprimé](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult a déménagé à Microsoft.AspNetCore.Mvc.Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC : Outil de précomplification déprécié](#mvc-precompilation-tool-deprecated)
- [MVC : Types passés à l’interne](#mvc-pubternal-types-changed-to-internal)
- [MVC: Web API cal de compatibilité supprimé](#mvc-web-api-compatibility-shim-removed)
- [Razor: Compilation Runtime déplacé à un paquet](#razor-runtime-compilation-moved-to-a-package)
- [État de la session : Les API obsolètes supprimées](#session-state-obsolete-apis-removed)
- [Cadre partagé : Suppression de l’assemblage de Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Cadre partagé: Microsoft.AspNetCore.All supprimé](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol.SuccessHandshakeData remplacé](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: Les méthodes HubConnection supprimées](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR : Les constructeurs HubConnectionContext ont changé](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: Changement de nom du client JavaScript](#signalr-javascript-client-package-name-changed)
- [SignalR: API obsolètes](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SPAs: SpaServices et NodeServices marqués obsolètes](#spas-spaservices-and-nodeservices-marked-obsolete)
- [SPAs: SpaServices et NodeServices console logger change de défaut de repli](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Cadre cible : .NET Framework non pris en charge](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a>ASP.NET Noyau 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Noyau 3.0

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
