---
ms.openlocfilehash: 8bcd9987cb061233c8476b9c083a224fc0e25440
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539467"
---
### <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a>Authentification : AzureAD. UI et AzureADB2C. UI API et packages marqués comme obsolètes

Dans ASP.NET Core 2,1, l’intégration avec l’authentification Azure Active Directory (Azure AD) et Azure Active Directory B2C (Azure AD B2C) est fournie par les packages [Microsoft. AspNetCore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) et [Microsoft. AspNetCore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) . La fonctionnalité fournie par ces packages est basée sur le point de terminaison Azure AD v 1.0.

Dans ASP.NET Core 5,0 et versions ultérieures, l’intégration avec l’authentification Azure AD et Azure AD B2C est assurée par le package [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) . Ce package est basé sur la plateforme d’identité Microsoft, anciennement appelée point de terminaison Azure AD v 2.0. Par conséquent, les anciennes API des `Microsoft.AspNetCore.Authentication.AzureAD.UI` `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages et étaient dépréciées.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="old-behavior"></a>Ancien comportement

Les API n’ont pas été marquées comme obsolètes.

#### <a name="new-behavior"></a>Nouveau comportement

Les API sont marquées comme obsolètes.

#### <a name="reason-for-change"></a>Motif de modification

La fonctionnalité d’authentification Azure AD et Azure AD B2C a été migrée vers les API de la bibliothèque d’authentification Microsoft (MSAL) fournies par `Microsoft.Identity.Web` .

#### <a name="recommended-action"></a>Action recommandée

Suivez les `Microsoft.Identity.Web` instructions de l’API pour les [applications Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) et les [API Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

* [Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADOptions](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
