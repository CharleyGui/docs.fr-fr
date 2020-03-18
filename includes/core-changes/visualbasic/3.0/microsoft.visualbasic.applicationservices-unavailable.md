---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116349"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Types dans Microsoft.VisualBasic.ApplicationServices namespace non disponible

Les types <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> dans l’espace nom ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3.0 Aperçu 8

#### <a name="change-description"></a>Description de la modification

Les types <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> dans l’espace de nom étaient disponibles dans certains .NET Core 3.0 Versions aperçu. Ils ne sont plus disponibles à partir de .NET Core 3.0 Aperçu 9.

Les types ont été supprimés pour éviter des dépendances inutiles à l’assemblage ou des changements de rupture dans les rejets ultérieurs.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend <xref:Microsoft.VisualBasic.ApplicationServices> de l’utilisation des types et de leurs membres, vous pouvez être en mesure d’utiliser un type ou un membre correspondant dans la bibliothèque de classe .NET. Par exemple, <xref:System.Environment?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> certains et les membres fournissent <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> des fonctionnalités équivalentes aux propriétés de la classe.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
