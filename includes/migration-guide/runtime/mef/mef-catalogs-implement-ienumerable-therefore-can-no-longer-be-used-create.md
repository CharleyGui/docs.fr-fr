---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620034"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur (objet <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>). La tentative de sérialisation d'un catalogue MEF lève une exception.

#### <a name="suggestion"></a>Suggestion

Ne peut plus utiliser un catalogue MEF pour créer un sérialiseur

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime|
