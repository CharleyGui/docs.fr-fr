---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181831"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. MyServices non disponibles

Les types de l' <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> espace de noms ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="details"></a>Détails

Les types de l' <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> espace de noms étaient disponibles dans certaines versions préliminaires de .net Core 3,0,. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.
 
#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation des types **Microsoft. VisualBasic. MyServices** et de leurs membres, il existe des types et des membres correspondants dans la bibliothèque de classes .net. Voici un mappage des types **Microsoft. VisualBasic. MyServices** aux types de bibliothèques de classes .net équivalents :

|Type Microsoft. VisualBasic. MyServices|Type de bibliothèque de classes .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>pour les applications WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> , pour les applications Windows Forms| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Types dans l' <xref:System.IO> espace de noms|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Types liés au registre dans l' <xref:Microsoft.Win32> espace de noms|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

