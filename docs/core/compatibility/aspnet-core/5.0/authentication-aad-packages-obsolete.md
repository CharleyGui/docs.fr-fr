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
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="18bef-103">Authentification : AzureAD. UI et AzureADB2C. UI API et packages marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="18bef-103">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="18bef-104">Dans ASP.NET Core 2,1, l’intégration avec l’authentification Azure Active Directory (Azure AD) et Azure Active Directory B2C (Azure AD B2C) est fournie par les packages [Microsoft. AspNetCore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) et [Microsoft. AspNetCore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) .</span><span class="sxs-lookup"><span data-stu-id="18bef-104">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="18bef-105">La fonctionnalité fournie par ces packages est basée sur le point de terminaison Azure AD v 1.0.</span><span class="sxs-lookup"><span data-stu-id="18bef-105">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="18bef-106">Dans ASP.NET Core 5,0 et versions ultérieures, l’intégration avec l’authentification Azure AD et Azure AD B2C est assurée par le package [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) .</span><span class="sxs-lookup"><span data-stu-id="18bef-106">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="18bef-107">Ce package est basé sur la plateforme d’identité Microsoft, anciennement appelée point de terminaison Azure AD v 2.0.</span><span class="sxs-lookup"><span data-stu-id="18bef-107">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="18bef-108">Par conséquent, les anciennes API des `Microsoft.AspNetCore.Authentication.AzureAD.UI` `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages et étaient dépréciées.</span><span class="sxs-lookup"><span data-stu-id="18bef-108">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="18bef-109">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).</span><span class="sxs-lookup"><span data-stu-id="18bef-109">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="18bef-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="18bef-110">Version introduced</span></span>

<span data-ttu-id="18bef-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="18bef-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="18bef-112">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="18bef-112">Old behavior</span></span>

<span data-ttu-id="18bef-113">Les API n’ont pas été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="18bef-113">The APIs weren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="18bef-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="18bef-114">New behavior</span></span>

<span data-ttu-id="18bef-115">Les API sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="18bef-115">The APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="18bef-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="18bef-116">Reason for change</span></span>

<span data-ttu-id="18bef-117">La fonctionnalité d’authentification Azure AD et Azure AD B2C a été migrée vers les API de la bibliothèque d’authentification Microsoft (MSAL) fournies par `Microsoft.Identity.Web` .</span><span class="sxs-lookup"><span data-stu-id="18bef-117">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="18bef-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="18bef-118">Recommended action</span></span>

<span data-ttu-id="18bef-119">Suivez les `Microsoft.Identity.Web` instructions de l’API pour les [applications Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) et les [API Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span><span class="sxs-lookup"><span data-stu-id="18bef-119">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="18bef-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="18bef-120">Affected APIs</span></span>

* [<span data-ttu-id="18bef-121">Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="18bef-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="18bef-122">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="18bef-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="18bef-123">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADOptions</span><span class="sxs-lookup"><span data-stu-id="18bef-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="18bef-124">Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="18bef-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="18bef-125">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="18bef-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="18bef-126">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="18bef-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

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
