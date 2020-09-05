---
ms.openlocfilehash: 4e685722271a8079e727ea9c2e0e501f68b30fc9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497581"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="56f57-101">Dans le domaine d’application par défaut, TargetFrameworkName ne prend plus la valeur Null par défaut quand il n’est pas défini</span><span class="sxs-lookup"><span data-stu-id="56f57-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="56f57-102">Détails</span><span class="sxs-lookup"><span data-stu-id="56f57-102">Details</span></span>

<span data-ttu-id="56f57-103">Avant, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> était défini sur la valeur Null dans le domaine d’application par défaut quand il n’était pas défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="56f57-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="56f57-104">À compter de la version 4.6, la valeur par défaut de la propriété <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> du domaine d’application par défaut est dérivée de TargetFrameworkAttribute (si celui-ci est présent).</span><span class="sxs-lookup"><span data-stu-id="56f57-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="56f57-105">Les domaines d’application autres que ceux par défaut continuent d’hériter leur valeur <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> du domaine d’application par défaut (qui n’aura pas la valeur Null par défaut dans la version 4.6), sauf si cette valeur est substituée explicitement.</span><span class="sxs-lookup"><span data-stu-id="56f57-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="56f57-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="56f57-106">Suggestion</span></span>

<span data-ttu-id="56f57-107">Le code doit être mis à jour pour ne pas attendre que <xref:System.AppDomainSetup.TargetFrameworkName> ait la valeur Null par défaut.</span><span class="sxs-lookup"><span data-stu-id="56f57-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="56f57-108">Si vous avez besoin que cette propriété continue de prendre la valeur Null, vous pouvez la définir explicitement sur cette valeur.</span><span class="sxs-lookup"><span data-stu-id="56f57-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="56f57-109">Name</span><span class="sxs-lookup"><span data-stu-id="56f57-109">Name</span></span>    | <span data-ttu-id="56f57-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="56f57-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="56f57-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="56f57-111">Scope</span></span>   |<span data-ttu-id="56f57-112">Edge</span><span class="sxs-lookup"><span data-stu-id="56f57-112">Edge</span></span>|
|<span data-ttu-id="56f57-113">Version</span><span class="sxs-lookup"><span data-stu-id="56f57-113">Version</span></span>|<span data-ttu-id="56f57-114">4,6</span><span class="sxs-lookup"><span data-stu-id="56f57-114">4.6</span></span>|
|<span data-ttu-id="56f57-115">Type</span><span class="sxs-lookup"><span data-stu-id="56f57-115">Type</span></span>|<span data-ttu-id="56f57-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="56f57-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="56f57-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="56f57-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.TargetFrameworkName`

-->
