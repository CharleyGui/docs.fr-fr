---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100937"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="31594-101">Autorisation : surcharge AddAuthorization déplacée vers un assembly différent</span><span class="sxs-lookup"><span data-stu-id="31594-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="31594-102">Les méthodes `AddAuthorization` principales qui utilisaient pour résider `Microsoft.AspNetCore.Authorization` dans ont été renommées en `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="31594-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="31594-103">Les anciennes `AddAuthorization` méthodes existent toujours, mais elles se trouvent `Microsoft.AspNetCore.Authorization.Policy` dans l’assembly à la place.</span><span class="sxs-lookup"><span data-stu-id="31594-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="31594-104">Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact.</span><span class="sxs-lookup"><span data-stu-id="31594-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="31594-105">Notez que `Microsoft.AspNetCore.Authorization.Policy` est désormais fourni dans le Framework partagé au lieu d’un package autonome, comme indiqué dans [Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="31594-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="31594-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="31594-106">Version introduced</span></span>

<span data-ttu-id="31594-107">3.0</span><span class="sxs-lookup"><span data-stu-id="31594-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="31594-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="31594-108">Old behavior</span></span>
<span data-ttu-id="31594-109">`AddAuthorization`les méthodes existaient `Microsoft.AspNetCore.Authorization`dans.</span><span class="sxs-lookup"><span data-stu-id="31594-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="31594-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="31594-110">New behavior</span></span>

<span data-ttu-id="31594-111">`AddAuthorization`les méthodes existent `Microsoft.AspNetCore.Authorization.Policy`dans.</span><span class="sxs-lookup"><span data-stu-id="31594-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="31594-112">`AddAuthorizationCore`nouveau nom pour les anciennes méthodes.</span><span class="sxs-lookup"><span data-stu-id="31594-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="31594-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="31594-113">Reason for change</span></span>

<span data-ttu-id="31594-114">`AddAuthorization`est un meilleur nom de méthode pour l’ajout de tous les services communs nécessaires à l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="31594-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="31594-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="31594-115">Recommended action</span></span>

<span data-ttu-id="31594-116">Ajoutez une référence à ou `Microsoft.AspNetCore.Authorization.Policy` utilisez `AddAuthorizationCore` à la place.</span><span class="sxs-lookup"><span data-stu-id="31594-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="31594-117">Category</span><span class="sxs-lookup"><span data-stu-id="31594-117">Category</span></span>

<span data-ttu-id="31594-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="31594-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31594-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="31594-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
