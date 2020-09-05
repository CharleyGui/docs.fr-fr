---
ms.openlocfilehash: b7b16e39fa5df9732fa769f2bcd3696dff3b2a49
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497331"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="c49c7-101">RSACng.VerifyHash retourne maintenant la valeur False pour tout échec de vérification</span><span class="sxs-lookup"><span data-stu-id="c49c7-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="c49c7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c49c7-102">Details</span></span>

<span data-ttu-id="c49c7-103">À compter de .NET Framework 4.6.2, cette méthode retourne **False** si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="c49c7-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="c49c7-104">Elle retourne maintenant False pour tout échec de vérification. Dans .NET Framework 4.6 et 4.6.1, la méthode lève une <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="c49c7-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c49c7-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c49c7-105">Suggestion</span></span>

<span data-ttu-id="c49c7-106">Tout code dont l’exécution dépend de la gestion de <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> doit s’exécuter à la place si la validation échoue et que la méthode retourne **False**.</span><span class="sxs-lookup"><span data-stu-id="c49c7-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="c49c7-107">Name</span><span class="sxs-lookup"><span data-stu-id="c49c7-107">Name</span></span>    | <span data-ttu-id="c49c7-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="c49c7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c49c7-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="c49c7-109">Scope</span></span>   |<span data-ttu-id="c49c7-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="c49c7-110">Minor</span></span>|
|<span data-ttu-id="c49c7-111">Version</span><span class="sxs-lookup"><span data-stu-id="c49c7-111">Version</span></span>|<span data-ttu-id="c49c7-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c49c7-112">4.6.2</span></span>|
|<span data-ttu-id="c49c7-113">Type</span><span class="sxs-lookup"><span data-stu-id="c49c7-113">Type</span></span>|<span data-ttu-id="c49c7-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="c49c7-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c49c7-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="c49c7-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
