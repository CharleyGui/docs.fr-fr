---
ms.openlocfilehash: b01424c63d6e7956127bf889c53422b60ba2f219
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065155"
---
### <a name="ca2013-do-not-use-referenceequals-with-value-types"></a>CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur

La [règle de](/visualstudio/code-quality/ca2013) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tout code où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité.

#### <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2013](/visualstudio/code-quality/ca2013). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

La règle ca2013 recherche des instances où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité. La comparaison des types valeur pour l’égalité de cette façon peut entraîner des résultats incorrects, car les valeurs sont converties avant d’être comparées. <xref:System.Object.ReferenceEquals(System.Object,System.Object)> retourne `false` même si les valeurs comparées représentent la même instance d’un type valeur.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

- Modifiez le code pour utiliser un opérateur d’égalité approprié, tel que `==` . Vous ne devez pas supprimer cet avertissement.

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Category

Analyse du code

#### <a name="affected-apis"></a>API affectées

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

-->
