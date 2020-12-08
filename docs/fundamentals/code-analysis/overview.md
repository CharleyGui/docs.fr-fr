---
title: Analyse du code dans .NET
titleSuffix: ''
description: En savoir plus sur l’analyse du code source dans le kit de développement logiciel (SDK) .NET.
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 657975742c3efc2985264fe16cb316357b959e73
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851814"
---
# <a name="overview-of-net-source-code-analysis"></a>Vue d’ensemble de l’analyse du code source .NET

Les analyseurs .NET Compiler Platform (Roslyn) inspectent la qualité et les problèmes de styles de code de votre code C# ou Visual Basic. À compter de .NET 5,0, ces analyseurs sont inclus dans le kit de développement logiciel (SDK) .NET et vous n’avez pas besoin de les installer séparément. Si votre projet cible .NET 5 ou une version ultérieure, l’analyse du code est activée par défaut. Si votre projet cible une implémentation .NET différente, par exemple, .NET Core, .NET Standard ou .NET Framework, vous devez activer manuellement l’analyse du code en affectant à la propriété [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) la valeur `true` .

Si vous ne souhaitez pas migrer vers le kit de développement logiciel (SDK) .NET 5 + ou si vous préférez un modèle basé sur un package NuGet, les analyseurs sont également disponibles dans le [package NuGet Microsoft. CodeAnalysis. Netanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Vous préférerez peut-être un modèle basé sur des packages pour les mises à jour de version à la demande.

> [!NOTE]
> Les analyseurs .NET sont agnostiques au Framework cible. Autrement dit, votre projet n’a pas besoin de cibler une implémentation spécifique de .NET. Les analyseurs fonctionnent pour les projets qui ciblent `net5.0` et les versions antérieures de .net, telles que `netcoreapp3.1` et `net472` .

Si un analyseur détecte des violations de règle, celles-ci sont signalées sous la forme d’une suggestion, d’un avertissement ou d’une erreur, selon la façon dont chaque règle est [configurée](configuration-options.md). Les violations de l’analyse du code s’affichent avec le préfixe « CA » ou « IDE » pour les différencier des erreurs du compilateur.

## <a name="code-quality-analysis"></a>Analyse de la qualité du code

Les règles d’analyse de la *qualité du code* (« CAXXXX ») inspectent votre code C# ou Visual Basic pour la sécurité, les performances, la conception et d’autres problèmes. L’analyse est activée par défaut pour les projets qui ciblent .NET 5,0 ou une version ultérieure. Vous pouvez activer l’analyse du code sur des projets qui ciblent des versions antérieures de .NET en affectant à la propriété [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) la valeur `true` . Vous pouvez également désactiver l’analyse du code pour votre projet en affectant à la valeur `EnableNETAnalyzers` `false` .

> [!TIP]
> Si vous utilisez Visual Studio :
>
> - De nombreuses règles de l’analyseur sont associées à des *correctifs de code* que vous pouvez appliquer pour corriger le problème. Les corrections de code s’affichent dans le menu de l’icône d’ampoule.
> - Vous pouvez activer ou désactiver l’analyse du code en cliquant avec le bouton droit sur un projet dans Explorateur de solutions et en sélectionnant **Propriétés**  >  onglet **analyse du code** > activer les **analyseurs .net**.

### <a name="enabled-rules"></a>Règles activées

Les règles suivantes sont activées par défaut dans .NET 5,0.

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

Vous pouvez modifier la gravité de ces règles pour les désactiver ou les élever aux erreurs. Vous pouvez également [activer davantage de règles](#enable-additional-rules).

- Pour obtenir la liste des règles incluses avec chaque version du kit de développement logiciel (SDK) .NET, consultez [releases de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).
- Pour obtenir la liste de toutes les règles de qualité du code, consultez [règles de qualité du code](quality-rules/index.md).

### <a name="enable-additional-rules"></a>Activer des règles supplémentaires

Le *mode d’analyse* fait référence à une configuration d’analyse du code prédéfinie dans laquelle aucune, une partie ou l’ensemble des règles n’est activée. Dans le mode d’analyse par défaut, seul un petit nombre de règles est [activé en tant qu’avertissements de génération](#enabled-rules). Vous pouvez modifier le mode d’analyse de votre projet en définissant la propriété [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) dans le fichier projet. Les valeurs autorisées sont les suivantes :

| Valeur | Description |
| - | - |
| `AllDisabledByDefault` | Il s’agit du mode le plus conservateur. Toutes les règles sont désactivées par défaut. Vous pouvez [choisir](configuration-options.md) des règles individuelles pour les activer.<br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | Il s’agit du mode le plus agressif. Toutes les règles sont activées en tant qu’avertissements de Build. Vous pouvez [choisir de](configuration-options.md) désactiver les règles individuelles de manière sélective pour les désactiver.<br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | Le mode par défaut, dans lequel quelques règles sont activées en tant qu’avertissements, les autres sont uniquement activées en tant que suggestions de l’IDE Visual Studio avec les correctifs de code correspondants, et les autres sont désactivés complètement. Vous pouvez [choisir d’accepter ou de refuser des](configuration-options.md) règles individuelles pour les désactiver.<br /><br />`<AnalysisMode>Default</AnalysisMode>` |

Pour connaître la gravité par défaut de chaque règle disponible et indiquer si la règle est activée ou non dans le mode d’analyse par défaut, consultez la [liste complète des règles](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).

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

Les règles d' *analyse de style de code* (« IDExxxx ») vous permettent de définir et de maintenir un style de code cohérent dans votre base de code. Les paramètres d’activation par défaut sont les suivants :

- Génération de la ligne de commande : l’analyse du style de code est désactivée, par défaut, pour tous les projets .NET sur les générations à partir de la ligne de commande.
- Visual Studio : l’analyse de style de code est activée, par défaut, pour tous les projets .NET dans Visual Studio en tant que [actions rapides de refactorisation de code](/visualstudio/ide/code-generation-in-visual-studio).

À partir de .NET 5,0, vous pouvez activer l’analyse de style de code sur la build, à la fois sur la ligne de commande et dans Visual Studio. Les violations de style de code apparaissent sous la forme d’avertissements ou d’erreurs avec un préfixe « IDE ». Cela vous permet d’appliquer des styles de code cohérents au moment de la génération.

Pour obtenir la liste complète des règles d’analyse de style code, consultez [règles de style de code](style-rules/index.md).

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

## <a name="third-party-analyzers"></a>Analyseurs tiers

En plus des analyseurs .NET officiels, vous pouvez également installer des analyseurs tiers, tels que [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), les [analyseurs xUnit](https://www.nuget.org/packages/xunit.analyzers/)et l' [Analyseur de sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="see-also"></a>Voir aussi

- [Référence de règle d’analyse de la qualité du code](quality-rules/index.md)
- [Référence de règle d’analyse de style de code](style-rules/index.md)
- [Analyse du code dans Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview)
- [SDK .NET Compiler Platform](../../csharp/roslyn-sdk/index.md)
- [Tutoriel : Écrire votre premier analyseur et correctif de code](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
