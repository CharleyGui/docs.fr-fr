---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720186"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a>Reconnaissance d’URI de chemins d’accès UNC sur UNIX

La <xref:System.Uri> classe reconnaît maintenant les chaînes qui commencent par deux barres obliques ( `//` ) en tant que chemins d’accès UNC (Universal Naming Convention) sur les systèmes d’exploitation UNIX. Cette modification rend le comportement de ces chaînes cohérent sur toutes les plateformes.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par avec deux barres obliques, par exemple, `//contoso` sous la forme de chemins de fichiers absolus sur les systèmes d’exploitation UNIX. Toutefois, sous Windows, ces chaînes sont reconnues comme des chemins d’accès UNC.

À compter de .NET 5,0, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par avec deux barres obliques comme chemins d’accès UNC sur toutes les plateformes, y compris UNIX. En outre, les propriétés se comportent selon la sémantique UNC :

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> retourne `true`.
- Les barres obliques inverses dans le chemin d’accès sont remplacées par des barres obliques. Par exemple, `//first\second` devient `//first/second`.
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> n’encode pas les caractères en pourcentage. Par exemple, `//first/\uFFF0` n’est *pas* converti en `//first/%EF%BF%B0` .

#### <a name="version-introduced"></a>Version introduite

5,0

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
