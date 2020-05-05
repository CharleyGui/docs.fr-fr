---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116338"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. Devices non disponible

Les types de l' <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> espace de noms ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Description de la modification

Les types de l' <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> espace de noms étaient disponibles dans certaines versions préliminaires de .net Core 3,0,. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.Devices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .net. Par exemple, les fonctionnalités équivalentes <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> à la classe sont fournies <xref:System.DateTime?displayProperty=nameWithType> par <xref:System.Environment?displayProperty=nameWithType> les types et, et les fonctionnalités <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> équivalentes à la classe sont fournies <xref:System.IO.Ports?displayProperty=nameWithType> par les types dans l’espace de noms.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
