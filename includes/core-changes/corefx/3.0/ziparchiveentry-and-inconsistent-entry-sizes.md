---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568091"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry ne gère plus les archives avec des tailles d’entrée incohérentes

Les archives zip répertorient à la fois la taille compressée et la taille non compressée dans le répertoire central et l’en-tête local.  Les données d’entrée lui-même indiquent également sa taille.  Dans .NET Core 2,2 et les versions antérieures, ces valeurs n’ont jamais été vérifiées pour des fins de cohérence. À compter de .NET Core 3,0, ils sont désormais.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2,2 et les versions antérieures <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> , fonctionne même si l’en-tête local est en désaccord avec l’en-tête central du fichier zip. Les données sont décompressées jusqu’à la fin du flux compressé, même si leur longueur dépasse la taille du fichier non compressé figurant dans le répertoire central/l’en-tête local.

À compter de .NET Core 3,0, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> la méthode vérifie que l’en-tête local et l’en-tête central s’accordent sur des tailles compressées et non compressées d’une entrée.  Si ce n’est pas le cas, la méthode <xref:System.IO.InvalidDataException> lève une si les tailles d’en-tête local et/ou de liste de descripteurs de données de l’archive ne sont pas en accord avec le répertoire central du fichier. zip. Lors de la lecture d’une entrée, les données décompressées sont tronquées à la taille de fichier non compressée indiquée dans l’en-tête.

Cette modification a été apportée pour <xref:System.IO.Compression.ZipArchiveEntry> s’assurer qu’un correspond correctement à la taille de ses données et que seule cette quantité de données est lue.

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
