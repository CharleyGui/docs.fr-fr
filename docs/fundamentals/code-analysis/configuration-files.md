---
title: Fichiers de configuration pour les règles d’analyse du code
description: Découvrez les différents fichiers de configuration permettant de configurer les règles d’analyse du code.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: b98fdd48f2373bd23fcd3273834860a60c682969
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216380"
---
# <a name="configuration-files-for-code-analysis-rules"></a>Fichiers de configuration pour les règles d’analyse du code

Les règles d’analyse du code ont plusieurs [options de configuration](configuration-options.md). Vous spécifiez ces options en tant que paires clé-valeur dans l’un des fichiers de configuration de l’analyseur suivants :

- [EditorConfig](#editorconfig) fichier : options de configuration basées sur un fichier ou sur un dossier.
- Fichier [Global AnalyzerConfig](#global-analyzerconfig) : options de configuration au niveau du projet. Utile lorsque certains fichiers projet résident à l’extérieur du dossier du projet.

## EditorConfig

[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) les fichiers sont utilisés pour fournir **des options qui s’appliquent à des fichiers ou des dossiers sources spécifiques**. Les options sont placées sous les en-têtes de section pour identifier les fichiers et dossiers applicables. Ajoutez une entrée pour chaque règle que vous souhaitez configurer, puis placez-la sous la section d’extension de fichier correspondante, par exemple `[*.cs]` .

```ini
[*.cs]
<option_name> = <option_value>
```

Dans l’exemple ci-dessus, `[*.cs]` est un en-tête de section editorconfig pour sélectionner tous les fichiers C# avec `.cs` l’extension de fichier dans le dossier actif, y compris les sous-dossiers. L’entrée suivante, `<option_name> = <option_value>` , est une option d’analyseur qui sera appliquée à tous les fichiers C#.

Vous pouvez appliquer des EditorConfig conventions de fichiers à un dossier, à un projet ou à un référentiel entier en plaçant le fichier dans le répertoire correspondant. Ces options sont appliquées lors de l’exécution de l’analyse au moment de la génération et Pendant la modification du code dans Visual Studio.

Si vous avez un fichier *. editorconfig* existant pour les paramètres de l’éditeur tels que la taille du retrait ou si vous souhaitez supprimer les espaces de fin, vous pouvez placer les options de configuration de l’analyse du code dans le même fichier.

> [!TIP]
> Visual Studio fournit un modèle d’élément *. editorconfig* qui facilite l’ajout de l’un de ces fichiers à votre projet. Pour plus d’informations, consultez [Ajouter un EditorConfig fichier à un projet](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

### <a name="example"></a>Exemple

Voici un exemple EditorConfig de fichier permettant de configurer les options et la gravité de la règle :

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a>AnalyzerConfig global

À compter du kit de développement logiciel (SDK) .NET 5 (qui est pris en charge dans Visual Studio 2019 version 16,8 et versions ultérieures), vous pouvez également configurer des options d’analyseur avec des fichiers _AnalyzerConfig_ globaux. Ces fichiers sont utilisés pour fournir des **options qui s’appliquent à tous les fichiers sources d’un projet**, quels que soient leur nom de fichier ou leur chemin d’accès.

Contrairement aux [EditorConfig](#editorconfig) fichiers, les fichiers de configuration globaux ne peuvent pas être utilisés pour configurer les paramètres de style de l’éditeur pour les IDE, tels que la taille du retrait ou la suppression des espaces blancs de fin. Au lieu de cela, ils sont conçus exclusivement pour spécifier les options de configuration de l’analyseur au niveau du projet.

### <a name="format"></a>Format

Contrairement aux EditorConfig fichiers, qui doivent avoir des en-têtes de section, tels que `[*.cs]` , pour identifier les fichiers et dossiers applicables, les fichiers AnalyzerConfig globaux n’ont pas d’en-tête de section. Au lieu de cela, ils nécessitent une entrée de niveau supérieur du formulaire `is_global = true` pour les différencier des EditorConfig fichiers normaux. Cela indique que toutes les options dans le fichier s’appliquent à l’ensemble du projet. Par exemple :

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a>Dénomination

Contrairement aux EditorConfig fichiers, qui doivent être nommés `.editorconfig` , les fichiers de configuration globaux n’ont pas besoin d’avoir un nom ou une extension spécifique. Toutefois, si vous nommez ces fichiers, `.globalconfig` ils sont implicitement appliqués à tous les projets C# et Visual Basic dans le dossier actif, y compris les sous-dossiers. Sinon, vous devez ajouter explicitement l' `GlobalAnalyzerConfigFiles` élément à votre fichier projet MSBuild :

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> L’entrée de niveau supérieur `is_global = true` est requise même si le fichier est nommé `.globalconfig` .

### <a name="example"></a>Exemple

Voici un exemple de fichier AnalyzerConfig global permettant de configurer les options et la gravité de la règle au niveau du projet :

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a>Priorité

Les fichiers EditorConfig et les fichiers AnalyzerConfig globaux spécifient une paire clé-valeur pour chaque option. Des conflits se produisent quand il existe plusieurs entrées avec la même clé mais des valeurs différentes.

### <a name="general-options"></a>Options générales

Lorsque des conflits se produisent entre les options, les règles de précédence suivantes sont utilisées pour résoudre les conflits :

- Entrées en conflit dans le même fichier de configuration : l’entrée qui apparaît ultérieurement dans le fichier gagne. Cela est vrai pour les entrées en conflit dans un EditorConfig fichier unique et également dans un fichier AnalyzerConfig global unique.

- Entrées en conflit dans deux EditorConfig fichiers : l’entrée dans le EditorConfig fichier qui est plus profonde dans le système de fichiers et, par conséquent, a un chemin d’accès de fichier plus long, WINS.

- Entrées en conflit dans deux fichiers AnalyzerConfig globaux : un avertissement du compilateur est signalé et les deux entrées sont ignorées.

- Entrées en conflit dans un EditorConfig fichier et un fichier AnalyzerConfig global : l’entrée dans le EditorConfig fichier gagne.

### <a name="severity-options"></a>Options de gravité

Les [règles de précédence générales](#general-options) précédentes s’appliquent à toutes les options spécifiées dans les fichiers de configuration. Pour les options de [configuration de gravité](configuration-options.md#severity-level) , les règles de précédence supplémentaires suivantes s’appliquent :

- Les options de gravité spécifiées sur la ligne de commande en tant qu’options du compilateur ( `/nowarn` ou `/warnaserror` ) remplacent toujours les options de [configuration de gravité](configuration-options.md#severity-level) spécifiées dans EditorConfig et les fichiers Global AnalyzerConfig.

- Les options de gravité peuvent également être spécifiées avec un fichier [RuleSet](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) . Toutefois, les fichiers RuleSet sont dépréciés en faveur des EditorConfig fichiers AnalyzerConfig globaux et. Il est recommandé de [convertir les fichiers de l’ensemble de règles en un EditorConfig fichier équivalent](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file). La priorité des entrées de gravité conflictuelles d’un fichier RuleSet et de EditorConfig fichiers AnalyzerConfig globaux n’est _pas définie_.

- Pour plus d’informations sur les règles de précédence pour les options de gravité associées avec des clés différentes, par exemple, lorsque différents niveaux de gravité sont spécifiés pour une seule règle et pour la catégorie dans laquelle la règle se trouve, consultez [options de configuration pour l’analyse du code](configuration-options.md#precedence).

## <a name="see-also"></a>Voir aussi

- [EditorConfig problème de conception de AnalyzerConfig global vs](https://github.com/dotnet/roslyn/issues/47707)
