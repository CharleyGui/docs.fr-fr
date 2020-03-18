---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568091"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes

Les archives zip énumèrent à la fois la taille comprimée et la taille non compressée dans le répertoire central et l’en-tête local.  Les données d’entrée elles-mêmes indiquent également sa taille.  Dans .NET Core 2.2 et les versions antérieures, ces valeurs n’ont jamais été vérifiées pour la cohérence. En commençant par .NET Core 3.0, ils le sont maintenant.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2.2 et <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> les versions antérieures, réussit même si l’en-tête local n’est pas d’accord avec l’en-tête central du fichier zip. Les données sont décompressées jusqu’à ce que la fin du flux compressé soit atteinte, même si sa longueur dépasse la taille du fichier non compressé énuméré dans l’annuaire central /en-tête local.

À partir de .NET Core 3.0, la méthode vérifie que l’en-tête <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> local et l’en-tête central s’entendent sur les tailles comprimées et non compressées d’une entrée.  S’ils ne le font <xref:System.IO.InvalidDataException> pas, la méthode jette un si l’en-tête local de l’archive et / ou les tailles de liste descripteur de données qui ne sont pas d’accord avec l’annuaire central du fichier zip. Lors de la lecture d’une entrée, les données décompressées sont tronquées sur la taille du fichier non compressé figurant dans l’en-tête.

Cette modification a été <xref:System.IO.Compression.ZipArchiveEntry> apportée pour s’assurer qu’un traitement à juste titre représente la taille de ses données et que seule cette quantité de données est lue.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Reconditionner toute archive zip qui présente ces problèmes.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
