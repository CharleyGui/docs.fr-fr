---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275311"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="d3c76-101">Identité: SignInManager constructeur accepte un nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="d3c76-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="d3c76-102">En commençant par ASP.NET Core 3.0, un `IUserConfirmation<TUser>` nouveau `SignInManager` paramètre a été ajouté au constructeur.</span><span class="sxs-lookup"><span data-stu-id="d3c76-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="d3c76-103">Pour plus d’informations, voir [dotnet/aspnetcore 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="d3c76-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3c76-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d3c76-104">Version introduced</span></span>

<span data-ttu-id="d3c76-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d3c76-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d3c76-106">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="d3c76-106">Reason for change</span></span>

<span data-ttu-id="d3c76-107">La motivation pour le changement était d’ajouter un soutien pour les nouveaux flux de messagerie / confirmation dans l’identité.</span><span class="sxs-lookup"><span data-stu-id="d3c76-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3c76-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d3c76-108">Recommended action</span></span>

<span data-ttu-id="d3c76-109">Si la construction `SignInManager`manuelle d’un, fournir une mise en œuvre ou `IUserConfirmation` saisir un de l’injection de dépendance à fournir.</span><span class="sxs-lookup"><span data-stu-id="d3c76-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="d3c76-110">Category</span><span class="sxs-lookup"><span data-stu-id="d3c76-110">Category</span></span>

<span data-ttu-id="d3c76-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d3c76-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3c76-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="d3c76-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
