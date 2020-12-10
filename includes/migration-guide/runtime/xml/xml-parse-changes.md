---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009049"
---
### <a name="xml-parsing-changes"></a>Modifications de l’analyse XML

| Name    | Valeur   |
|:--------|:--------|
| Étendue   | Secondaire   |
| Version | 4.5.2   |
| Type    | Runtime |

#### <a name="details"></a>Détails

Pour des raisons de sécurité, les modifications suivantes ont été introduites dans les API d’analyse XML :

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> a la valeur 10 millions lorsque <xref:System.Xml.XmlReaderSettings> est initialisé.
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> a la valeur `null` par défaut.

> [!NOTE]
> <xref:System.Xml.XmlReaderSettings> est utilisé par tous les analyseurs XML. ainsi, bien que cette modification aide le <xref:System.Xml.XmlReader> cas, elle affecte également d’autres scénarios.

#### <a name="suggestion"></a>Suggestion

Pour rétablir le comportement précédent, vous pouvez définir une valeur dans le registre. Ajoutez une valeur DWORD nommée `EnableLegacyXmlSettings` à la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` clé de Registre et affectez-lui la valeur `1` . Vous pouvez également ajouter la valeur de Registre dans la ruche HKEY_CURRENT_USER à la place.

#### <a name="affected-apis"></a>API affectées

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

En outre, toute API XML qui dépend de <xref:System.Xml.XmlResolver> , directement ou indirectement, est affectée.

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
