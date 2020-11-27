---
ms.openlocfilehash: 2819fb3857fa6d40a2b2e42eeaec2d9c6e50eef0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96299351"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="22fc7-101">Autorisation : surcharge AddAuthorization déplacée vers un assembly différent</span><span class="sxs-lookup"><span data-stu-id="22fc7-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="22fc7-102">Les `AddAuthorization` méthodes principales qui utilisaient pour résider dans `Microsoft.AspNetCore.Authorization` ont été renommées en `AddAuthorizationCore` .</span><span class="sxs-lookup"><span data-stu-id="22fc7-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="22fc7-103">Les anciennes `AddAuthorization` méthodes existent toujours, mais elles se trouvent dans l' `Microsoft.AspNetCore.Authorization.Policy` assembly à la place.</span><span class="sxs-lookup"><span data-stu-id="22fc7-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="22fc7-104">Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact.</span><span class="sxs-lookup"><span data-stu-id="22fc7-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="22fc7-105">Notez que est `Microsoft.AspNetCore.Authorization.Policy` désormais fourni dans le Framework partagé au lieu d’un package autonome, comme indiqué dans [Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="22fc7-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22fc7-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="22fc7-106">Version introduced</span></span>

<span data-ttu-id="22fc7-107">3.0</span><span class="sxs-lookup"><span data-stu-id="22fc7-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="22fc7-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="22fc7-108">Old behavior</span></span>

<span data-ttu-id="22fc7-109">`AddAuthorization` les méthodes existaient dans `Microsoft.AspNetCore.Authorization` .</span><span class="sxs-lookup"><span data-stu-id="22fc7-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="22fc7-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="22fc7-110">New behavior</span></span>

<span data-ttu-id="22fc7-111">`AddAuthorization` les méthodes existent dans `Microsoft.AspNetCore.Authorization.Policy` .</span><span class="sxs-lookup"><span data-stu-id="22fc7-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="22fc7-112">`AddAuthorizationCore` nouveau nom pour les anciennes méthodes.</span><span class="sxs-lookup"><span data-stu-id="22fc7-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="22fc7-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="22fc7-113">Reason for change</span></span>

<span data-ttu-id="22fc7-114">`AddAuthorization` est un meilleur nom de méthode pour l’ajout de tous les services communs nécessaires à l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="22fc7-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22fc7-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="22fc7-115">Recommended action</span></span>

<span data-ttu-id="22fc7-116">Ajoutez une référence à `Microsoft.AspNetCore.Authorization.Policy` ou utilisez à la `AddAuthorizationCore` place.</span><span class="sxs-lookup"><span data-stu-id="22fc7-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="22fc7-117">Catégorie</span><span class="sxs-lookup"><span data-stu-id="22fc7-117">Category</span></span>

<span data-ttu-id="22fc7-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22fc7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22fc7-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="22fc7-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
