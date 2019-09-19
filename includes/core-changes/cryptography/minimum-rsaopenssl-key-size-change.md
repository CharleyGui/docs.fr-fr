---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117167"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>La taille minimale de la génération de la clé de RSAOpenSsl a augmenté

La taille minimale de la génération de nouvelles clés RSA sur Linux est passée de 384 bits à 512 bits.

#### <a name="change-description"></a>Modifier la description

À compter de .net Core 3,0, la taille de clé légale minimale indiquée `LegalKeySizes` par la propriété sur les instances RSA de < System. Security. Cryptography. RSA. Create% 2A ? displayProperty = nameWithType >, < System. Security. Cryptography. RSAOpenSsl.% 23ctor% 2A ? displayProperty = nameWithType > et < System. Security. Cryptography. RSACryptoServicePlatform.% 23ctor% 2A ? displayProperty = nameWithType > sur Linux a augmenté de 384 à 512.

Par conséquent, dans .net Core 2,2 et les versions antérieures, un appel de méthode tel `RSA.Create(384)` que aboutit. Dans .net Core 3,0 et versions ultérieures, l’appel `RSA.Create(384)` de méthode lève une exception indiquant que la taille est trop petite.

Cette modification a été apportée car OpenSSL, qui effectue les opérations de chiffrement sur Linux, a augmenté son minimum entre les versions 1.0.2 et 1.1.0.  .NET Core 3,0 préfère OpenSSL 1.1. x à 1.0. x, et la version signalée minimale a été augmentée pour refléter cette nouvelle limite de dépendance supérieure.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Si vous appelez l’une des API affectées, assurez-vous que la taille de toutes les clés générées n’est pas inférieure à la valeur minimale du fournisseur.

> [!NOTE]
> RSA 384 bits est déjà considéré comme non sécurisé (comme c’est le cas de la RSA 512 bits). Des recommandations modernes, telles que la [publication spéciale NIST 800-57 partie 1 révision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggèrent 2048 bits comme taille minimale pour les clés nouvellement générées.

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`


-->
