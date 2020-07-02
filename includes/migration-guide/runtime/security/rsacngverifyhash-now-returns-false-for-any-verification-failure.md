---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621081"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="69fe4-101">RSACng.VerifyHash retourne maintenant la valeur False pour tout échec de vérification</span><span class="sxs-lookup"><span data-stu-id="69fe4-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="69fe4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="69fe4-102">Details</span></span>

<span data-ttu-id="69fe4-103">À compter de .NET Framework 4.6.2, cette méthode retourne **False** si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="69fe4-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="69fe4-104">Elle retourne maintenant False pour tout échec de vérification. Dans .NET Framework 4.6 et 4.6.1, la méthode lève une <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="69fe4-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="69fe4-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="69fe4-105">Suggestion</span></span>

<span data-ttu-id="69fe4-106">Tout code dont l’exécution dépend de la gestion de <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> doit s’exécuter à la place si la validation échoue et que la méthode retourne **False**.</span><span class="sxs-lookup"><span data-stu-id="69fe4-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="69fe4-107">Nom</span><span class="sxs-lookup"><span data-stu-id="69fe4-107">Name</span></span>    | <span data-ttu-id="69fe4-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="69fe4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="69fe4-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="69fe4-109">Scope</span></span>   |<span data-ttu-id="69fe4-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="69fe4-110">Minor</span></span>|
|<span data-ttu-id="69fe4-111">Version</span><span class="sxs-lookup"><span data-stu-id="69fe4-111">Version</span></span>|<span data-ttu-id="69fe4-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="69fe4-112">4.6.2</span></span>|
|<span data-ttu-id="69fe4-113">Type</span><span class="sxs-lookup"><span data-stu-id="69fe4-113">Type</span></span>|<span data-ttu-id="69fe4-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="69fe4-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="69fe4-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="69fe4-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
