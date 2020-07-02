---
ms.openlocfilehash: e92cbb7decb5e530bbf611cec26ce03a05e06eb3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622240"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng et DSACng sont à nouveau utilisables dans les scénarios de confiance partielle

#### <a name="details"></a>Détails

CngLightup (utilisé dans plusieurs API de chiffrement de niveau supérieur, telles que <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) et <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> dans certains cas s’appuient sur la confiance totale. Ces éléments comprennent P/Invokes sans l’assertion d’autorisations <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> et des chemins de code où <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> a des demandes d’autorisation pour <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>. À compter de .NET Framework 4.6.2, CngLightup a été utilisé pour basculer vers <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> autant que possible. Par conséquent, les applications de confiance partielle qui utilisaient correctement <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ont commencé à échouer et à lever des exceptions <xref:System.Security.SecurityException>. Cette modification ajoute les assertions nécessaires afin que toutes les fonctions utilisant CngLightup disposent des autorisations requises.

#### <a name="suggestion"></a>Suggestion

Si cette modification dans .NET Framework 4.6.2 a eu un impact négatif sur vos applications de confiance partielle, effectuez la mise à niveau vers .NET Framework 4.7.1.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
