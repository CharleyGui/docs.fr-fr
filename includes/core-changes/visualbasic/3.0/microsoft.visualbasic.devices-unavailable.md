---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116338"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Types dans Microsoft.VisualBasic.Devices namespace non disponible

Les types <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> dans l’espace nom ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3.0 Aperçu 8

#### <a name="change-description"></a>Description de la modification

Les types <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> dans l’espace de nom étaient disponibles dans certains .NET Core 3.0 Versions aperçu,. Ils ne sont plus disponibles à partir de .NET Core 3.0 Aperçu 9.

Les types ont été supprimés pour éviter des dépendances inutiles à l’assemblage ou des changements de rupture dans les rejets ultérieurs.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend <xref:Microsoft.VisualBasic.Devices> de l’utilisation des types et de leurs membres, vous pouvez être en mesure d’utiliser un type ou un membre correspondant dans la bibliothèque de classe .NET. Par exemple, des fonctionnalités équivalentes <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> <xref:System.DateTime?displayProperty=nameWithType> à <xref:System.Environment?displayProperty=nameWithType> la classe sont fournies <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> par les types <xref:System.IO.Ports?displayProperty=nameWithType> et les types, et des fonctionnalités équivalentes à la classe sont fournies par des types dans l’espace nom.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
