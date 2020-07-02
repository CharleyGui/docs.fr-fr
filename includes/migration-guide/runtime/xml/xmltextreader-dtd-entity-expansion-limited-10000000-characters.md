---
ms.openlocfilehash: fdec6671cbf2dae0d72dfaec07f162058b38cf9d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620512"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>L’extension d’entité DTD de XmlTextReader est limitée à 10 000 000 caractères.

#### <a name="details"></a>Détails

L’extension d’entité DTD est désormais limitée à 10 000 000 caractères. Le chargement des fichiers XML sans extension d'entité DTD ou avec une extension d'entité DTD limitée reste inchangé. Les fichiers avec des entités DTD qui s'étendent à plus de 10 000 000 caractères ne se chargent pas et lèvent désormais une exception.

#### <a name="suggestion"></a>Suggestion

Si la limite de l’extension d’entité DTD n’est pas suffisante, la valeur peut être remplacée par la propriété <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities>. Un <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> avec la valeur <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> correcte peut être passé à <code>XmlReader.Create</code> qui prend <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (c’est-à-dire <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)></li></ul>|
