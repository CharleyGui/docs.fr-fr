---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449395"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException jeté par FileSystemInfo.Attributes

Dans .NET Core, un <xref:System.UnauthorizedAccessException> est lancé lorsque l’appelant tente de définir une valeur d’attribut de fichier, mais n’a pas d’autorisation d’écriture.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, un <xref:System.ArgumentException> est lancé lorsque l’appelant <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> tente de définir une valeur d’attribut de fichier, mais n’a pas d’autorisation d’écriture. Dans .NET Core, un <xref:System.UnauthorizedAccessException> est jeté à la place. (Dans .NET Core, un <xref:System.ArgumentException> est toujours jeté si l’appelant tente de définir un attribut de fichier invalide.)

#### <a name="version-introduced"></a>Version introduite

1.0

#### <a name="recommended-action"></a>Action recommandée

Modifier `catch` toutes les <xref:System.UnauthorizedAccessException> déclarations pour attraper un <xref:System.ArgumentException>au lieu ou en plus d’un , si nécessaire.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
