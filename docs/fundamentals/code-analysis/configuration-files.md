---
title: Fichiers de configuration pour les règles d’analyse du code
description: Découvrez les différents fichiers de configuration permettant de configurer les règles d’analyse du code.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: cf9b8f4033e6774684b2b7e3b788ef3c157d95df
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96588671"
---
# <a name="configuration-files-for-code-analysis-rules"></a><span data-ttu-id="e87a7-103">Fichiers de configuration pour les règles d’analyse du code</span><span class="sxs-lookup"><span data-stu-id="e87a7-103">Configuration files for code analysis rules</span></span>

<span data-ttu-id="e87a7-104">Les règles d’analyse du code ont plusieurs [options de configuration](configuration-options.md).</span><span class="sxs-lookup"><span data-stu-id="e87a7-104">Code analysis rules have various [configuration options](configuration-options.md).</span></span> <span data-ttu-id="e87a7-105">Vous spécifiez ces options en tant que paires clé-valeur dans l’un des fichiers de configuration de l’analyseur suivants :</span><span class="sxs-lookup"><span data-stu-id="e87a7-105">You specify these options as key-value pairs in one of the following analyzer configuration files:</span></span>

- <span data-ttu-id="e87a7-106">[EditorConfig](#editorconfig) fichier : options de configuration basées sur un fichier ou sur un dossier.</span><span class="sxs-lookup"><span data-stu-id="e87a7-106">[EditorConfig](#editorconfig) file: File-based or folder-based configuration options.</span></span>
- <span data-ttu-id="e87a7-107">Fichier [Global AnalyzerConfig](#global-analyzerconfig) : options de configuration au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="e87a7-107">[Global AnalyzerConfig](#global-analyzerconfig) file: Project-level configuration options.</span></span>

## EditorConfig

<span data-ttu-id="e87a7-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) les fichiers sont utilisés pour fournir **des options qui s’appliquent à des fichiers ou des dossiers sources spécifiques**.</span><span class="sxs-lookup"><span data-stu-id="e87a7-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) files are used to provide **options that apply to specific source files or folders**.</span></span> <span data-ttu-id="e87a7-109">Les options sont placées sous les en-têtes de section pour identifier les fichiers et dossiers applicables.</span><span class="sxs-lookup"><span data-stu-id="e87a7-109">Options are placed under section headers to identify the applicable files and folders.</span></span> <span data-ttu-id="e87a7-110">Ajoutez une entrée pour chaque règle que vous souhaitez configurer, puis placez-la sous la section d’extension de fichier correspondante, par exemple `[*.cs]` .</span><span class="sxs-lookup"><span data-stu-id="e87a7-110">Add an entry for each rule you want to configure, and place it under the corresponding file extension section, for example, `[*.cs]`.</span></span>

```ini
[*.cs]
<option_name> = <option_value>
```

<span data-ttu-id="e87a7-111">Dans l’exemple ci-dessus, `[*.cs]` est un en-tête de section editorconfig pour sélectionner tous les fichiers C# avec `.cs` l’extension de fichier dans le dossier actif, y compris les sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="e87a7-111">In the above example, `[*.cs]` is an editorconfig section header to select all C# files with `.cs` file extension within the current folder, including subfolders.</span></span> <span data-ttu-id="e87a7-112">L’entrée suivante, `<option_name> = <option_value>` , est une option d’analyseur qui sera appliquée à tous les fichiers C#.</span><span class="sxs-lookup"><span data-stu-id="e87a7-112">The subsequent entry, `<option_name> = <option_value>`, is an analyzer option that will be applied to all the C# files.</span></span>

<span data-ttu-id="e87a7-113">Vous pouvez appliquer des EditorConfig conventions de fichiers à un dossier, à un projet ou à un référentiel entier en plaçant le fichier dans le répertoire correspondant.</span><span class="sxs-lookup"><span data-stu-id="e87a7-113">You can apply EditorConfig file conventions to a folder, a project, or an entire repo by placing the file in the corresponding directory.</span></span> <span data-ttu-id="e87a7-114">Ces options sont appliquées lors de l’exécution de l’analyse au moment de la génération et Pendant la modification du code dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e87a7-114">These options are applied when executing the analysis at build time and while you edit code in Visual Studio.</span></span>

<span data-ttu-id="e87a7-115">Si vous avez un fichier *. editorconfig* existant pour les paramètres de l’éditeur tels que la taille du retrait ou si vous souhaitez supprimer les espaces de fin, vous pouvez placer les options de configuration de l’analyse du code dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="e87a7-115">If you have an existing *.editorconfig* file for editor settings such as indent size or whether to trim trailing whitespace, you can place your code analysis configuration options in the same file.</span></span>

> [!TIP]
> <span data-ttu-id="e87a7-116">Visual Studio fournit un modèle d’élément *. editorconfig* qui facilite l’ajout de l’un de ces fichiers à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e87a7-116">Visual Studio provides an *.editorconfig* item template that makes is easy to add one of these files to your project.</span></span> <span data-ttu-id="e87a7-117">Pour plus d’informations, consultez [Ajouter un EditorConfig fichier à un projet](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span><span class="sxs-lookup"><span data-stu-id="e87a7-117">For more information, see [Add an EditorConfig file to a project](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span></span>

### <a name="example"></a><span data-ttu-id="e87a7-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e87a7-118">Example</span></span>

<span data-ttu-id="e87a7-119">Voici un exemple EditorConfig de fichier permettant de configurer les options et la gravité de la règle :</span><span class="sxs-lookup"><span data-stu-id="e87a7-119">Following is an example EditorConfig file to configure options and rule severity:</span></span>

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
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a><span data-ttu-id="e87a7-120">AnalyzerConfig global</span><span class="sxs-lookup"><span data-stu-id="e87a7-120">Global AnalyzerConfig</span></span>

<span data-ttu-id="e87a7-121">À compter du kit de développement logiciel (SDK) .NET 5,0 (qui est pris en charge dans Visual Studio 2019 version 16,8 et versions ultérieures), vous pouvez également configurer des options d’analyseur avec des fichiers _AnalyzerConfig_ globaux.</span><span class="sxs-lookup"><span data-stu-id="e87a7-121">Starting with the .NET 5.0 SDK (which is supported in Visual Studio 2019 version 16.8 and later versions), you can also configure analyzer options with global _AnalyzerConfig_ files.</span></span> <span data-ttu-id="e87a7-122">Ces fichiers sont utilisés pour fournir des **options qui s’appliquent à tous les fichiers sources d’un projet**, quels que soient leur nom de fichier ou leur chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="e87a7-122">These files are used to provide **options that apply to all the source files in a project**, regardless of their file names or file paths.</span></span>

<span data-ttu-id="e87a7-123">Contrairement aux [EditorConfig](#editorconfig) fichiers, les fichiers de configuration globaux ne peuvent pas être utilisés pour configurer les paramètres de style de l’éditeur pour les IDE, tels que la taille du retrait ou la suppression des espaces blancs de fin.</span><span class="sxs-lookup"><span data-stu-id="e87a7-123">Unlike [EditorConfig](#editorconfig) files, global config files can't be used to configure editor style settings for IDEs, such as indent size or whether to trim trailing whitespace.</span></span> <span data-ttu-id="e87a7-124">Au lieu de cela, ils sont conçus exclusivement pour spécifier les options de configuration de l’analyseur au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="e87a7-124">Instead, they are designed purely for specifying project-level analyzer configuration options.</span></span>

### <a name="format"></a><span data-ttu-id="e87a7-125">Format</span><span class="sxs-lookup"><span data-stu-id="e87a7-125">Format</span></span>

<span data-ttu-id="e87a7-126">Contrairement aux EditorConfig fichiers, qui doivent avoir des en-têtes de section, tels que `[*.cs]` , pour identifier les fichiers et dossiers applicables, les fichiers AnalyzerConfig globaux n’ont pas d’en-tête de section.</span><span class="sxs-lookup"><span data-stu-id="e87a7-126">Unlike EditorConfig files, which must have section headers, such as `[*.cs]`, to identify the applicable files and folders, global AnalyzerConfig files don't have section headers.</span></span> <span data-ttu-id="e87a7-127">Au lieu de cela, ils nécessitent une entrée de niveau supérieur du formulaire `is_global = true` pour les différencier des EditorConfig fichiers normaux.</span><span class="sxs-lookup"><span data-stu-id="e87a7-127">Instead, they require a top level entry of the form `is_global = true` to differentiate them from regular EditorConfig files.</span></span> <span data-ttu-id="e87a7-128">Cela indique que toutes les options dans le fichier s’appliquent à l’ensemble du projet.</span><span class="sxs-lookup"><span data-stu-id="e87a7-128">This indicates that all the options in the file apply to the entire project.</span></span> <span data-ttu-id="e87a7-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e87a7-129">For example:</span></span>

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a><span data-ttu-id="e87a7-130">Dénomination</span><span class="sxs-lookup"><span data-stu-id="e87a7-130">Naming</span></span>

<span data-ttu-id="e87a7-131">Contrairement aux EditorConfig fichiers, qui doivent être nommés `.editorconfig` , les fichiers de configuration globaux n’ont pas besoin d’avoir un nom ou une extension spécifique.</span><span class="sxs-lookup"><span data-stu-id="e87a7-131">Unlike EditorConfig files, which must be named `.editorconfig`, global config files do not need to have a specific name or extension.</span></span> <span data-ttu-id="e87a7-132">Toutefois, si vous nommez ces fichiers, `.globalconfig` ils sont implicitement appliqués à tous les projets C# et Visual Basic dans le dossier actif, y compris les sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="e87a7-132">However, if you name these files as `.globalconfig` then they will be implicitly applied to all the C# and Visual Basic projects within the current folder, including subfolders.</span></span> <span data-ttu-id="e87a7-133">Sinon, vous devez ajouter explicitement l' `GlobalAnalyzerConfigFiles` élément à votre fichier projet MSBuild :</span><span class="sxs-lookup"><span data-stu-id="e87a7-133">Otherwise, you must explicitly add the `GlobalAnalyzerConfigFiles` item to your MSBuild project file:</span></span>

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="e87a7-134">L’entrée de niveau supérieur `is_global = true` est requise même si le fichier est nommé `.globalconfig` .</span><span class="sxs-lookup"><span data-stu-id="e87a7-134">The top-level entry `is_global = true` is required even when the file is named `.globalconfig`.</span></span>

### <a name="example"></a><span data-ttu-id="e87a7-135"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e87a7-135">Example</span></span>

<span data-ttu-id="e87a7-136">Voici un exemple de fichier AnalyzerConfig global permettant de configurer les options et la gravité de la règle au niveau du projet :</span><span class="sxs-lookup"><span data-stu-id="e87a7-136">Following is an example global AnalyzerConfig file to configure options and rule severity at the project level:</span></span>

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

## <a name="precedence"></a><span data-ttu-id="e87a7-137">Priorité</span><span class="sxs-lookup"><span data-stu-id="e87a7-137">Precedence</span></span>

<span data-ttu-id="e87a7-138">Les fichiers EditorConfig et les fichiers AnalyzerConfig globaux spécifient une paire clé-valeur pour chaque option.</span><span class="sxs-lookup"><span data-stu-id="e87a7-138">Both EditorConfig files and global AnalyzerConfig files specify a key-value pair for each option.</span></span> <span data-ttu-id="e87a7-139">Des conflits se produisent quand il existe plusieurs entrées avec la même clé mais des valeurs différentes.</span><span class="sxs-lookup"><span data-stu-id="e87a7-139">Conflicts arise when there are multiple entries with the same key but different values.</span></span>

### <a name="general-options"></a><span data-ttu-id="e87a7-140">Options générales</span><span class="sxs-lookup"><span data-stu-id="e87a7-140">General options</span></span>

<span data-ttu-id="e87a7-141">Lorsque des conflits se produisent entre les options, les règles de précédence suivantes sont utilisées pour résoudre les conflits :</span><span class="sxs-lookup"><span data-stu-id="e87a7-141">When conflicts arise between options, the following precedence rules are used to resolve the conflicts:</span></span>

- <span data-ttu-id="e87a7-142">Entrées en conflit dans le même fichier de configuration : l’entrée qui apparaît ultérieurement dans le fichier gagne.</span><span class="sxs-lookup"><span data-stu-id="e87a7-142">Conflicting entries in the same configuration file: The entry that appears later in the file wins.</span></span> <span data-ttu-id="e87a7-143">Cela est vrai pour les entrées en conflit dans un EditorConfig fichier unique et également dans un fichier AnalyzerConfig global unique.</span><span class="sxs-lookup"><span data-stu-id="e87a7-143">This is true for conflicting entries within a single EditorConfig file and also within a single global AnalyzerConfig file.</span></span>

- <span data-ttu-id="e87a7-144">Entrées en conflit dans deux EditorConfig fichiers : l’entrée dans le EditorConfig fichier qui est plus profonde dans le système de fichiers et, par conséquent, a un chemin d’accès de fichier plus long, WINS.</span><span class="sxs-lookup"><span data-stu-id="e87a7-144">Conflicting entries in two EditorConfig files: The entry in the EditorConfig file that's deeper in the file system, and hence has a longer file path, wins.</span></span>

- <span data-ttu-id="e87a7-145">Entrées en conflit dans deux fichiers AnalyzerConfig globaux : un avertissement du compilateur est signalé et les deux entrées sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="e87a7-145">Conflicting entries in two global AnalyzerConfig files: A compiler warning is reported and both entries are ignored.</span></span>

- <span data-ttu-id="e87a7-146">Entrées en conflit dans un EditorConfig fichier et un fichier AnalyzerConfig global : l’entrée dans le EditorConfig fichier gagne.</span><span class="sxs-lookup"><span data-stu-id="e87a7-146">Conflicting entries in an EditorConfig file and a Global AnalyzerConfig file: The entry in the EditorConfig file wins.</span></span>

### <a name="severity-options"></a><span data-ttu-id="e87a7-147">Options de gravité</span><span class="sxs-lookup"><span data-stu-id="e87a7-147">Severity options</span></span>

<span data-ttu-id="e87a7-148">Les [règles de précédence générales](#general-options) précédentes s’appliquent à toutes les options spécifiées dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="e87a7-148">The previous [general precedence rules](#general-options) apply for all options specified in configuration files.</span></span> <span data-ttu-id="e87a7-149">Pour les options de [configuration de gravité](configuration-options.md#severity-level) , les règles de précédence supplémentaires suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="e87a7-149">For [severity configuration](configuration-options.md#severity-level) options, the following additional precedence rules apply:</span></span>

- <span data-ttu-id="e87a7-150">Les options de gravité spécifiées sur la ligne de commande en tant qu’options du compilateur ( `/nowarn` ou `/warnaserror` ) remplacent toujours les options de [configuration de gravité](configuration-options.md#severity-level) spécifiées dans EditorConfig et les fichiers Global AnalyzerConfig.</span><span class="sxs-lookup"><span data-stu-id="e87a7-150">Severity options specified at the command line as compiler options (`/nowarn` or `/warnaserror`) always override [severity configuration](configuration-options.md#severity-level) options specified in EditorConfig and global AnalyzerConfig files.</span></span>

- <span data-ttu-id="e87a7-151">Les options de gravité peuvent également être spécifiées avec un fichier [RuleSet](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) .</span><span class="sxs-lookup"><span data-stu-id="e87a7-151">Severity options can also be specified with a [Ruleset](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) file.</span></span> <span data-ttu-id="e87a7-152">Toutefois, les fichiers RuleSet sont dépréciés en faveur des EditorConfig fichiers AnalyzerConfig globaux et.</span><span class="sxs-lookup"><span data-stu-id="e87a7-152">However, rulesets files are deprecated in favor of EditorConfig and global AnalyzerConfig files.</span></span> <span data-ttu-id="e87a7-153">Il est recommandé de [convertir les fichiers de l’ensemble de règles en un EditorConfig fichier équivalent](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span><span class="sxs-lookup"><span data-stu-id="e87a7-153">It's recommended that you [convert ruleset files to an equivalent EditorConfig file](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span></span> <span data-ttu-id="e87a7-154">La priorité des entrées de gravité conflictuelles d’un fichier RuleSet et de EditorConfig fichiers AnalyzerConfig globaux n’est _pas définie_.</span><span class="sxs-lookup"><span data-stu-id="e87a7-154">Precedence for conflicting severity entries from a ruleset file and EditorConfig or global AnalyzerConfig files is _undefined_.</span></span>

- <span data-ttu-id="e87a7-155">Pour plus d’informations sur les règles de précédence pour les options de gravité associées avec des clés différentes, par exemple, lorsque différents niveaux de gravité sont spécifiés pour une seule règle et pour la catégorie dans laquelle la règle se trouve, consultez [options de configuration pour l’analyse du code](configuration-options.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="e87a7-155">For information about precedence rules for related severity options with different keys, for example, when different severities are specified for a single rule and for the category that rule falls under, see [Configuration options for code analysis](configuration-options.md#precedence).</span></span>

## <a name="see-also"></a><span data-ttu-id="e87a7-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e87a7-156">See also</span></span>

- [<span data-ttu-id="e87a7-157">EditorConfig problème de conception de AnalyzerConfig global vs</span><span class="sxs-lookup"><span data-stu-id="e87a7-157">EditorConfig vs global AnalyzerConfig design issue</span></span>](https://github.com/dotnet/roslyn/issues/47707)
