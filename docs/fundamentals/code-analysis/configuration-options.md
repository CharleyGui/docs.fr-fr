---
title: Configurer les règles d’analyse du code
description: Découvrez comment configurer des règles d’analyse du code dans un fichier de configuration de l’analyseur.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0687bcb16cae6a0a2dde6c7864a1af1d0027e122
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216458"
---
# <a name="configuration-options-for-code-analysis"></a>Options de configuration pour l’analyse du code

Les règles d’analyse du code ont plusieurs options de configuration. Ces options sont spécifiées en tant que paires clé-valeur dans un [fichier de configuration d’analyseur](configuration-files.md) à l’aide de la syntaxe `<option key> = <option value>` .

L’option la plus courante que vous configurez est la [gravité d’une règle](#severity-level). Vous pouvez configurer le niveau de gravité pour toutes les règles de l’analyseur, y compris les règles de [qualité du code](quality-rules/index.md) et les règles de [style de code](style-rules/index.md). Par exemple, pour activer une règle en tant qu’avertissement, vous pouvez ajouter la paire clé-valeur suivante à un EditorConfig fichier.

`dotnet_diagnostic.<rule ID>.severity = warning`

Vous pouvez également configurer des options supplémentaires pour personnaliser le comportement de la règle :

- Les règles de qualité du code comportent [des options supplémentaires](code-quality-rule-options.md) pour configurer le comportement, telles que les noms des méthodes auxquelles une règle doit s’appliquer.
- Les règles de style de code ont des [options de style de code personnalisées](code-style-rule-options.md).
- Les règles de l’analyseur tiers peuvent définir leurs propres options de configuration, avec des noms de clé personnalisés et des formats de valeur.

La syntaxe de configuration de la gravité d’une règle spécifique dans un fichier de configuration de l' [analyseur](configuration-files.md) est la suivante :

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a>Options générales

Ces options s’appliquent à l’analyse du code dans son ensemble. Ils ne peuvent pas être appliqués uniquement à une seule règle ou à un ensemble de règles.

### <a name="exclude-generated-code"></a>Exclure le code généré

Vous pouvez configurer d’autres fichiers et dossiers à traiter comme du code généré en ajoutant une `generated_code = true | false` entrée à votre [fichier de configuration](configuration-files.md). Les avertissements de l’analyseur de code .NET ne sont pas utiles pour les fichiers de code générés, tels que les fichiers générés par le concepteur, que les utilisateurs ne peuvent pas modifier pour corriger les violations. Dans la plupart des cas, les analyseurs de code ignorent les fichiers de code générés et ne signalent pas de violations sur ces fichiers.

Par défaut, les fichiers avec des extensions de fichier ou des en-têtes de fichiers générés automatiquement sont traités comme des fichiers de code générés. Par exemple, un nom de fichier se terminant par `.designer.cs` ou `.generated.cs` est considéré comme du code généré. Cette option de configuration vous permet de spécifier des modèles de nommage supplémentaires.

Par exemple, pour traiter tous les fichiers dont le nom se termine par `.MyGenerated.cs` comme code généré, ajoutez l’entrée suivante :

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a>Options spécifiques à la règle

Les options spécifiques aux règles peuvent être appliquées à une seule règle, à un ensemble de règles ou à toutes les règles. Les options spécifiques à la règle sont les suivantes :

- [Niveau de gravité de la règle](#severity-level)
- [Options spécifiques aux règles de *qualité du code*](code-quality-rule-options.md)

### <a name="severity-level"></a>Niveau de gravité

Le tableau suivant présente les différents types de gravité de règle que vous pouvez configurer pour toutes les règles de l’analyseur, y compris la [qualité du code](quality-rules/index.md) et les règles de [style de code](style-rules/index.md) .

| Gravité | Comportement au moment de la génération |
|-|-|
| `error` | Les violations apparaissent comme des *Erreurs* de build et entraînent l’échec des builds.|
| `warning` | Les violations apparaissent en tant qu' *avertissements* de build, mais ne provoquent pas l’échec des builds (sauf si vous avez une option définie pour traiter les avertissements comme des erreurs). |
| `suggestion` | Les violations s’affichent sous la forme de *messages* de génération et sous forme de suggestions dans l’IDE de Visual Studio. |
| `silent` | Les violations ne sont pas visibles pour l’utilisateur. |
| `none` | La règle est entièrement supprimée. |
| `default` | La gravité par défaut de la règle est utilisée. |

> [!TIP]
> Pour plus d’informations sur la façon dont les niveaux de gravité de la règle s’affichent dans Visual Studio, consultez [niveaux de gravité](/visualstudio/ide/editorconfig-language-conventions#severity-levels).

#### <a name="scope"></a>Étendue

Pour définir la gravité de la règle pour une seule règle, utilisez la syntaxe suivante.

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

Pour définir la gravité de la règle par défaut pour une catégorie de règles d’analyseur, utilisez la syntaxe suivante. La catégorie de chaque règle est fournie dans les pages de référence de règle individuelles, par exemple, [CA1000](quality-rules/ca1000.md).

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

Pour définir la gravité de la règle par défaut pour toutes les règles de l’analyseur, utilisez la syntaxe suivante.

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a>Priorité

Si vous avez plusieurs entrées de configuration de gravité qui peuvent être appliquées au même ID de règle, la priorité est choisie dans l’ordre suivant :

- Une entrée pour une règle individuelle par ID est prioritaire sur une entrée pour une catégorie.
- Une entrée pour une catégorie est prioritaire sur une entrée pour toutes les règles de l’analyseur.

Prenons l’exemple suivant, où [CA1822](/visualstudio/code-quality/ca1822) a la catégorie « performance » :

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

Dans l’exemple précédent, les trois entrées de gravité sont applicables à CA1822. Toutefois, à l’aide des règles de précédence spécifiées, la première entrée basée sur l’ID de règle gagne sur les entrées suivantes. Dans cet exemple, CA1822 aura une gravité effective de `error` . Toutes les autres règles de la catégorie « performance » auront une gravité de `warning` .

Pour plus d’informations sur la façon dont la précédence entre fichiers est décidée, consultez la [section priorité de l’article fichiers de configuration](configuration-files.md#precedence).
