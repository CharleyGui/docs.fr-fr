---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031986"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Modification de la valeur par défaut de UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a une valeur par défaut de `false` sur .net core. Sur .NET Framework, sa valeur par défaut est `true` .

#### <a name="change-description"></a>Description de la modification

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> vous permet de lancer une application directement, par exemple avec un code tel que `Process.Start("mspaint.exe")` qui lance Paint. Elle vous permet également de lancer indirectement une application associée si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a la valeur `true` . Sur .NET Framework, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true` , ce qui signifie que le code `Process.Start("mytextfile.txt")` peut lancer le bloc-notes, si vous avez associé des fichiers *. txt* à cet éditeur. Pour empêcher le lancement indirect d’une application sur .NET Framework, vous devez définir explicitement sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` . Sur .NET Core, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `false` . Cela signifie que, par défaut, les applications associées ne sont pas lancées lorsque vous appelez `Process.Start` .

Cette modification a été introduite dans .NET Core pour des raisons de performances. En général, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> est utilisé pour lancer une application directement. Le lancement d’une application directement n’a pas besoin d’impliquer l’interpréteur de commandes Windows et de supporter les coûts de performances associés. Pour que ce cas par défaut soit plus rapide, .NET Core remplace la valeur par défaut par <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` . Vous pouvez choisir le chemin le plus lent si vous en avez besoin.

#### <a name="version-introduced"></a>Version introduite

2.1

> [!NOTE]
> Dans les versions antérieures de .NET Core, `UseShellExecute` n’était pas implémenté pour Windows.

#### <a name="recommended-action"></a>Action recommandée

Si votre application s’appuie sur l’ancien comportement, appelez <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> avec <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> défini sur `true` sur l' <xref:System.Diagnostics.ProcessStartInfo> objet.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
