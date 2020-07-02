---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614438"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>L’algorithme RSACng charge désormais correctement les clés RSA de taille de clé non standard

#### <a name="details"></a>Détails

Dans les versions .NET Framework antérieures à la version 4.6.2, les clients avec des tailles de clé non standard pour les certificats RSA ne peuvent pas accéder à ces clés via les méthodes d’extension <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> et <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName>.  Une exception <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> est levée avec un message indiquant que &quot;la taille de clé demandée n’est pas prise en charge&quot;. Dans .NET Framework 4.6.2, ce problème a été résolu. De même, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> et <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> fonctionnent désormais avec des tailles de clé non standard sans lever d’exception <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

S’il existe une logique de gestion des exceptions qui s’appuie sur le comportement précédent où un <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> est levé quand des tailles de clé non standard sont utilisées, supprimez la logique.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
