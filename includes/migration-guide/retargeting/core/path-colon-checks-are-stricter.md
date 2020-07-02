---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614483"
---
### <a name="path-colon-checks-are-stricter"></a>Les vérifications des signes deux-points dans les chemins d’accès sont plus strictes

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2, un certain nombre de modifications ont été apportées pour prendre en charge les chemins d’accès précédemment non pris en charge (à la fois en termes de longueur et de format). Les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes, ce qui a eu pour effet secondaire de bloquer certains chemins d’URI dans quelques API de sélection de chemin d’accès, où ils étaient tolérés.

#### <a name="suggestion"></a>Suggestion

Si vous passez un URI à des API affectées, modifiez d’abord la chaîne pour en faire un chemin valide.<ul><li>Supprimez manuellement le schéma des URL (par exemple, supprimez `file://` des URL)

- Passez l’URI de la classe <xref:System.Uri> et utilisez <xref:System.Uri.LocalPath>

Vous pouvez également refuser la nouvelle normalisation de chemin en définissant le commutateur AppContext `Switch.System.IO.UseLegacyPathHandling` sur true.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
