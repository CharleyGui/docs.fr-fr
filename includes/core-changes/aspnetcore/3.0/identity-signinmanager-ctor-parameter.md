---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032564"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="cc2c7-101">Identité : le constructeur SignInManager accepte le nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="cc2c7-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="cc2c7-102">À compter de ASP.NET Core 3,0, un nouveau `IUserConfirmation<TUser>` paramètre a été ajouté au `SignInManager` constructeur.</span><span class="sxs-lookup"><span data-stu-id="cc2c7-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="cc2c7-103">Pour plus d’informations, consultez [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="cc2c7-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cc2c7-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cc2c7-104">Version introduced</span></span>

<span data-ttu-id="cc2c7-105">3.0</span><span class="sxs-lookup"><span data-stu-id="cc2c7-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cc2c7-106">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="cc2c7-106">Reason for change</span></span>

<span data-ttu-id="cc2c7-107">La motivation de la modification consistait à ajouter la prise en charge de nouveaux flux de courrier électronique/confirmation dans l’identité.</span><span class="sxs-lookup"><span data-stu-id="cc2c7-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cc2c7-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cc2c7-108">Recommended action</span></span>

<span data-ttu-id="cc2c7-109">Si vous construisez manuellement un `SignInManager` , fournissez une implémentation de `IUserConfirmation` ou récupérez-en un à partir de l’injection de dépendances pour fournir.</span><span class="sxs-lookup"><span data-stu-id="cc2c7-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="cc2c7-110">Category</span><span class="sxs-lookup"><span data-stu-id="cc2c7-110">Category</span></span>

<span data-ttu-id="cc2c7-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cc2c7-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cc2c7-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="cc2c7-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
