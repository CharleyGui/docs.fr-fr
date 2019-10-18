---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522671"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="15e7b-101">Identité : surcharge de la méthode AddDefaultUI supprimée</span><span class="sxs-lookup"><span data-stu-id="15e7b-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="15e7b-102">À compter de ASP.NET Core 3,0, la surcharge de méthode <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> n’existe plus.</span><span class="sxs-lookup"><span data-stu-id="15e7b-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="15e7b-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="15e7b-103">Version introduced</span></span>

<span data-ttu-id="15e7b-104">3,0</span><span class="sxs-lookup"><span data-stu-id="15e7b-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="15e7b-105">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="15e7b-105">Reason for change</span></span>

<span data-ttu-id="15e7b-106">Cette modification est le résultat de l’adoption de la fonctionnalité de ressources Web statiques.</span><span class="sxs-lookup"><span data-stu-id="15e7b-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="15e7b-107">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="15e7b-107">Recommended action</span></span>

<span data-ttu-id="15e7b-108">Appelez <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> à la place de la surcharge.</span><span class="sxs-lookup"><span data-stu-id="15e7b-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="15e7b-109">Si vous utilisez bootstrap 3, ajoutez également la ligne suivante à un élément `<PropertyGroup>` dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="15e7b-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="15e7b-110">Category</span><span class="sxs-lookup"><span data-stu-id="15e7b-110">Category</span></span>

<span data-ttu-id="15e7b-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="15e7b-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="15e7b-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="15e7b-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
