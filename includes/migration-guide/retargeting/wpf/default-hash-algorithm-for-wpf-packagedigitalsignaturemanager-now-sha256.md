---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614587"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="3af28-101">L’algorithme de hachage par défaut pour WPF PackageDigitalSignatureManager est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="3af28-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="3af28-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3af28-102">Details</span></span>

<span data-ttu-id="3af28-103">`System.IO.Packaging.PackageDigitalSignatureManager` fournit des fonctionnalités pour les signatures numériques en relation avec les packages WPF.</span><span class="sxs-lookup"><span data-stu-id="3af28-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="3af28-104">Dans le .NET Framework 4.7 et versions antérieures, l’algorithme par défaut (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) utilisé pour la signature des parties d’un package était SHA1.</span><span class="sxs-lookup"><span data-stu-id="3af28-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="3af28-105">En raison des récents problèmes de sécurité avec SHA1, cette valeur par défaut est remplacée par SHA256 à compter du .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3af28-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="3af28-106">Ce changement affecte toutes les signatures de package, notamment les documents XPS.</span><span class="sxs-lookup"><span data-stu-id="3af28-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3af28-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3af28-107">Suggestion</span></span>

<span data-ttu-id="3af28-108">Un développeur qui souhaite utiliser ce changement tout en ciblant une version antérieure à .NET Framework 4.7.1 ou un développeur qui nécessite les fonctionnalités précédentes tout en ciblant .NET Framework 4.7.1 ou ultérieur peut définir l’indicateur AppContext en conséquence.</span><span class="sxs-lookup"><span data-stu-id="3af28-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="3af28-109">La valeur true signifie que SHA1 est utilisé comme algorithme par défaut ; false entraîne l’utilisation de SHA256.</span><span class="sxs-lookup"><span data-stu-id="3af28-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3af28-110">Nom</span><span class="sxs-lookup"><span data-stu-id="3af28-110">Name</span></span>    | <span data-ttu-id="3af28-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="3af28-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3af28-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="3af28-112">Scope</span></span>   | <span data-ttu-id="3af28-113">Edge</span><span class="sxs-lookup"><span data-stu-id="3af28-113">Edge</span></span>        |
| <span data-ttu-id="3af28-114">Version</span><span class="sxs-lookup"><span data-stu-id="3af28-114">Version</span></span> | <span data-ttu-id="3af28-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3af28-115">4.7.1</span></span>       |
| <span data-ttu-id="3af28-116">Type</span><span class="sxs-lookup"><span data-stu-id="3af28-116">Type</span></span>    | <span data-ttu-id="3af28-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="3af28-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3af28-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="3af28-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
