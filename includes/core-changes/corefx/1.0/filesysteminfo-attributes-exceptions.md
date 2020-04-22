---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021818"
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

Core .NET bibliothèques

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
