---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449393"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Variation de la valeur par défaut de UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>a une valeur `false` par défaut de sur .NET Core. Sur .NET Framework, sa `true`valeur par défaut est .

#### <a name="change-description"></a>Description de la modification

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>vous permet de lancer une application directement, `Process.Start("mspaint.exe")` par exemple, avec un code comme celui lance Paint. Il vous permet également de lancer <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> indirectement une `true`application associée si elle est configuré à . Sur .NET Framework, la <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`valeur par défaut `Process.Start("mytextfile.txt")` pour est , ce qui signifie que le code tel serait lancer Notepad, si vous avez associé des fichiers *.txt* avec cet éditeur. Pour éviter de lancer indirectement une application sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> .NET Framework, vous devez définir explicitement à `false`. Sur .NET Core, la <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`valeur par défaut pour est . Cela signifie que, par défaut, les applications `Process.Start`associées ne sont pas lancées lorsque vous appelez .

Ce changement a été introduit dans .NET Core pour des raisons de performance. Typiquement, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> est utilisé pour lancer une application directement. Le lancement direct d’une application n’a pas besoin d’impliquer la coque Windows et d’engager le coût de performance associé. Pour rendre ce cas par défaut plus rapide, .NET Core change la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`. Vous pouvez opter pour le chemin plus lent si vous en avez besoin.

#### <a name="version-introduced"></a>Version introduite

2.1

> [!NOTE]
> Dans les versions précédentes `UseShellExecute` de .NET Core, n’a pas été implémenté pour Windows.

#### <a name="recommended-action"></a>Action recommandée

Si votre application s’appuie <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> l’ancien comportement, appelez avec défini `true` sur l’objet. <xref:System.Diagnostics.ProcessStartInfo>

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
