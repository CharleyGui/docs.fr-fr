---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721621"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. Devices non disponible

Les types de l' <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> espace de noms ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Description de la modification

Les types de l' <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> espace de noms étaient disponibles dans certaines versions préliminaires de .net Core 3,0,. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.Devices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .net. Par exemple, les fonctionnalités équivalentes à la <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> classe sont fournies par les <xref:System.DateTime?displayProperty=nameWithType> <xref:System.Environment?displayProperty=nameWithType> types et, et les fonctionnalités équivalentes à la <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> classe sont fournies par les types dans l' <xref:System.IO.Ports?displayProperty=nameWithType> espace de noms.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
