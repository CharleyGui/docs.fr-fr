---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496888"
---
### <a name="path-colon-checks-are-stricter"></a>Les vérifications des signes deux-points dans les chemins d’accès sont plus strictes

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2, un certain nombre de modifications ont été apportées pour prendre en charge les chemins d’accès précédemment non pris en charge (à la fois en termes de longueur et de format). Vérifie que la syntaxe du séparateur de lecteur (deux-points) est devenue plus correcte, ce qui a eu pour effet secondaire de bloquer certains chemins d’accès URI dans quelques API de chemin d’accès SELECT où elles étaient précédemment tolérées.

#### <a name="suggestion"></a>Suggestion

Si vous passez un URI à des API affectées, modifiez d’abord la chaîne pour en faire un chemin valide.

- Supprimer manuellement le schéma des URL (par exemple, supprimer `file://` des URL).

- Transmettez l’URI à la <xref:System.Uri> classe et utilisez <xref:System.Uri.LocalPath> .

Vous pouvez également désactiver la nouvelle normalisation de chemin d’accès en définissant le `Switch.System.IO.UseLegacyPathHandling` commutateur AppContext sur `true` .

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
