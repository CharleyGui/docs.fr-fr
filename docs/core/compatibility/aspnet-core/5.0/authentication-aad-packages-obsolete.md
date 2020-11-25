---
title: 'Modification avec rupture : authentification : AzureAD. UI et AzureADB2C. UI et packages marqués comme obsolètes'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée authentification : AzureAD. UI et AzureADB2C. UI API et packages marqués comme obsolètes'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c977ba4d6e34fc5f11133bdd1446a94d54efcb63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761231"
---
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a>Authentification : AzureAD. UI et AzureADB2C. UI API et packages marqués comme obsolètes

Dans ASP.NET Core 2,1, l’intégration avec l’authentification Azure Active Directory (Azure AD) et Azure Active Directory B2C (Azure AD B2C) est fournie par les packages [Microsoft. AspNetCore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) et [Microsoft. AspNetCore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) . La fonctionnalité fournie par ces packages est basée sur le point de terminaison Azure AD v 1.0.

Dans ASP.NET Core 5,0 et versions ultérieures, l’intégration avec l’authentification Azure AD et Azure AD B2C est assurée par le package [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) . Ce package est basé sur la plateforme d’identité Microsoft, anciennement appelée point de terminaison Azure AD v 2.0. Par conséquent, les anciennes API des `Microsoft.AspNetCore.Authentication.AzureAD.UI` `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages et étaient dépréciées.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 8

## <a name="old-behavior"></a>Ancien comportement

Les API n’ont pas été marquées comme obsolètes.

## <a name="new-behavior"></a>Nouveau comportement

Les API sont marquées comme obsolètes.

## <a name="reason-for-change"></a>Motif de modification

La fonctionnalité d’authentification Azure AD et Azure AD B2C a été migrée vers les API de la bibliothèque d’authentification Microsoft (MSAL) fournies par `Microsoft.Identity.Web` .

## <a name="recommended-action"></a>Action recommandée

Suivez les `Microsoft.Identity.Web` instructions de l’API pour les [applications Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) et les [API Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).

## <a name="affected-apis"></a>API affectées

* [Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADOptions](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
