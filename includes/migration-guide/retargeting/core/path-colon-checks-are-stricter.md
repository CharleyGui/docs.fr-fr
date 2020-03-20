---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859250"
---
### <a name="path-colon-checks-are-stricter"></a>Les vérifications des signes deux-points dans les chemins d’accès sont plus strictes

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.2, un certain nombre de modifications ont été apportées pour prendre en charge les chemins d’accès précédemment non pris en charge (à la fois en termes de longueur et de format). Les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes, ce qui a eu pour effet secondaire de bloquer certains chemins d’URI dans quelques API de sélection de chemin d’accès, où ils étaient tolérés.|
|Suggestion|Si vous passez un URI à des API affectées, modifiez d’abord la chaîne pour en faire un chemin valide.<ul><li>Supprimez manuellement le schéma des URL (par exemple, supprimez <code>file://</code> des URL)</li><li>Passez l’URI de la classe <xref:System.Uri> et utilisez <xref:System.Uri.LocalPath></li></ul>Vous pouvez également refuser la nouvelle normalisation de chemin en définissant le commutateur AppContext <code>Switch.System.IO.UseLegacyPathHandling</code> sur true.|
|Étendue|Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
