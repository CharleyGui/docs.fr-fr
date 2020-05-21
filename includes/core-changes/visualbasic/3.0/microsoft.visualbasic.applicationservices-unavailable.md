---
ms.openlocfilehash: 09027863ff2f0009a14578db35db870c27369726
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721253"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Types dans l’espace de noms Microsoft. VisualBasic. ApplicationServices non disponibles

Les types de l' <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> espace de noms ne sont pas disponibles.

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Description de la modification

Les types de l' <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> espace de noms étaient disponibles dans certaines versions préliminaires de .net Core 3,0. Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.

Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.

#### <a name="recommended-action"></a>Action recommandée

Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.ApplicationServices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .net. Par exemple, certains <xref:System.Environment?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> membres et fournissent des fonctionnalités équivalentes aux propriétés de la <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> classe.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
