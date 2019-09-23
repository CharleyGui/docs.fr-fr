---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181970"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Modification du comportement de l’analyse et de la mise en forme à virgule flottante

Le comportement d’analyse et de mise en forme de virgule <xref:System.Double> flottante (par les types et <xref:System.Single> ) est désormais conforme à la norme IEEE.

#### <a name="change-description"></a>Modifier la description

Dans .net Core 2,2 et versions antérieures, la mise en <xref:System.Double.ToString%2A?displayProperty=nameWithType> forme <xref:System.Single.ToString%2A?displayProperty=nameWithType>avec et, ainsi que <xref:System.Double.Parse%2A?displayProperty=nameWithType>l' <xref:System.Double.TryParse%2A?displayProperty=nameWithType>analyse <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> avec,, et ne sont pas conformes à IEEE. Par conséquent, il est impossible de garantir qu’une valeur fera l’aller-retour avec toute chaîne de format standard ou personnalisée prise en charge. Pour certaines entrées, la tentative d’analyse d’une valeur mise en forme peut échouer et, pour d’autres, la valeur analysée n’est pas égale à la valeur d’origine.

À compter de .NET Core 3,0, les opérations d’analyse et de mise en forme sont conformes à la norme IEEE 754. Cela garantit que le comportement des types à virgule flottante dans .NET correspond à celui des langages compatibles IEEE tels C#que. Pour plus d’informations, consultez le billet de blog [améliorations de la mise en forme et de l’analyse de la virgule flottante dans .net Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La section « impact potentiel sur le code existant » des améliorations de l’analyse de la [virgule flottante et de la mise en forme dans le billet de blog .net core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) suggère des modifications apportées à votre code si vous observez un changement de comportement par rapport aux applications .net Core 2,2 généralement, Cela implique l’utilisation d’une chaîne de format standard ou personnalisée différente pour appliquer le comportement souhaité. Certains résultats peuvent ne pas avoir de solution de contournement s’ils étaient précédemment incorrects.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
