---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393978"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="729c2-101">Autorisation : surcharge AddAuthorization déplacée vers un assembly différent</span><span class="sxs-lookup"><span data-stu-id="729c2-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="729c2-102">Les méthodes principales `AddAuthorization` qui se trouvent dans `Microsoft.AspNetCore.Authorization` ont été renommées en `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="729c2-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="729c2-103">Les anciennes méthodes `AddAuthorization` existent toujours, mais elles se trouvent dans le package `Microsoft.AspNetCore.Authorization.Policy` à la place.</span><span class="sxs-lookup"><span data-stu-id="729c2-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` package instead.</span></span> <span data-ttu-id="729c2-104">Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact.</span><span class="sxs-lookup"><span data-stu-id="729c2-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="729c2-105">Les applications qui n’utilisent pas le package de stratégie doivent passer à l’utilisation de `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="729c2-105">Apps that weren't using the policy package must switch to using `AddAuthorizationCore`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="729c2-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="729c2-106">Version introduced</span></span>

<span data-ttu-id="729c2-107">3,0</span><span class="sxs-lookup"><span data-stu-id="729c2-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="729c2-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="729c2-108">Old behavior</span></span>

<span data-ttu-id="729c2-109">les méthodes `AddAuthorization` existaient dans `Microsoft.AspNetCore.Authorization`.</span><span class="sxs-lookup"><span data-stu-id="729c2-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="729c2-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="729c2-110">New behavior</span></span>

<span data-ttu-id="729c2-111">les méthodes `AddAuthorization` existent dans `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="729c2-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="729c2-112">`AddAuthorizationCore` est le nouveau nom des anciennes méthodes.</span><span class="sxs-lookup"><span data-stu-id="729c2-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="729c2-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="729c2-113">Reason for change</span></span>

<span data-ttu-id="729c2-114">`AddAuthorization` est un meilleur nom de méthode pour l’ajout de tous les services communs nécessaires à l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="729c2-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="729c2-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="729c2-115">Recommended action</span></span>

<span data-ttu-id="729c2-116">Ajoutez une référence à `Microsoft.AspNetCore.Authorization.Policy` ou utilisez `AddAuthorizationCore` à la place.</span><span class="sxs-lookup"><span data-stu-id="729c2-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="729c2-117">Category</span><span class="sxs-lookup"><span data-stu-id="729c2-117">Category</span></span>

<span data-ttu-id="729c2-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="729c2-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="729c2-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="729c2-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
