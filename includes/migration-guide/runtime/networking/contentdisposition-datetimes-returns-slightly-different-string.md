---
ms.openlocfilehash: 705bbd0e0bf80e0726d41898685a5e166e039f99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858481"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Les DateTime ContentDisposition retournent une chaîne légèrement différente

|   |   |
|---|---|
|Détails|À compter de la version 4.6, les représentations sous forme de chaîne des <xref:System.Net.Mime.ContentDisposition?displayProperty=name> ont été mises à jour pour toujours représenter le composant d’heure d’une valeur <xref:System.DateTime?displayProperty=name> avec deux chiffres. Ce changement a pour but de se conformer aux normes [RFC822](https://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). <xref:System.Net.Mime.ContentDisposition.ToString> retourne à présent une chaîne légèrement différente dans la version 4.6, lorsque l’un des éléments d’heure de la disposition est antérieur à 10:00. Notez que les ContentDisposition sont parfois sérialisés lors de leur conversion en chaînes. Pour cette raison, les opérations <xref:System.Net.Mime.ContentDisposition.ToString>, les sérialisations et les appels GetHashCode doivent être examinés.|
|Suggestion|Ne vous attendez pas à ce que les représentations sous forme de chaîne des ContentDisposition issues de différentes versions du .NET Framework puissent être comparées correctement. Reconvertissez les chaînes en ContentDisposition, si possible, avant d’effectuer une comparaison.|
|Étendue|Secondaire|
|Version|4.6|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
