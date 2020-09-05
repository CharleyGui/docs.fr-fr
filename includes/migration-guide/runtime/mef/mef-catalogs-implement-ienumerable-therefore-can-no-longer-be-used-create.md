---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497487"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur (objet <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>). La tentative de sérialisation d'un catalogue MEF lève une exception.

#### <a name="suggestion"></a>Suggestion

Ne peut plus utiliser un catalogue MEF pour créer un sérialiseur

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
