---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021615"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Le formatage et l’analyse des points flottants ont changé

Le comportement flottant d’analyse et <xref:System.Double> de <xref:System.Single> formatage des points (par les types et les types) est maintenant conforme à l’IEEE.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2.2 et les <xref:System.Double.ToString%2A?displayProperty=nameWithType> versions antérieures, le formatage avec <xref:System.Single.ToString%2A?displayProperty=nameWithType>et , et l’analyse <xref:System.Double.Parse%2A?displayProperty=nameWithType>avec , <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> ne sont pas conformes à l’IEEE. Par conséquent, il est impossible de garantir qu’une valeur sera aller-retour avec n’importe quelle chaîne de format standard ou personnalisé prise en charge. Pour certaines entrées, la tentative d’analyser une valeur formatée peut échouer, et pour d’autres, la valeur analysée n’égale pas la valeur originale.

À partir de .NET Core 3.0, les opérations d’analyse et de mise en forme sont conformes à l’IEEE 754. Cela garantit que le comportement des types de points flottants en .NET correspond à celui des langues conformes à l’IEEE telles que le C. Pour plus d’informations, voir les améliorations de l’analyse et du formatage des points flottants dans le billet de blog [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La section « Impact potentiel sur le code existant » des améliorations de l’analyse et du formatage des points flottants dans le billet de blog [.NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) suggère des modifications à votre code si vous observez un changement de comportement par rapport aux applications .NET Core 2.2 En général, cela implique l’utilisation d’une chaîne de format standard ou personnalisée différente pour appliquer le comportement souhaité. Certains résultats peuvent ne pas avoir une solution de contournement s’ils étaient auparavant incorrects.

#### <a name="category"></a>Category

Core .NET bibliothèques

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
