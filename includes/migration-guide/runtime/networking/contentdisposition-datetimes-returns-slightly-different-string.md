---
ms.openlocfilehash: 529d1b83c0637f705b725a64aa82e2c053bbfd19
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858481"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Les DateTime ContentDisposition retournent une chaîne légèrement différente

|   |   |
|---|---|
|Détails|À compter de la version 4.6, les représentations sous forme de chaîne des <xref:System.Net.Mime.ContentDisposition?displayProperty=name> ont été mises à jour pour toujours représenter le composant d’heure d’une valeur <xref:System.DateTime?displayProperty=name> avec deux chiffres. Ce changement a pour but de se conformer aux normes [RFC822](https://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). <xref:System.Net.Mime.ContentDisposition.ToString> retourne à présent une chaîne légèrement différente dans la version 4.6, lorsque l’un des éléments d’heure de la disposition est antérieur à 10:00. Notez que les ContentDisposition sont parfois sérialisés lors de leur conversion en chaînes. Pour cette raison, les opérations <xref:System.Net.Mime.ContentDisposition.ToString>, les sérialisations et les appels GetHashCode doivent être examinés.|
|Suggestion|Ne vous attendez pas à ce que les représentations sous forme de chaîne des ContentDisposition issues de différentes versions du .NET Framework puissent être comparées correctement. Reconvertissez les chaînes en ContentDisposition, si possible, avant d’effectuer une comparaison.|
|Portée|Mineur|
|Version|4.6|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

