---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859261"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>L’algorithme RSACng charge désormais correctement les clés RSA de taille de clé non standard

|   |   |
|---|---|
|Détails|Dans les versions .NET Framework antérieures à la version 4.6.2, les clients avec des tailles de clé non standard pour les certificats RSA ne peuvent pas accéder à ces clés via les méthodes d’extension <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> et <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name>.  Une exception <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> est levée avec un message indiquant que &quot;la taille de clé demandée n’est pas prise en charge&quot;. Dans .NET Framework 4.6.2, ce problème a été résolu. De même, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> et <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> fonctionnent désormais avec des tailles de clé non standard sans lever d’exception <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Suggestion|S’il existe une logique de gestion des exceptions qui s’appuie sur le comportement précédent où un <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> est levé quand des tailles de clé non standard sont utilisées, supprimez la logique.|
|Étendue|Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
