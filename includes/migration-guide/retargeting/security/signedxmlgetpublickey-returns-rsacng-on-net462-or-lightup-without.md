---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858943"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey retourne RSACng sur net462 (ou lightup) sans changement de reciblage

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6.2, le type concret de l’objet retourné par la méthode <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> est passé (sans coïncidence) d’une implémentation CryptoServiceProvider à une implémentation Cng. La raison en est que l’implémentation est passée de l’utilisation de <code>certificate.PublicKey.Key</code> à l’utilisation du <code>certificate.GetAnyPublicKey</code> interne qu’elle transfère à <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Suggestion|À partir des applications qui s’exécutent sur .NET Framework 4.7.1, vous pouvez utiliser l’implémentation CryptoServiceProvider utilisée par défaut dans .NET Framework 4.6.1 et les versions antérieures en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
