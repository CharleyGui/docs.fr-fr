---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032002"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException levée par FileSystemInfo. Attributes

Dans .NET Core, une <xref:System.UnauthorizedAccessException> exception est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier mais ne dispose pas de l’autorisation d’écriture.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, une <xref:System.ArgumentException> exception est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier dans, <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> mais ne dispose pas de l’autorisation d’écriture. Dans .NET Core, une <xref:System.UnauthorizedAccessException> exception est levée à la place. (Dans .NET Core, une <xref:System.ArgumentException> est toujours levée si l’appelant tente de définir un attribut de fichier non valide.)

#### <a name="version-introduced"></a>Version introduite

1.0

#### <a name="recommended-action"></a>Action recommandée

Modifiez toutes les `catch` instructions pour intercepter un <xref:System.UnauthorizedAccessException> au lieu de, ou en plus d’un <xref:System.ArgumentException> , si nécessaire.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
