---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496706"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Les DateTime ContentDisposition retournent une chaîne légèrement différente

#### <a name="details"></a>Détails

À compter de la version 4.6, les représentations sous forme de chaîne des <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> ont été mises à jour pour toujours représenter le composant d’heure d’une valeur <xref:System.DateTime?displayProperty=fullName> avec deux chiffres. Ce changement a pour but de se conformer aux normes [RFC822](https://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). <xref:System.Net.Mime.ContentDisposition.ToString> retourne à présent une chaîne légèrement différente dans la version 4.6, lorsque l’un des éléments d’heure de la disposition est antérieur à 10:00. Notez que les ContentDisposition sont parfois sérialisés lors de leur conversion en chaînes. Pour cette raison, les opérations <xref:System.Net.Mime.ContentDisposition.ToString>, les sérialisations et les appels GetHashCode doivent être examinés.

#### <a name="suggestion"></a>Suggestion

Ne vous attendez pas à ce que les représentations sous forme de chaîne des ContentDisposition issues de différentes versions du .NET Framework puissent être comparées correctement. Reconvertissez les chaînes en ContentDisposition, si possible, avant d’effectuer une comparaison.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,6|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
