---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619932"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode ne décode plus les séquences d’entrée non valides

#### <a name="details"></a>Détails

Par défaut, les méthodes de décodage ne décodent plus une séquence d'entrée non valide en une chaîne UTF-16 non valide. Au lieu de cela, elles retournent l'entrée d'origine.

#### <a name="suggestion"></a>Suggestion

Le changement lié à la sortie du décodeur doit importer uniquement si vous stockez des données binaires à la place de données UTF-16 dans les chaînes. Pour contrôler explicitement ce comportement, affectez à l’attribut <code>aspnet:AllowRelaxedUnicodeDecoding</code> de l’élément [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) la valeur <code>true</code> pour activer le comportement hérité ou la valeur <code>false</code> pour activer le comportement actuel.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
