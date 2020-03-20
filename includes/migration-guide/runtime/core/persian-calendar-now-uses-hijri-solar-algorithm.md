---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858374"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Le calendrier persan utilise désormais l’algorithme solaire hégirien

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6, la classe <xref:System.Globalization.PersianCalendar?displayProperty=name> utilise l’algorithme solaire hégirien. La conversion de dates entre le calendrier <xref:System.Globalization.PersianCalendar?displayProperty=name> et les autres calendriers peut produire un résultat légèrement différent à compter de .NET Framework 4.6 pour les dates antérieures à 1800 ou postérieures à 2023 (calendrier grégorien). De plus, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> est désormais <code>March 22, 0622</code> au lieu de <code>March 21, 0622</code>.|
|Suggestion|Notez que certaines dates anciennes ou futures peuvent être légèrement différentes quand vous utilisez le calendrier persan dans .NET Framework 4.6. En outre, quand vous sérialisez des dates dans plusieurs processus qui peuvent s’exécuter sur des versions différentes du .NET Framework, ne les stockez pas sous forme de chaînes de date PersianCalendar (puisque ces valeurs peuvent être différentes).|
|Étendue|Secondaire|
|Version|4.6|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
