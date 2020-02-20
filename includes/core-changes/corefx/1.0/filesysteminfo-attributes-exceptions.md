---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449395"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException levée par FileSystemInfo. Attributes

Dans .NET Core, une <xref:System.UnauthorizedAccessException> est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier, mais ne dispose pas de l’autorisation d’écriture.

#### <a name="change-description"></a>Modifier la description

Dans .NET Framework, une <xref:System.ArgumentException> est levée lorsque l’appelant tente de définir une valeur d’attribut de fichier dans <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, mais ne dispose pas de l’autorisation d’écriture. Dans .NET Core, une <xref:System.UnauthorizedAccessException> est levée à la place. (Dans .NET Core, une <xref:System.ArgumentException> est toujours levée si l’appelant tente de définir un attribut de fichier non valide.)

#### <a name="version-introduced"></a>Version introduite

1.0

#### <a name="recommended-action"></a>Action recommandée

Modifiez les instructions `catch` pour intercepter une <xref:System.UnauthorizedAccessException> au lieu de, ou en plus d’un <xref:System.ArgumentException>, si nécessaire.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
