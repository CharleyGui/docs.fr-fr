---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615705"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="3df3d-101">L’appel de CreateDefaultAuthorizationContext avec un argument Null a été modifié</span><span class="sxs-lookup"><span data-stu-id="3df3d-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="3df3d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3df3d-102">Details</span></span>

<span data-ttu-id="3df3d-103">L’implémentation de la valeur <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> retournée par un appel à <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> avec un argument authorizationPolicies null est maintenant différente dans .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="3df3d-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3df3d-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3df3d-104">Suggestion</span></span>

<span data-ttu-id="3df3d-105">Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement.</span><span class="sxs-lookup"><span data-stu-id="3df3d-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="3df3d-106">Dans ce cas, vous pouvez restaurer l’ancien comportement de deux manières :</span><span class="sxs-lookup"><span data-stu-id="3df3d-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="3df3d-107">Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6.</span><span class="sxs-lookup"><span data-stu-id="3df3d-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="3df3d-108">Pour les services hébergés dans IIS, utilisez l'élément `<httpRuntime targetFramework="x.x">` pour cibler une version antérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3df3d-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="3df3d-109">Ajoutez la ligne suivante à la section `<appSettings>` de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="3df3d-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="3df3d-110">Nom</span><span class="sxs-lookup"><span data-stu-id="3df3d-110">Name</span></span>    | <span data-ttu-id="3df3d-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="3df3d-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3df3d-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="3df3d-112">Scope</span></span>   | <span data-ttu-id="3df3d-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="3df3d-113">Minor</span></span>       |
| <span data-ttu-id="3df3d-114">Version</span><span class="sxs-lookup"><span data-stu-id="3df3d-114">Version</span></span> | <span data-ttu-id="3df3d-115">4.6</span><span class="sxs-lookup"><span data-stu-id="3df3d-115">4.6</span></span>         |
| <span data-ttu-id="3df3d-116">Type</span><span class="sxs-lookup"><span data-stu-id="3df3d-116">Type</span></span>    | <span data-ttu-id="3df3d-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="3df3d-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3df3d-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="3df3d-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
