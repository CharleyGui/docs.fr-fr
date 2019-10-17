---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394087"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="4a513-101">Identité : le constructeur SignInManager accepte le nouveau paramètre</span><span class="sxs-lookup"><span data-stu-id="4a513-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="4a513-102">À compter de ASP.NET Core 3,0, un nouveau paramètre `IUserConfirmation<TUser>` a été ajouté au constructeur `SignInManager`.</span><span class="sxs-lookup"><span data-stu-id="4a513-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="4a513-103">Pour plus d’informations, consultez [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="4a513-103">For more information, see [aspnet/AspNetCore#8356](https://github.com/aspnet/AspNetCore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a513-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4a513-104">Version introduced</span></span>

<span data-ttu-id="4a513-105">3,0</span><span class="sxs-lookup"><span data-stu-id="4a513-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4a513-106">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="4a513-106">Reason for change</span></span>

<span data-ttu-id="4a513-107">La motivation de la modification consistait à ajouter la prise en charge de nouveaux flux de courrier électronique/confirmation dans l’identité.</span><span class="sxs-lookup"><span data-stu-id="4a513-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a513-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4a513-108">Recommended action</span></span>

<span data-ttu-id="4a513-109">Si vous construisez manuellement un `SignInManager`, fournissez une implémentation de `IUserConfirmation` ou récupérez-en une à partir de l’injection de dépendances à fournir.</span><span class="sxs-lookup"><span data-stu-id="4a513-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="4a513-110">Category</span><span class="sxs-lookup"><span data-stu-id="4a513-110">Category</span></span>

<span data-ttu-id="4a513-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a513-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a513-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="4a513-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
