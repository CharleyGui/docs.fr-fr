---
ms.openlocfilehash: 242a9952cb47d170aceffa1aa392071eb40cc6ab
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857225"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng et DSACng sont à nouveau utilisables dans les scénarios de confiance partielle

|   |   |
|---|---|
|Détails|CngLightup (utilisé dans plusieurs API de chiffrement de niveau supérieur, telles que <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) et <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> dans certains cas s’appuient sur la confiance totale. Ces éléments comprennent P/Invokes sans l’assertion d’autorisations <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> et des chemins de code où <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> a des demandes d’autorisation pour <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>. À compter de .NET Framework 4.6.2, CngLightup a été utilisé pour basculer vers <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> autant que possible. Par conséquent, les applications de confiance partielle qui utilisaient correctement <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ont commencé à échouer et à lever des exceptions <xref:System.Security.SecurityException>. Cette modification ajoute les assertions nécessaires afin que toutes les fonctions utilisant CngLightup disposent des autorisations requises.|
|Suggestion|Si cette modification dans .NET Framework 4.6.2 a eu un impact négatif sur vos applications de confiance partielle, effectuez la mise à niveau vers .NET Framework 4.7.1.|
|Portée|Microsoft Edge|
|Version|4.6.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

