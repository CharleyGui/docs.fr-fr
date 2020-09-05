---
ms.openlocfilehash: 75c7385bceec2595683d1c0d97a7df9264e3bf0b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496865"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a>XmlSerializer échoue lors de la sérialisation d’un type qui masque un membre accessible avec un membre inaccessible

#### <a name="details"></a>Détails

Lors de la sérialisation d’un type dérivé, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> peut échouer si le type contient un champ ou une propriété inaccessible qui masque (via le mot clé 'new') un champ ou une propriété portant le même nom précédemment accessible (public, par exemple) sur le type de base.

#### <a name="suggestion"></a>Suggestion

Ce problème peut être résolu en rendant le nouveau membre qui masque accessible à <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (en le marquant comme public, par exemple). Vous pouvez également utiliser le paramètre de configuration suivant qui rétablira le comportement de <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> de la version 4.0, ce qui permet de résoudre le problème :<pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)`

-->
