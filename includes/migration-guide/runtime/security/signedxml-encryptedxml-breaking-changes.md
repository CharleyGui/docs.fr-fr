---
ms.openlocfilehash: 5c8ea3565fbe599dd53a71ba8bd339704f7d7f8a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497345"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>Modifications avec rupture pour SignedXml et EncryptedXml

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2, les correctifs de sécurité dans <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> et <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> aboutissent à différents comportements au moment de l’exécution. Par exemple,<ul><li>Si un document contient plusieurs éléments avec le même attribut <code>id</code> et qu’une signature cible l’un de ces éléments comme racine de la signature, le document est désormais considéré comme non valide.</li><li>Les documents utilisant des algorithmes de transformation XPath non canoniques dans les références sont désormais considérés comme non valides.</li><li>Les documents utilisant des algorithmes de transformation XSLT non canoniques dans les références sont désormais considérés comme non valides.</li><li>N’importe quel programme tirant parti des signatures détachées des ressources externes ne pourra plus le faire.</li></ul>

#### <a name="suggestion"></a>Suggestion

Les développeurs peuvent examiner l’utilisation de <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> et <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, ainsi que les types dérivés de <xref:System.Security.Cryptography.Xml.Transform>, car un destinataire du document risque de ne pas pouvoir le traiter.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.Xml.Transform`
- `T:System.Security.Cryptography.Xml.XmlDsigXPathTransform`
- `T:System.Security.Cryptography.Xml.XmlDsigXsltTransform`

-->
