---
ms.openlocfilehash: 96c2a32dd7cca91e965601d715bbd4625bba439a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032624"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="78454-101">MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="78454-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="78454-102">`JsonResult` a été déplacé vers l' `Microsoft.AspNetCore.Mvc.Core` assembly.</span><span class="sxs-lookup"><span data-stu-id="78454-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="78454-103">Ce type est utilisé pour être défini dans [Microsoft.AspNetCore.Mvc.Formatters.Jssur](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="78454-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="78454-104">Un attribut [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) au niveau de l’assembly a été ajouté à `Microsoft.AspNetCore.Mvc.Formatters.Json` pour résoudre ce problème pour la majorité des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="78454-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="78454-105">Les applications qui utilisent des bibliothèques tierces peuvent rencontrer des problèmes.</span><span class="sxs-lookup"><span data-stu-id="78454-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="78454-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="78454-106">Version introduced</span></span>

<span data-ttu-id="78454-107">3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="78454-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="78454-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="78454-108">Old behavior</span></span>

<span data-ttu-id="78454-109">Une application utilisant une bibliothèque 2,2 est générée avec succès.</span><span class="sxs-lookup"><span data-stu-id="78454-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="78454-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="78454-110">New behavior</span></span>

<span data-ttu-id="78454-111">Une application utilisant une bibliothèque 2,2 ne parvient pas à se compiler.</span><span class="sxs-lookup"><span data-stu-id="78454-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="78454-112">Une erreur contenant une variante du texte suivant est fournie :</span><span class="sxs-lookup"><span data-stu-id="78454-112">An error containing a variation of the following text is provided:</span></span>

```output
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="78454-113">Pour obtenir un exemple de ce type de problème, consultez [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="78454-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="78454-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="78454-114">Reason for change</span></span>

<span data-ttu-id="78454-115">Modifications au niveau de la plateforme de la composition de ASP.NET Core comme décrit dans [ASPNET/announcements # 325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="78454-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="78454-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="78454-116">Recommended action</span></span>

<span data-ttu-id="78454-117">Les bibliothèques compilées avec la version 2,2 de `Microsoft.AspNetCore.Mvc.Formatters.Json` peuvent avoir besoin d’être recompilées pour résoudre le problème pour tous les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="78454-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="78454-118">S’il est affecté, contactez l’auteur de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="78454-118">If affected, contact the library author.</span></span> <span data-ttu-id="78454-119">Demandez la recompilation de la bibliothèque pour cibler ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="78454-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="78454-120">Category</span><span class="sxs-lookup"><span data-stu-id="78454-120">Category</span></span>

<span data-ttu-id="78454-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78454-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="78454-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="78454-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
