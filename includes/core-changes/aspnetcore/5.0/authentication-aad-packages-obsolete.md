---
ms.openlocfilehash: 8bcd9987cb061233c8476b9c083a224fc0e25440
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539467"
---
### <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="6befa-101">Authentification : AzureAD. UI et AzureADB2C. UI API et packages marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="6befa-101">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="6befa-102">Dans ASP.NET Core 2,1, l’intégration avec l’authentification Azure Active Directory (Azure AD) et Azure Active Directory B2C (Azure AD B2C) est fournie par les packages [Microsoft. AspNetCore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) et [Microsoft. AspNetCore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) .</span><span class="sxs-lookup"><span data-stu-id="6befa-102">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="6befa-103">La fonctionnalité fournie par ces packages est basée sur le point de terminaison Azure AD v 1.0.</span><span class="sxs-lookup"><span data-stu-id="6befa-103">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="6befa-104">Dans ASP.NET Core 5,0 et versions ultérieures, l’intégration avec l’authentification Azure AD et Azure AD B2C est assurée par le package [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) .</span><span class="sxs-lookup"><span data-stu-id="6befa-104">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="6befa-105">Ce package est basé sur la plateforme d’identité Microsoft, anciennement appelée point de terminaison Azure AD v 2.0.</span><span class="sxs-lookup"><span data-stu-id="6befa-105">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="6befa-106">Par conséquent, les anciennes API des `Microsoft.AspNetCore.Authentication.AzureAD.UI` `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages et étaient dépréciées.</span><span class="sxs-lookup"><span data-stu-id="6befa-106">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="6befa-107">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).</span><span class="sxs-lookup"><span data-stu-id="6befa-107">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6befa-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6befa-108">Version introduced</span></span>

<span data-ttu-id="6befa-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="6befa-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6befa-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6befa-110">Old behavior</span></span>

<span data-ttu-id="6befa-111">Les API n’ont pas été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="6befa-111">The APIs weren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6befa-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6befa-112">New behavior</span></span>

<span data-ttu-id="6befa-113">Les API sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="6befa-113">The APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6befa-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6befa-114">Reason for change</span></span>

<span data-ttu-id="6befa-115">La fonctionnalité d’authentification Azure AD et Azure AD B2C a été migrée vers les API de la bibliothèque d’authentification Microsoft (MSAL) fournies par `Microsoft.Identity.Web` .</span><span class="sxs-lookup"><span data-stu-id="6befa-115">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6befa-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6befa-116">Recommended action</span></span>

<span data-ttu-id="6befa-117">Suivez les `Microsoft.Identity.Web` instructions de l’API pour les [applications Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) et les [API Web](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span><span class="sxs-lookup"><span data-stu-id="6befa-117">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

#### <a name="category"></a><span data-ttu-id="6befa-118">Category</span><span class="sxs-lookup"><span data-stu-id="6befa-118">Category</span></span>

<span data-ttu-id="6befa-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6befa-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6befa-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="6befa-120">Affected APIs</span></span>

* [<span data-ttu-id="6befa-121">Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="6befa-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="6befa-122">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="6befa-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="6befa-123">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADOptions</span><span class="sxs-lookup"><span data-stu-id="6befa-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="6befa-124">Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="6befa-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="6befa-125">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="6befa-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="6befa-126">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="6befa-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
