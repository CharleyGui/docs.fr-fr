---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032644"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="e61dd-101">État de session : API obsolètes supprimées</span><span class="sxs-lookup"><span data-stu-id="e61dd-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="e61dd-102">Les API obsolètes pour la configuration des cookies de session ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="e61dd-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="e61dd-103">Pour plus d’informations, consultez [ASPNET/announcements # 257](https://github.com/aspnet/Announcements/issues/257).</span><span class="sxs-lookup"><span data-stu-id="e61dd-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e61dd-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e61dd-104">Version introduced</span></span>

<span data-ttu-id="e61dd-105">3.0</span><span class="sxs-lookup"><span data-stu-id="e61dd-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e61dd-106">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e61dd-106">Reason for change</span></span>

<span data-ttu-id="e61dd-107">Cette modification applique la cohérence entre les API pour la configuration des fonctionnalités qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="e61dd-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e61dd-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e61dd-108">Recommended action</span></span>

<span data-ttu-id="e61dd-109">Migrez l’utilisation des API supprimées vers leurs remplacements plus récents.</span><span class="sxs-lookup"><span data-stu-id="e61dd-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="e61dd-110">Prenons l’exemple suivant dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="e61dd-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(ServiceCollection services)
{
    services.AddSession(options =>
    {
        // Removed obsolete APIs
        options.CookieName = "SessionCookie";
        options.CookieDomain = "contoso.com";
        options.CookiePath = "/";
        options.CookieHttpOnly = true;
        options.CookieSecure = CookieSecurePolicy.Always;

        // new API
        options.Cookie.Name = "SessionCookie";
        options.Cookie.Domain = "contoso.com";
        options.Cookie.Path = "/";
        options.Cookie.HttpOnly = true;
        options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    });
}
```

#### <a name="category"></a><span data-ttu-id="e61dd-111">Category</span><span class="sxs-lookup"><span data-stu-id="e61dd-111">Category</span></span>

<span data-ttu-id="e61dd-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e61dd-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e61dd-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="e61dd-113">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure?displayProperty=fullName>

<!-- 

#### Affected APIs

- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieName`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure`

-->
