---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116338"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. Devices non disponible

Les types de l’espace de noms <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Description des modifications

Les types de l’espace de noms <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> étaient disponibles dans certaines versions préliminaires de .NET Core 3,0,. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.Devices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .NET. Par exemple, les fonctionnalités équivalentes à la classe <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> sont fournies par les types <xref:System.DateTime?displayProperty=nameWithType> et <xref:System.Environment?displayProperty=nameWithType>, et les fonctionnalités équivalentes à la classe <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sont fournies par les types dans l’espace de noms <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Catégorie

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
