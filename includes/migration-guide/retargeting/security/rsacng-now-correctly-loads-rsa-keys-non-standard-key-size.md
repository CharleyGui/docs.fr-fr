---
ms.openlocfilehash: 6d9f4b630e95d9a63393da3ae0ecd83c2b994712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859261"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng charge désormais correctement les clés RSA de taille de clé non standard

|   |   |
|---|---|
|Détails|Dans les versions du .NET Framework antérieures à 4.6.2, les clients avec des tailles de clé non standard pour les certificats RSA ne peuvent pas accéder à ces clés par le biais des méthodes d’extension <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> et <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name>.  Une exception <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> est levée avec un message indiquant que &quot;la taille de clé demandée n’est pas prise en charge&quot;. Dans .NET Framework 4.6.2, ce problème a été résolu. De même, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> et <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> fonctionnent désormais avec des tailles de clé non standard sans lever d’exception <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Suggestion|S’il existe une logique de gestion des exceptions qui s’appuie sur le comportement précédent où un <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> est levé quand des tailles de clé non standard sont utilisées, supprimez la logique.|
|Portée|Microsoft Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|

