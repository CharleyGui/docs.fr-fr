---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617163"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode et WebUtility.HtmlDecode font un aller-retour correct au plan BMP

#### <a name="details"></a>Détails

Pour les applications qui ciblent .NET Framework 4.5, les caractères extérieurs au plan BMP (Basic Multilingual Plane) font un aller-retour correct quand ils sont passés à la méthode <xref:System.Net.WebUtility.HtmlDecode(System.String)>.

#### <a name="suggestion"></a>Suggestion

Cette modification ne doit avoir aucun effet sur les applications actuelles, mais pour restaurer le comportement d’origine, affectez `targetFramework` à l’attribut de l' `<httpRuntime>` élément une chaîne autre que « 4,5 ». Vous pouvez également définir les attributs `unicodeEncodingConformance` et `unicodeDecodingConformance` de l'élément de configuration `<webUtility>` pour contrôler ce comportement indépendamment de la version ciblée du .NET Framework.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
