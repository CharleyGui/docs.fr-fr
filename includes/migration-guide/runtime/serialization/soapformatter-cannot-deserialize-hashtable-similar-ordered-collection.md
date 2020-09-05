---
ms.openlocfilehash: 71cc7119710a2b381626dd9cf4ab66265eb3deba
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497320"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter ne peut pas désérialiser Hashtable et les objets de collection ordonnée similaires

#### <a name="details"></a>Détails

<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> ne garantit pas que les objets sérialisés dans une version du .NET Framework pourront être désérialisés correctement dans une autre version. En effet, certaines collections ordonnées (comme <xref:System.Collections.Hashtable?displayProperty=fullName>) ont gagné de nouveaux membres entre les versions 4.0 et 4.5. De fait, les objets de ces types ne peuvent pas être désérialisés avec .NET Framework 4.0 s’ils ont été sérialisés avec .NET Framework 4.5. Notez que si les données sérialisées sont sérialisées et désérialisées avec la même version du .NET Framework, aucun problème ne se produit.

#### <a name="suggestion"></a>Suggestion

La sérialisation <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> doit être remplacée par la sérialisation <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> ou <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> pour ne pas être affectée par les changements du .NET Framework.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
