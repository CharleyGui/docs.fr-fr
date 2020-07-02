---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616053"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey retourne RSACng sur net462 (ou lightup) sans changement de reciblage

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6.2, le type concret de l’objet retourné par la méthode <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> est passé (sans coïncidence) d’une implémentation CryptoServiceProvider à une implémentation Cng. La raison en est que l’implémentation est passée de l’utilisation de `certificate.PublicKey.Key` à l’utilisation du `certificate.GetAnyPublicKey` interne qu’elle transfère à <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.

#### <a name="suggestion"></a>Suggestion

À partir des applications qui s’exécutent sur .NET Framework 4.7.1, vous pouvez utiliser l’implémentation CryptoServiceProvider utilisée par défaut dans .NET Framework 4.6.1 et les versions antérieures en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
