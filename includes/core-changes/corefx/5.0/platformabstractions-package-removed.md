---
ms.openlocfilehash: d85fb8df7afdc5f4c3faecebcd24d11677798bc9
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365611"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a>Package Microsoft. DotNet. PlatformAbstractions supprimé

Aucune nouvelle version du [package NuGet Microsoft. dotnet. PlatformAbstractions](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) ne sera produite.

#### <a name="change-description"></a>Description de la modification

Auparavant, les nouvelles versions de la <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliothèque étaient produites avec les nouvelles versions de .net core. À l’avenir, aucune nouvelle fonctionnalité ne sera ajoutée à la bibliothèque et aucune nouvelle version principale ne sera publiée. Toutefois, les versions existantes de la bibliothèque continuent de fonctionner et seront desservies.

La <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliothèque chevauche les API qui sont déjà établies dans System. \* namespaces. En outre, certaines <xref:Microsoft.DotNet.PlatformAbstractions> API n’ont pas été conçues avec le même niveau de surveillance et de prise en charge à long terme que le reste du système. \* Interfaces. Par exemple, <xref:Microsoft.DotNet.PlatformAbstractions> utilise l' `Platform` énumération pour décrire la plateforme du système d’exploitation actuel. Cette conception d’énumération a été explicitement rejetée lorsque l' <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API a été conçue, afin de permettre de nouvelles plateformes et une flexibilité future.

Les scénarios activés par la <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliothèque sont désormais possibles sans lui. Les versions existantes continueront à fonctionner, même dans .NET 5,0 et versions ultérieures, et seront servies avec les versions précédentes de .NET Core. Toutefois, les nouvelles fonctionnalités ne seront pas ajoutées à la bibliothèque. Au lieu de cela, de nouvelles fonctionnalités seront ajoutées à d’autres bibliothèques et API.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 6

#### <a name="recommended-action"></a>Action recommandée

- Vous pouvez continuer à utiliser des versions antérieures de la bibliothèque si elles répondent à vos besoins.

- Si les versions antérieures ne répondent pas à vos besoins, remplacez les utilisations des `PlatformAbstractions` API par les remplacements recommandés.

  | `PlatformAbstractions`MOBILEVBACTIVEX | Remplacement recommandé |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> et <xref:System.Environment.OSVersion?displayProperty=nameWithType> |

  > [!NOTE]
  > La plupart des cas d’usage pour et sont utilisés à des `RuntimeEnvironment.OperatingSystem` `RuntimeEnvironment.OperatingSystemVersion` fins d’affichage, par exemple, pour afficher à un utilisateur, journalisation et télémétrie. Il n’est pas recommandé de prendre des décisions d’exécution basées sur une version du système d’exploitation. <xref:System.Environment.OSVersion?displayProperty=nameWithType>retourne désormais la version correcte pour les systèmes d’exploitation Windows et macOS. Toutefois, pour la plupart des distributions UNIX, ce qui est considéré comme étant la « version du système d’exploitation » n’est pas aussi simple. Par exemple, il peut s’agir de la version du noyau Linux, ou de la version distribution. Pour la plupart des plateformes UNIX, <xref:System.Environment.OSVersion?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> retournent la version retournée par `uname` . Pour obtenir le nom et la version des distribution Linux, l’approche recommandée consiste à lire le fichier */etc/OS-Release* .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
