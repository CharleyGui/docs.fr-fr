---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911555"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Modification de la valeur par défaut de UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a une valeur par défaut de `false` sur .net core. Sur .NET Framework, sa valeur par défaut est `true` .

#### <a name="change-description"></a>Description de la modification

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> vous permet de lancer une application directement, par exemple avec un code tel que `Process.Start("mspaint.exe")` qui lance Paint. Elle vous permet également de lancer indirectement une application associée si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a la valeur `true` . Sur .NET Framework, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true` , ce qui signifie que le code `Process.Start("mytextfile.txt")` peut lancer le bloc-notes, si vous avez associé des fichiers *. txt* à cet éditeur. Pour empêcher le lancement indirect d’une application sur .NET Framework, vous devez définir explicitement sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` . Sur .NET Core, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `false` . Cela signifie que, par défaut, les applications associées ne sont pas lancées lorsque vous appelez `Process.Start` .

Les propriétés suivantes sur <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> ne sont fonctionnelles que si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true` :

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.

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
