---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050562"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>La valeur de FrameworkDescription est .NET au lieu de .NET Core

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne désormais « .NET » au lieu de « .NET Core ».

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net core » dans le cadre de la chaîne de description, par exemple `.NET Core 3.1.1` .

À compter de .NET 5,0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net » dans le cadre de la chaîne de description, par exemple `.NET 5.0.0` .

#### <a name="reason-for-change"></a>Motif de modification

Avec .NET 5, `netcoreapp` est remplacé par `net` comme moniker de Framework cible courts. Pour des fins de cohérence, la description de l’infrastructure a également été mise à jour. La modification est cosmétique, car `FrameworkName` n’est pas encodé ailleurs que dans la <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriété.

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui recherche « .NET Core » dans la chaîne retournée par <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
