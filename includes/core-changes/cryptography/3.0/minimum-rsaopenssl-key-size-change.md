---
ms.openlocfilehash: 3d94023fc508a56304587121c6cf1444c87b0d52
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721499"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>La taille minimale de la génération de la clé de RSAOpenSsl a augmenté

La taille minimale de la génération de nouvelles clés RSA sur Linux est passée de 384 bits à 512 bits.

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0, la taille de clé légale minimale indiquée par la `LegalKeySizes` propriété sur les instances RSA de <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> , <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A> et <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> sur Linux est passée de 384 à 512.

Par conséquent, dans .NET Core 2,2 et les versions antérieures, un appel de méthode tel que `RSA.Create(384)` aboutit. Dans .NET Core 3,0 et versions ultérieures, l’appel de méthode `RSA.Create(384)` lève une exception indiquant que la taille est trop petite.

Cette modification a été apportée car OpenSSL, qui effectue les opérations de chiffrement sur Linux, a augmenté son minimum entre les versions 1.0.2 et 1.1.0. .NET Core 3,0 préfère OpenSSL 1.1. x à 1.0. x, et la version signalée minimale a été augmentée pour refléter cette nouvelle limite de dépendance supérieure.

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
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
#### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
