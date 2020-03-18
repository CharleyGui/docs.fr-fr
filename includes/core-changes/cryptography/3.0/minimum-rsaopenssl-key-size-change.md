---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567961"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>La taille minimale de la génération clé RSAOpenSsl a augmenté

La taille minimale pour générer de nouvelles touches RSA sur Linux est passée de 384 bits à 512 bits.

#### <a name="change-description"></a>Description de la modification

À partir de .NET Core 3.0, la `LegalKeySizes` taille minimale <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>de <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>clé <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> légale déclarée par la propriété sur les instances RSA de , , et sur Linux a augmenté de 384 à 512.

En conséquence, dans .NET Core 2.2 et les versions antérieures, un appel de méthode tel que `RSA.Create(384)` réussit. Dans .NET Core 3.0 et les `RSA.Create(384)` versions ultérieures, l’appel de méthode jette une exception indiquant que la taille est trop petite.

Ce changement a été apporté parce qu’OpenSSL, qui effectue les opérations cryptographiques sur Linux, a augmenté son minimum entre les versions 1.0.2 et 1.1.0. .NET Core 3.0 préfère OpenSSL 1.1.x à 1.0.x, et la version minimale déclarée a été soulevée pour refléter cette nouvelle limitation de dépendance plus élevée.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Si vous appelez l’une des API affectées, assurez-vous que la taille des clés générées n’est pas inférieure au minimum du fournisseur.

> [!NOTE]
> Le RSA 384 bits est déjà considéré comme peu sûr (tout comme le RSA 512 bits). Les recommandations modernes, telles que [NIST Special Publication 800-57 Partie 1 Révision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggèrent 2048-bit comme la taille minimale pour les clés nouvellement générées.

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
