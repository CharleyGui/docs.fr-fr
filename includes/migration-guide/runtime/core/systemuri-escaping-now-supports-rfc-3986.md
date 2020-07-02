---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619991"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>L’échappement de System.Uri prend maintenant en charge la norme RFC 3986

#### <a name="details"></a>Détails

L’échappement d’URI a été modifié dans NET Framework 4.5 de manière à prendre en charge la norme [RFC 3986](https://tools.ietf.org/html/rfc3986). Ces modifications sont les suivantes :<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> représente une séquence d'échappement pour les caractères réservés basés sur la norme RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> ne représente pas une séquence d'échappement pour les caractères réservés.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> ne lève pas d'exception s'il rencontre une séquence d'échappement non valide.</li><li>Les caractères d'échappement non réservés sont sans séquence d'échappement.</li></ul>

#### <a name="suggestion"></a>Suggestion

<ul><li>Mettez à jour les applications pour qu’elles ne comptent pas sur <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> pour lever une exception en cas de séquence d’échappement non valide. Ces séquences sont à présent directement détectées.</li><li>Il est également possible que les URI avec et sans séquence d’échappement, ainsi que les chaînes de données, varient entre les versions 4.0 et 4.5 du .NET Framework. De plus, ils ne doivent pas être comparés directement entre différentes versions de .NET. Ils doivent être analysés et normalisés dans une seule version du .NET avant de faire l’objet d’une comparaison.</li></ul>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
