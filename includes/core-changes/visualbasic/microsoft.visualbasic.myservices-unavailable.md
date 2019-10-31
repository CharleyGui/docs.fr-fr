---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198414"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. MyServices non disponibles

Les types de l’espace de noms <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Modifier la description

Les types de l’espace de noms <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> étaient disponibles dans certaines versions préliminaires de .NET Core 3,0. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation des types **Microsoft. VisualBasic. MyServices** et de leurs membres, il existe des types et des membres correspondants dans la bibliothèque de classes .net. Voici un mappage des types **Microsoft. VisualBasic. MyServices** aux types de bibliothèques de classes .net équivalents :

|Type Microsoft. VisualBasic. MyServices|Type de bibliothèque de classes .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType> pour les applications WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> pour les applications Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Types dans l’espace de noms <xref:System.IO>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Types relatifs au registre dans l’espace de noms <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

