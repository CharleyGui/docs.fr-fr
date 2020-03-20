---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887764"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="dd560-101">RSACng.VerifyHash retourne maintenant la valeur False pour tout échec de vérification</span><span class="sxs-lookup"><span data-stu-id="dd560-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dd560-102">Détails</span><span class="sxs-lookup"><span data-stu-id="dd560-102">Details</span></span>|<span data-ttu-id="dd560-103">À compter de .NET Framework 4.6.2, cette méthode retourne **False** si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="dd560-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="dd560-104">Elle retourne maintenant False pour tout échec de vérification. Dans .NET Framework 4.6 et 4.6.1, la méthode lève une <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="dd560-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="dd560-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="dd560-105">Suggestion</span></span>|<span data-ttu-id="dd560-106">Tout code dont l’exécution dépend de la gestion de <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> doit s’exécuter à la place si la validation échoue et que la méthode retourne **False**.</span><span class="sxs-lookup"><span data-stu-id="dd560-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="dd560-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="dd560-107">Scope</span></span>|<span data-ttu-id="dd560-108">Secondaire</span><span class="sxs-lookup"><span data-stu-id="dd560-108">Minor</span></span>|
|<span data-ttu-id="dd560-109">Version</span><span class="sxs-lookup"><span data-stu-id="dd560-109">Version</span></span>|<span data-ttu-id="dd560-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="dd560-110">4.6.2</span></span>|
|<span data-ttu-id="dd560-111">Type</span><span class="sxs-lookup"><span data-stu-id="dd560-111">Type</span></span>|<span data-ttu-id="dd560-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="dd560-112">Runtime</span></span>|
|<span data-ttu-id="dd560-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="dd560-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
