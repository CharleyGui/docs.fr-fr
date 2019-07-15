---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857530"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="82b4d-101">RSACng.VerifyHash retourne maintenant la valeur False pour tout échec de vérification</span><span class="sxs-lookup"><span data-stu-id="82b4d-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="82b4d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="82b4d-102">Details</span></span>|<span data-ttu-id="82b4d-103">À compter de .NET Framework 4.6.2, cette méthode retourne <strong>False</strong> si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="82b4d-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="82b4d-104">Elle retourne maintenant False pour tout échec de vérification. Dans .NET Framework 4.6 et 4.6.1, la méthode lève une <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> si le format de la signature proprement dite n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="82b4d-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="82b4d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="82b4d-105">Suggestion</span></span>|<span data-ttu-id="82b4d-106">Tout code dont l’exécution dépend de la gestion de <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> doit s’exécuter à la place si la validation échoue et que la méthode retourne <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="82b4d-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="82b4d-107">Portée</span><span class="sxs-lookup"><span data-stu-id="82b4d-107">Scope</span></span>|<span data-ttu-id="82b4d-108">Mineur</span><span class="sxs-lookup"><span data-stu-id="82b4d-108">Minor</span></span>|
|<span data-ttu-id="82b4d-109">Version</span><span class="sxs-lookup"><span data-stu-id="82b4d-109">Version</span></span>|<span data-ttu-id="82b4d-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="82b4d-110">4.6.2</span></span>|
|<span data-ttu-id="82b4d-111">Type</span><span class="sxs-lookup"><span data-stu-id="82b4d-111">Type</span></span>|<span data-ttu-id="82b4d-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="82b4d-112">Runtime</span></span>|
|<span data-ttu-id="82b4d-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="82b4d-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

