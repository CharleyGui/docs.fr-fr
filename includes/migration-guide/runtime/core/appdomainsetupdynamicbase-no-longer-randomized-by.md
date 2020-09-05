---
ms.openlocfilehash: 26c50ac8b0e570e31a38b1913f73acbe21fae08b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497059"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="503e6-101">AppDomainSetup.DynamicBase n’est plus aléatoire en activant UseRandomizedStringHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="503e6-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="503e6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="503e6-102">Details</span></span>

<span data-ttu-id="503e6-103">Avant .NET Framework 4.6, la valeur de <xref:System.AppDomainSetup.DynamicBase> était aléatoire entre les domaines d’application, ou entre les processus, si UseRandomizedStringHashAlgorithm était activé dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="503e6-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="503e6-104">À compter de .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retourne un résultat stable entre différentes instances d’une application en cours d’exécution et entre différents domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="503e6-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="503e6-105">Les bases dynamiques seront toujours différentes pour différentes applications ; cette modification supprime uniquement l’élément de nommage aléatoire pour différentes instances de la même application.</span><span class="sxs-lookup"><span data-stu-id="503e6-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="503e6-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="503e6-106">Suggestion</span></span>

<span data-ttu-id="503e6-107">Gardez à l’esprit que l’activation de <code>UseRandomizedStringHashAlgorithm</code> ne rendra pas <xref:System.AppDomainSetup.DynamicBase> aléatoire.</span><span class="sxs-lookup"><span data-stu-id="503e6-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="503e6-108">Si une base aléatoire est nécessaire, elle doit être générée dans le code de votre application plutôt que via cette API.</span><span class="sxs-lookup"><span data-stu-id="503e6-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="503e6-109">Name</span><span class="sxs-lookup"><span data-stu-id="503e6-109">Name</span></span>    | <span data-ttu-id="503e6-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="503e6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="503e6-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="503e6-111">Scope</span></span>   |<span data-ttu-id="503e6-112">Edge</span><span class="sxs-lookup"><span data-stu-id="503e6-112">Edge</span></span>|
|<span data-ttu-id="503e6-113">Version</span><span class="sxs-lookup"><span data-stu-id="503e6-113">Version</span></span>|<span data-ttu-id="503e6-114">4,6</span><span class="sxs-lookup"><span data-stu-id="503e6-114">4.6</span></span>|
|<span data-ttu-id="503e6-115">Type</span><span class="sxs-lookup"><span data-stu-id="503e6-115">Type</span></span>|<span data-ttu-id="503e6-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="503e6-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="503e6-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="503e6-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.DynamicBase`

-->
