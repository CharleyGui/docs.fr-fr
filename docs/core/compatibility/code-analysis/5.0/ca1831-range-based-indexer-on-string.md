---
title: 'Modification avec rupture : CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour une chaîne'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code CA1831.
ms.date: 08/21/2020
ms.openlocfilehash: 850916b804ae29dba8d2bd05c6e4fb06fe667296
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437886"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a>AVERTISSEMENT CA1831 : utiliser AsSpan à la place d’indexeurs basés sur une plage pour une chaîne

La règle de l’analyseur de code .NET [CA1831](/visualstudio/code-quality/ca1831) est activée, par défaut, à partir de .net 5,0. Il génère un avertissement de génération pour tout code où un <xref:System.Range> indexeur de based est utilisé sur une chaîne, mais aucune copie n’était prévue.

## <a name="change-description"></a>Description de la modification

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md). Plusieurs de ces règles sont activées, par défaut, y compris [CA1831](/visualstudio/code-quality/ca1831). Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.

La règle CA1831 trouve des instances où un <xref:System.Range> indexeur de base est utilisé sur une chaîne, mais qu’aucune copie n’était prévue. Si l' <xref:System.Range> indexeur de base est utilisé directement sur une chaîne pour produire un cast implicite, une copie inutile de la partie demandée de la chaîne est créée. Par exemple :

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

CA1831 suggère d’utiliser à la <xref:System.Range> place l’indexeur basé sur une *étendue* de la chaîne. Par exemple :

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

- Pour corriger votre code et éviter les allocations inutiles, appelez <xref:System.MemoryExtensions.AsSpan(System.String)> ou <xref:System.MemoryExtensions.AsMemory(System.String)> avant d’utiliser l' <xref:System.Range> indexeur basé sur. Par exemple :

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- Si vous ne souhaitez pas modifier votre code, vous pouvez désactiver la règle en affectant à sa gravité la valeur `suggestion` ou `none` . Pour plus d’informations, consultez [configurer des règles d’analyse du code](../../../../fundamentals/code-analysis/configuration-options.md).

- Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet. Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>API affectées

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
