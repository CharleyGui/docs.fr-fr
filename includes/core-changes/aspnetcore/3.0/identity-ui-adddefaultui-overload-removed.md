---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637195"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="8da4c-101">Identité : surcharge de la méthode AddDefaultUI supprimée</span><span class="sxs-lookup"><span data-stu-id="8da4c-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="8da4c-102">À compter de ASP.NET Core 3,0, la surcharge de méthode [IdentityBuilderUIExtensions. AddDefaultUI (IdentityBuilder, UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) n’existe plus.</span><span class="sxs-lookup"><span data-stu-id="8da4c-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8da4c-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8da4c-103">Version introduced</span></span>

<span data-ttu-id="8da4c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="8da4c-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8da4c-105">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="8da4c-105">Reason for change</span></span>

<span data-ttu-id="8da4c-106">Cette modification est le résultat de l’adoption de la fonctionnalité de ressources Web statiques.</span><span class="sxs-lookup"><span data-stu-id="8da4c-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8da4c-107">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="8da4c-107">Recommended action</span></span>

<span data-ttu-id="8da4c-108">Appelez <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> au lieu de la surcharge qui accepte deux arguments.</span><span class="sxs-lookup"><span data-stu-id="8da4c-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="8da4c-109">Si vous utilisez bootstrap 3, ajoutez également la ligne suivante à un `<PropertyGroup>` élément dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="8da4c-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="8da4c-110">Category</span><span class="sxs-lookup"><span data-stu-id="8da4c-110">Category</span></span>

<span data-ttu-id="8da4c-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8da4c-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8da4c-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="8da4c-112">Affected APIs</span></span>

[<span data-ttu-id="8da4c-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="8da4c-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
