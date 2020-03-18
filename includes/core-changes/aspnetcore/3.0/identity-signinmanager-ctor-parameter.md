---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901914"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="89425-101">Identité: SignInManager constructeur accepte un nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="89425-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="89425-102">En commençant par ASP.NET Core 3.0, un `IUserConfirmation<TUser>` nouveau `SignInManager` paramètre a été ajouté au constructeur.</span><span class="sxs-lookup"><span data-stu-id="89425-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="89425-103">Pour plus d’informations, voir [dotnet/aspnetcore 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="89425-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="89425-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="89425-104">Version introduced</span></span>

<span data-ttu-id="89425-105">3.0</span><span class="sxs-lookup"><span data-stu-id="89425-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="89425-106">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="89425-106">Reason for change</span></span>

<span data-ttu-id="89425-107">La motivation pour le changement était d’ajouter un soutien pour les nouveaux flux de messagerie / confirmation dans l’identité.</span><span class="sxs-lookup"><span data-stu-id="89425-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="89425-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="89425-108">Recommended action</span></span>

<span data-ttu-id="89425-109">Si la construction `SignInManager`manuelle d’un, fournir une mise en œuvre ou `IUserConfirmation` saisir un de l’injection de dépendance à fournir.</span><span class="sxs-lookup"><span data-stu-id="89425-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="89425-110">Category</span><span class="sxs-lookup"><span data-stu-id="89425-110">Category</span></span>

<span data-ttu-id="89425-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89425-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="89425-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="89425-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
