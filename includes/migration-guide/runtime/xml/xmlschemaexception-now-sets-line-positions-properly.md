---
ms.openlocfilehash: 04d1c1162dc79bbcb0578c6661466f4d58a57acc
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496564"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException définit désormais les positions de ligne correctement

#### <a name="details"></a>Détails

Si la valeur <xref:System.Xml.Linq.LoadOptions.SetLineInfo> est passée à la méthode Load et qu’une erreur de validation se produit, les propriétés <xref:System.Xml.Schema.XmlSchemaException.LineNumber> et <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contiennent désormais les informations de ligne.

#### <a name="suggestion"></a>Suggestion

Le code de gestion des exceptions qui suppose que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> et <xref:System.Xml.Schema.XmlSchemaException.LinePosition> ne seront pas définies doit être modifié, car ces propriétés seront maintenant définies correctement quand SetLineInfo est utilisé lors du chargement du code XML.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Xml.Linq.LoadOptions.SetLineInfo`

-->
