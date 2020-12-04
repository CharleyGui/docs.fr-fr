---
title: Analyse du code dans .NET
titleSuffix: ''
description: En savoir plus sur l’analyse du code source dans le kit de développement logiciel (SDK) .NET.
ms.date: 08/22/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: ca3a9cb914befbc8e0982070b818b27ee3143793
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "96588395"
---
# <a name="overview-of-net-source-code-analysis"></a>Vue d’ensemble de l’analyse du code source .NET

Les analyseurs .NET Compiler Platform (Roslyn) inspectent la qualité et les problèmes de styles de code de votre code C# ou Visual Basic. À compter de .NET 5.0, ces analyseurs sont inclus dans le kit de développement logiciel (SDK) .NET. (Précédemment, vous avez installé des analyseurs de qualité du code en tant que [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)et les analyseurs de style de code ont été installés avec Visual Studio.)

- [Analyse de la qualité du code (règles « CAXXXX »)](#code-quality-analysis)
- [Analyse de style de code (règles « IDExxxx »)](#code-style-analysis)

Si un analyseur détecte des violations de règle, celles-ci sont signalées sous la forme d’une suggestion, d’un avertissement ou d’une erreur, selon la façon dont chaque règle est [configurée](configuration-options.md). Les violations de l’analyse du code s’affichent avec le préfixe « CA » ou « IDE » pour les différencier des erreurs du compilateur.

> [!TIP]
>
> - Vous pouvez également installer des analyseurs tiers, tels que [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), les [analyseurs xUnit](https://www.nuget.org/packages/xunit.analyzers/)et l' [analyseur sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).
> - Si vous utilisez Visual Studio, de nombreuses règles de l’analyseur sont associées à des *correctifs de code* que vous pouvez appliquer pour corriger le problème. Les corrections de code s’affichent dans le menu de l’icône d’ampoule.

## <a name="code-quality-analysis"></a>Analyse de la qualité du code

Les règles d’analyse de la _qualité du code (« ca »)_ inspectent votre code C# ou Visual Basic pour la sécurité, les performances, la conception et d’autres problèmes. L’analyse est activée par défaut pour les projets qui ciblent .NET 5,0 ou une version ultérieure. Vous pouvez activer l’analyse du code sur des projets qui ciblent des versions antérieures de .NET en affectant à la propriété [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) la valeur `true` . Vous pouvez également désactiver l’analyse du code pour votre projet en affectant à la valeur `EnableNETAnalyzers` `false` .

> [!TIP]
> Dans Visual Studio, vous pouvez activer ou désactiver l’analyse du code à l’aide du Fenêtre Propriétés de projet. Pour accéder au Fenêtre Propriétés du projet, cliquez avec le bouton droit sur un projet dans Explorateur de solutions et sélectionnez **Propriétés**. Ensuite, sélectionnez l’onglet **analyse du code** , puis activez ou désactivez la case à cocher pour activer les **analyseurs .net**.

### <a name="enabled-rules"></a>Règles activées

Les règles suivantes sont activées par défaut dans .NET 5,0 Preview 8.

| ID de diagnostic | Category | Gravité | Description |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | Interopérabilité | Avertissement | Analyseur de compatibilité de plateforme |
| [CA1417](/visualstudio/code-quality/ca1417) | Interopérabilité | Avertissement | Ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour P/Invoke |
| [CA1831](/visualstudio/code-quality/ca1831) | Performances | Avertissement | Utilisez `AsSpan` à la place des indexeurs de plage pour la chaîne quand cela est approprié |
| [CA2013](/visualstudio/code-quality/ca2013) | Fiabilité | Avertissement | Ne pas utiliser `ReferenceEquals` avec les types valeur |
| [CA2014](/visualstudio/code-quality/ca2014) | Fiabilité | Avertissement | Ne pas utiliser `stackalloc` dans les boucles |
| [CA2015](/visualstudio/code-quality/ca2015) | Fiabilité | Avertissement | Ne définissez pas de finaliseurs pour les types dérivés de <xref:System.Buffers.MemoryManager%601> |
| [CA2200](/visualstudio/code-quality/ca2200) | Usage | Avertissement | Levez à nouveau une exception pour conserver les détails de la pile
| [CA2247](/visualstudio/code-quality/ca2247) | Usage | Avertissement | L’argument passé au constructeur TaskCompletionSource doit être <xref:System.Threading.Tasks.TaskCreationOptions> enum au lieu de <xref:System.Threading.Tasks.TaskContinuationOptions> |

Vous pouvez modifier la gravité de ces règles pour les désactiver ou les élever aux erreurs.

Pour obtenir la liste complète des règles de qualité du code disponibles, consultez [règles de qualité du code](quality-rules/index.md).

### <a name="enable-additional-rules"></a>Activer des règles supplémentaires

À compter de .NET 5,0 RC2, le kit de développement logiciel (SDK) .NET est fourni avec toutes les [règles de qualité du code « ca »](/visualstudio/code-quality/code-analysis-for-managed-code-warnings). Pour obtenir la liste complète des règles incluses avec chaque version du kit de développement logiciel (SDK) .NET, consultez [releases de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).

#### <a name="default-analysis-mode"></a>Mode d’analyse par défaut

Dans le mode d’analyse par défaut, certaines règles sont [activées par défaut](#enabled-rules) en tant qu’avertissements de génération. Certaines autres règles sont activées par défaut uniquement en tant que suggestions de l’IDE Visual Studio avec les corrections de code correspondantes. Les règles restantes sont désactivées par défaut. La [liste complète des règles](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md) comprend la gravité par défaut de chaque règle et indique si la règle est activée par défaut dans le mode d’analyse par défaut.

#### <a name="custom-analysis-mode"></a>Mode d’analyse personnalisée

Vous pouvez [configurer des règles d’analyse du code](configuration-options.md) pour activer ou désactiver une règle individuelle ou une catégorie de règles. En outre, vous pouvez utiliser la propriété [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) pour basculer vers l’un des modes d’analyse personnalisés suivants :

- Mode _agressif_ ou _opt-out_ : toutes les règles sont activées par défaut en tant qu’avertissements de génération. Vous pouvez [choisir](configuration-options.md) de désactiver les règles individuelles de manière sélective pour les désactiver.
- Mode _conservateur_ ou _opt-in_ : toutes les règles sont désactivées par défaut. Vous pouvez [choisir](configuration-options.md) des règles individuelles pour les activer.

### <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Si vous utilisez l' `-warnaserror` indicateur lorsque vous générez vos projets, tous les avertissements de l’analyse du code sont également traités comme des erreurs. Si vous ne souhaitez pas que les avertissements de qualité du code (CAXXXX) soient traités comme des erreurs en présence de `-warnaserror` , vous pouvez définir la `CodeAnalysisTreatWarningsAsErrors` propriété MSBuild sur `false` dans votre fichier projet.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

Vous verrez toujours les avertissements liés à l’analyse du code, mais ils ne perturberont pas votre génération.

### <a name="latest-updates"></a>Dernières mises à jour

Par défaut, vous obtiendrez les dernières règles d’analyse du code et les gravités de règle par défaut lors de la mise à niveau vers des versions plus récentes du kit de développement logiciel (SDK) .NET. Si vous ne souhaitez pas ce comportement, par exemple, si vous souhaitez vous assurer qu’aucune nouvelle règle n’est activée ou désactivée, vous pouvez la remplacer de l’une des manières suivantes :

- Affectez à la `AnalysisLevel` propriété MSBuild une valeur spécifique pour verrouiller les avertissements à cet ensemble. Lorsque vous effectuez une mise à niveau vers un kit de développement logiciel (SDK) plus récent, vous obtenez toujours des correctifs de bogues pour ces avertissements, mais aucun nouvel avertissement n’est activé et aucun avertissement existant n’est désactivé. Par exemple, pour verrouiller l’ensemble de règles pour celles fournies avec la version 5,0 du kit de développement logiciel (SDK) .NET, ajoutez l’entrée suivante à votre fichier projet.

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > La valeur par défaut de la `AnalysisLevel` propriété est `latest` , ce qui signifie que vous recevez toujours les dernières règles d’analyse du code à mesure que vous passez à des versions plus récentes du kit de développement logiciel (SDK) .net.

  Pour plus d’informations et pour afficher une liste des valeurs possibles, consultez [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).

- Installez le [package NuGet Microsoft. CodeAnalysis. Netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) pour découpler les mises à jour des règles des mises à jour du kit de développement logiciel (SDK) .net. L’installation du package désactive les analyseurs SDK intégrés et génère un avertissement de génération si le kit de développement logiciel (SDK) contient une version d’assembly d’analyseur plus récente que celle du package NuGet.

## <a name="code-style-analysis"></a>Analyse de style de code

L' [analyse de style de code](/visualstudio/ide/editorconfig-code-style-settings-reference) (règles « IDExxxx ») vous permet de définir et de maintenir un style de code cohérent dans votre base de code. Les paramètres par défaut sont les suivants :

- Génération de la ligne de commande : l’analyse du style de code est désactivée, par défaut, pour tous les projets .NET sur les générations à partir de la ligne de commande.
- Visual Studio : l’analyse de style de code est activée, par défaut, pour tous les projets .NET dans Visual Studio en tant que [actions rapides de refactorisation de code](/visualstudio/ide/code-generation-in-visual-studio).

À partir de .NET 5,0 RC2, vous pouvez activer l’analyse de style de code sur la build, à la fois sur la ligne de commande et dans Visual Studio. Les violations de style de code apparaissent sous la forme d’avertissements ou d’erreurs avec un préfixe « IDE ». Cela vous permet d’appliquer des styles de code cohérents au moment de la génération.

> [!NOTE]
> La fonctionnalité d’analyse de style de code est expérimentale et peut changer entre les versions .NET 5 et .NET 6.

Étapes pour activer l’analyse de style de code sur la build :

1. Affectez à la propriété MSBuild [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) la valeur `true` .

1. Dans un fichier *. editorconfig* , [configurez](configuration-options.md) chaque règle de style de code « IDE » que vous souhaitez exécuter lors de la génération comme un avertissement ou une erreur. Par exemple :

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   Vous pouvez également configurer la catégorie « style » entière comme un avertissement ou une erreur, par défaut, puis désactiver de manière sélective les règles que vous ne souhaitez pas exécuter lors de la génération. Par exemple :

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

## <a name="suppress-a-warning"></a>Supprimer un avertissement

Pour supprimer une violation de règle, définissez l’option de gravité de cet ID de règle sur `none` dans un fichier EditorConfig. Par exemple :

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio fournit des méthodes supplémentaires pour supprimer les avertissements des règles d’analyse du code. Pour plus d’informations, consultez [Supprimer les violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).

Pour plus d’informations sur les niveaux de gravité de la règle, consultez [configurer la gravité](configuration-options.md#severity-level)de la règle.

## <a name="see-also"></a>Voir aussi

- [Référence de règle d’analyse de la qualité du code](quality-rules/index.md)
- [Référence de règle d’analyse de style de code](style-rules/index.md)
- [Analyse du code dans Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview)
- [SDK .NET Compiler Platform](../../csharp/roslyn-sdk/index.md)
- [Tutoriel : Écrire votre premier analyseur et correctif de code](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
