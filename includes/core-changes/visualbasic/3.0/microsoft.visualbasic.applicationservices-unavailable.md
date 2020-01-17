---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116349"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. ApplicationServices non disponibles

Les types de l’espace de noms <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Description des modifications

Les types de l’espace de noms <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> étaient disponibles dans certaines versions préliminaires de .NET Core 3,0. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.ApplicationServices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .NET. Par exemple, certains <xref:System.Environment?displayProperty=nameWithType> et <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> membres fournissent des fonctionnalités équivalentes aux propriétés de la classe <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType>.

#### <a name="category"></a>Catégorie

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
