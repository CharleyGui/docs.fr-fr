---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620058"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter ne peut pas désérialiser Hashtable et les objets de collection ordonnée similaires

#### <a name="details"></a>Détails

<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> ne garantit pas que les objets sérialisés dans une version du .NET Framework pourront être désérialisés correctement dans une autre version. En effet, certaines collections ordonnées (comme <xref:System.Collections.Hashtable?displayProperty=fullName>) ont gagné de nouveaux membres entre les versions 4.0 et 4.5. De fait, les objets de ces types ne peuvent pas être désérialisés avec .NET Framework 4.0 s’ils ont été sérialisés avec .NET Framework 4.5. Notez que si les données sérialisées sont sérialisées et désérialisées avec la même version du .NET Framework, aucun problème ne se produit.

#### <a name="suggestion"></a>Suggestion

La sérialisation <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> doit être remplacée par la sérialisation <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> ou <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> pour ne pas être affectée par les changements du .NET Framework.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
