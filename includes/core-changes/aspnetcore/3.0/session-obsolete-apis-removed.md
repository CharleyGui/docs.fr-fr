---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198422"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="c29a7-101">État de la session : Les API obsolètes supprimées</span><span class="sxs-lookup"><span data-stu-id="c29a7-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="c29a7-102">Les API obsolètes pour configurer les cookies de session ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="c29a7-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="c29a7-103">Pour plus d’informations, voir [aspnet/Annonces 257](https://github.com/aspnet/Announcements/issues/257).</span><span class="sxs-lookup"><span data-stu-id="c29a7-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c29a7-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c29a7-104">Version introduced</span></span>

<span data-ttu-id="c29a7-105">3.0</span><span class="sxs-lookup"><span data-stu-id="c29a7-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c29a7-106">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="c29a7-106">Reason for change</span></span>

<span data-ttu-id="c29a7-107">Ce changement applique la cohérence entre les API pour configurer les fonctionnalités qui utilisent des cookies.</span><span class="sxs-lookup"><span data-stu-id="c29a7-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c29a7-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c29a7-108">Recommended action</span></span>

<span data-ttu-id="c29a7-109">Migrer l’utilisation des API supprimées à leurs nouveaux remplacements.</span><span class="sxs-lookup"><span data-stu-id="c29a7-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="c29a7-110">Prenons l’exemple suivant dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="c29a7-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

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

#### <a name="category"></a><span data-ttu-id="c29a7-111">Category</span><span class="sxs-lookup"><span data-stu-id="c29a7-111">Category</span></span>

<span data-ttu-id="c29a7-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c29a7-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c29a7-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="c29a7-113">Affected APIs</span></span>

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
