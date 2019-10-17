---
ms.openlocfilehash: 2945465bb6a3a362dc640641056712dffd73d559
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394262"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="cac56-101">Authentification : propriété HttpContext. Authentication supprimée</span><span class="sxs-lookup"><span data-stu-id="cac56-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="cac56-102">La propriété déconseillée `Authentication` sur `HttpContext` a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="cac56-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cac56-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="cac56-103">Change description</span></span>

<span data-ttu-id="cac56-104">Dans le cadre de [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504), la propriété déconseillée `Authentication` sur `HttpContext` a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="cac56-104">As part of [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="cac56-105">La propriété `Authentication` est dépréciée depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="cac56-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="cac56-106">Un [Guide de migration](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) a été publié pour migrer le code à l’aide de cette propriété déconseillée vers les nouvelles API de remplacement.</span><span class="sxs-lookup"><span data-stu-id="cac56-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="cac56-107">Les autres classes/API inutilisées associées à l’ancienne pile d’authentification ASP.NET Core 1. x ont été supprimées dans la validation [aspnet/AspNetCore@d7a7c65](https://github.com/aspnet/AspNetCore/commit/d7a7c65).</span><span class="sxs-lookup"><span data-stu-id="cac56-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [aspnet/AspNetCore@d7a7c65](https://github.com/aspnet/AspNetCore/commit/d7a7c65).</span></span>

<span data-ttu-id="cac56-108">Pour plus d’informations, consultez [ASPNET/AspNetCore # 6533](https://github.com/aspnet/AspNetCore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="cac56-108">For discussion, see [aspnet/AspNetCore#6533](https://github.com/aspnet/AspNetCore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cac56-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cac56-109">Version introduced</span></span>

<span data-ttu-id="cac56-110">3,0</span><span class="sxs-lookup"><span data-stu-id="cac56-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cac56-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="cac56-111">Reason for change</span></span>

<span data-ttu-id="cac56-112">Les API ASP.NET Core 1,0 ont été remplacées par des méthodes d’extension dans <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="cac56-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cac56-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cac56-113">Recommended action</span></span>

<span data-ttu-id="cac56-114">Consultez le [Guide de migration](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span><span class="sxs-lookup"><span data-stu-id="cac56-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="cac56-115">Category</span><span class="sxs-lookup"><span data-stu-id="cac56-115">Category</span></span>

<span data-ttu-id="cac56-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cac56-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cac56-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="cac56-117">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
