---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857536"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>Modifications avec rupture pour SignedXml et EncryptedXml

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.2, les correctifs de sécurité dans <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> et <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> aboutissent à différents comportements au moment de l’exécution. Par exemple,<ul><li>Si un document contient plusieurs éléments avec le même attribut <code>id</code> et qu’une signature cible l’un de ces éléments comme racine de la signature, le document est désormais considéré comme non valide.</li><li>Les documents utilisant des algorithmes de transformation XPath non canoniques dans les références sont désormais considérés comme non valides.</li><li>Les documents utilisant des algorithmes de transformation XSLT non canoniques dans les références sont désormais considérés comme non valides.</li><li>N’importe quel programme tirant parti des signatures détachées des ressources externes ne pourra plus le faire.</li></ul>|
|Suggestion|Les développeurs peuvent examiner l’utilisation de <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> et <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, ainsi que les types dérivés de <xref:System.Security.Cryptography.Xml.Transform>, car un destinataire du document risque de ne pas pouvoir le traiter.|
|Étendue|Secondaire|
|Version|4.6.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
