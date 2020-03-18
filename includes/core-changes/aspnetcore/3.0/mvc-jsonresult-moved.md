---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901962"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="a38a8-101">MVC: JsonResult a déménagé à Microsoft.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="a38a8-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="a38a8-102">`JsonResult`a déménagé `Microsoft.AspNetCore.Mvc.Core` à l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="a38a8-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="a38a8-103">Ce type était défini dans [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="a38a8-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="a38a8-104">Un attribut de niveau d’assemblage [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) a été ajouté pour `Microsoft.AspNetCore.Mvc.Formatters.Json` résoudre ce problème pour la majorité des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="a38a8-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="a38a8-105">Les applications qui utilisent des bibliothèques tierces peuvent rencontrer des problèmes.</span><span class="sxs-lookup"><span data-stu-id="a38a8-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a38a8-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a38a8-106">Version introduced</span></span>

<span data-ttu-id="a38a8-107">3.0 Aperçu 6</span><span class="sxs-lookup"><span data-stu-id="a38a8-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a38a8-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a38a8-108">Old behavior</span></span>

<span data-ttu-id="a38a8-109">Une application utilisant une bibliothèque basée sur 2,2 se construit avec succès.</span><span class="sxs-lookup"><span data-stu-id="a38a8-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a38a8-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a38a8-110">New behavior</span></span>

<span data-ttu-id="a38a8-111">Une application utilisant une bibliothèque basée sur 2,2 échoue compilation.</span><span class="sxs-lookup"><span data-stu-id="a38a8-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="a38a8-112">Une erreur contenant une variation du texte suivant est fournie :</span><span class="sxs-lookup"><span data-stu-id="a38a8-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="a38a8-113">Pour un exemple d’un tel numéro, voir [dotnet/aspnetcore 7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="a38a8-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a38a8-114">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="a38a8-114">Reason for change</span></span>

<span data-ttu-id="a38a8-115">Modifications au niveau de la plate-forme dans la composition de ASP.NET Core, telle qu’elle est décrite à [l’aspnet/Announcements 325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="a38a8-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a38a8-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a38a8-116">Recommended action</span></span>

<span data-ttu-id="a38a8-117">Les bibliothèques compilées par rapport `Microsoft.AspNetCore.Mvc.Formatters.Json` à la version 2.2 de peut-être besoin de recompte pour résoudre le problème pour tous les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="a38a8-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="a38a8-118">En cas d’incidence, communiquez avec l’auteur de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a38a8-118">If affected, contact the library author.</span></span> <span data-ttu-id="a38a8-119">Demande de recomplification de la bibliothèque pour cibler ASP.NET Noyau 3.0.</span><span class="sxs-lookup"><span data-stu-id="a38a8-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="a38a8-120">Category</span><span class="sxs-lookup"><span data-stu-id="a38a8-120">Category</span></span>

<span data-ttu-id="a38a8-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a38a8-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a38a8-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="a38a8-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
