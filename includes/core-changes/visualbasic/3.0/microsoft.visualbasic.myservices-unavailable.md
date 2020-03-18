---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116376"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Types dans Microsoft.VisualBasic.MyServices namespace non disponible

Les types <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> dans l’espace nom ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3.0 Aperçu 8

#### <a name="change-description"></a>Description de la modification

Les types <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> dans l’espace de nom étaient disponibles dans certains .NET Core 3.0 Versions aperçu. Ils ne sont plus disponibles à partir de .NET Core 3.0 Aperçu 9.

Les types ont été supprimés pour éviter des dépendances inutiles à l’assemblage ou des changements de rupture dans les rejets ultérieurs.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation des types **Microsoft.VisualBasic.MyServices** et de leurs membres, il existe des types et membres correspondants dans la bibliothèque de classe .NET. Ce qui suit est une cartographie des types **Microsoft.VisualBasic.MyServices** à leurs types de bibliothèque de classe .NET équivalents:

|Type Microsoft.VisualBasic.MyServices|Type de bibliothèque de classe .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>pour les applications <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> WPF, pour les applications Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Types dans <xref:System.IO> l’espace nom|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Types liés au <xref:Microsoft.Win32> registre dans l’espace nom|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
