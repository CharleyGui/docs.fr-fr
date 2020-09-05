---
ms.openlocfilehash: 14581b193fc000c7f805a0602e191cad688c014a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496469"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Le calendrier persan utilise désormais l’algorithme solaire hégirien

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6, la classe <xref:System.Globalization.PersianCalendar?displayProperty=fullName> utilise l’algorithme solaire hégirien. La conversion de dates entre le calendrier <xref:System.Globalization.PersianCalendar?displayProperty=fullName> et les autres calendriers peut produire un résultat légèrement différent à compter de .NET Framework 4.6 pour les dates antérieures à 1800 ou postérieures à 2023 (calendrier grégorien). De plus, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> est désormais <code>March 22, 0622</code> au lieu de <code>March 21, 0622</code>.

#### <a name="suggestion"></a>Suggestion

Notez que certaines dates anciennes ou futures peuvent être légèrement différentes quand vous utilisez le calendrier persan dans .NET Framework 4.6. En outre, quand vous sérialisez des dates dans plusieurs processus qui peuvent s’exécuter sur des versions différentes du .NET Framework, ne les stockez pas sous forme de chaînes de date PersianCalendar (puisque ces valeurs peuvent être différentes).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,6|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Globalization.PersianCalendar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Globalization.PersianCalendar`

-->
