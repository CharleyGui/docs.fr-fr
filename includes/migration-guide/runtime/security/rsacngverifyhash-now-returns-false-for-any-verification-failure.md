---
ms.openlocfilehash: b7b16e39fa5df9732fa769f2bcd3696dff3b2a49
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497331"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash retourne maintenant la valeur False pour tout échec de vérification

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6.2, cette méthode retourne **False** si le format de la signature proprement dite n’est pas correct. Elle retourne maintenant False pour tout échec de vérification. Dans .NET Framework 4.6 et 4.6.1, la méthode lève une <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> si le format de la signature proprement dite n’est pas correct.

#### <a name="suggestion"></a>Suggestion

Tout code dont l’exécution dépend de la gestion de <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> doit s’exécuter à la place si la validation échoue et que la méthode retourne **False**.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
