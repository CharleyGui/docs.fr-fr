---
ms.openlocfilehash: e56d896f093d6cd28ed0d6640ba154e5d4593c6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496286"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>L’extension d’entité DTD de XmlTextReader est limitée à 10 000 000 caractères.

#### <a name="details"></a>Détails

L’extension d’entité DTD est désormais limitée à 10 000 000 caractères. Le chargement des fichiers XML sans extension d'entité DTD ou avec une extension d'entité DTD limitée reste inchangé. Les fichiers avec des entités DTD qui s'étendent à plus de 10 000 000 caractères ne se chargent pas et lèvent désormais une exception.

#### <a name="suggestion"></a>Suggestion

Si la limite de l’extension d’entité DTD n’est pas suffisante, la valeur peut être remplacée par la propriété <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities>. Un <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> avec la valeur <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> correcte peut être passé à <code>XmlReader.Create</code> qui prend <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (c’est-à-dire <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Xml.XmlTextReader?displayProperty=nameWithType>
- <xref:System.Xml.XmlTextReader.%23ctor>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)>
- <xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)>

<!--

#### Affected APIs

- `T:System.Xml.XmlTextReader`
- `M:System.Xml.XmlTextReader.#ctor`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNameTable)`
- `M:System.Xml.XmlTextReader.#ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)`
- `M:System.Xml.XmlTextReader.#ctor(System.Xml.XmlNameTable)`

-->
