---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031991"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>Process. StartInfo lève une exception InvalidOperationException pour les processus que vous n’avez pas démarrés

La lecture <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> de la propriété pour les processus que votre code n’a pas démarré lève une exception <xref:System.InvalidOperationException> .

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, l’accès à la <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriété pour les processus que votre code n’a pas démarré retourne un <xref:System.Diagnostics.ProcessStartInfo> objet factice. L’objet factice contient des valeurs par défaut pour toutes ses propriétés, à l’exception de <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .

À compter de .NET Core 1,0, si vous lisez la <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriété d’un processus que vous n’avez pas démarré (autrement dit, en appelant <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ), une <xref:System.InvalidOperationException> exception est levée.

#### <a name="version-introduced"></a>Version introduite

1.0

#### <a name="recommended-action"></a>Action recommandée

N’accédez pas à la <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriété pour les processus que votre code n’a pas démarré. Par exemple, ne lisez pas cette propriété pour les processus retournés par <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
