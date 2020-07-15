---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309143"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>Localisation : le constructeur obsolète a été supprimé de l’intergiciel (middleware) de localisation des demandes

Le <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructeur qui ne dispose pas d’un <xref:Microsoft.Extensions.Logging.ILoggerFactory> paramètre a été marqué comme obsolète [dans cette validation](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0). Dans ASP.NET Core 5,0, le constructeur obsolète a été supprimé. Pour plus d’informations, consultez [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="old-behavior"></a>Ancien comportement

Le `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructeur obsolète existe.

#### <a name="new-behavior"></a>Nouveau comportement

Le `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructeur obsolète n’existe pas.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification permet de s’assurer que l’intergiciel (middleware) de localisation des demandes a toujours accès à un enregistreur d’événements.

#### <a name="recommended-action"></a>Action recommandée

Lors de la construction manuelle d’une instance de `RequestLocalizationMiddleware` , passer une `ILoggerFactory` instance dans le constructeur. Si une `ILoggerFactory` instance valide n’est pas disponible dans ce contexte, envisagez de passer le constructeur d’intergiciel (middleware) à une <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

[RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
