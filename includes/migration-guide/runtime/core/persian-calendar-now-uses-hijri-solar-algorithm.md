---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621287"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Le calendrier persan utilise désormais l’algorithme solaire hégirien

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6, la classe <xref:System.Globalization.PersianCalendar?displayProperty=fullName> utilise l’algorithme solaire hégirien. La conversion de dates entre le calendrier <xref:System.Globalization.PersianCalendar?displayProperty=fullName> et les autres calendriers peut produire un résultat légèrement différent à compter de .NET Framework 4.6 pour les dates antérieures à 1800 ou postérieures à 2023 (calendrier grégorien). De plus, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> est désormais <code>March 22, 0622</code> au lieu de <code>March 21, 0622</code>.

#### <a name="suggestion"></a>Suggestion

Notez que certaines dates anciennes ou futures peuvent être légèrement différentes quand vous utilisez le calendrier persan dans .NET Framework 4.6. En outre, quand vous sérialisez des dates dans plusieurs processus qui peuvent s’exécuter sur des versions différentes du .NET Framework, ne les stockez pas sous forme de chaînes de date PersianCalendar (puisque ces valeurs peuvent être différentes).

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
