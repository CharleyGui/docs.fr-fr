---
title: 'Modification avec rupture : ca2013 : n’utilisez pas ReferenceEquals avec les types valeur'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca2013.
ms.date: 09/03/2020
ms.openlocfilehash: ca2b845427eff547b996b577394c6859e30f50bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760816"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a>AVERTISSEMENT ca2013 : n’utilisez pas ReferenceEquals avec les types valeur

La [règle de](/visualstudio/code-quality/ca2013) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tout code où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité.

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées par défaut, y compris [ca2013](/visualstudio/code-quality/ca2013). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

La règle ca2013 recherche des instances où <xref:System.Object.ReferenceEquals(System.Object,System.Object)> est utilisé pour comparer un ou plusieurs types valeur pour l’égalité. La comparaison des types valeur pour l’égalité de cette façon peut entraîner des résultats incorrects, car les valeurs sont converties avant d’être comparées. <xref:System.Object.ReferenceEquals(System.Object,System.Object)> retourne `false` même si les valeurs comparées représentent la même instance d’un type valeur.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Modifiez le code pour utiliser un opérateur d’égalité approprié, tel que `==` . Vous ne devez pas supprimer cet avertissement.

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
