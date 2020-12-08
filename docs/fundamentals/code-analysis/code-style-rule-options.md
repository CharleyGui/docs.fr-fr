---
title: Options de règle de style de code .NET
description: Découvrez comment spécifier les options de style de code .NET.
ms.date: 09/25/2020
ms.topic: conceptual
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 5e4d80ec55f7fbcd01e364bb2b9e2b4f49f820d5
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "96588348"
---
# <a name="code-style-rule-options"></a><span data-ttu-id="30e1e-103">Options de règle de style de code</span><span class="sxs-lookup"><span data-stu-id="30e1e-103">Code style rule options</span></span>

<span data-ttu-id="30e1e-104">Vous pouvez définir et maintenir un *style de code* cohérent dans votre base de code en définissant les options de règle de style de code .net dans un fichier [baEditorConfig](/visualstudio/ide/create-portable-custom-editor-options) .</span><span class="sxs-lookup"><span data-stu-id="30e1e-104">You can define and maintain consistent *code style* in your codebase by defining .NET code style rule options in an [EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) file.</span></span> <span data-ttu-id="30e1e-105">Ces règles sont représentées par différents IDE de développement, tels que Visual Studio, lorsque vous modifiez votre code.</span><span class="sxs-lookup"><span data-stu-id="30e1e-105">These rules are surfaced by various development IDEs, such as Visual Studio, as you edit your code.</span></span> <span data-ttu-id="30e1e-106">Pour les projets .NET, ces règles peuvent également être [appliquées au moment](overview.md#code-style-analysis)de la génération.</span><span class="sxs-lookup"><span data-stu-id="30e1e-106">For .NET projects, these rules can also be [enforced at build time](overview.md#code-style-analysis).</span></span> <span data-ttu-id="30e1e-107">Vous pouvez activer ou désactiver des règles individuelles et configurer le degré d’application de chaque règle, par le biais d’un niveau de gravité.</span><span class="sxs-lookup"><span data-stu-id="30e1e-107">You can enable or disable individual rules and configure the degree to which you want each rule enforced, via a severity level.</span></span>

> [!TIP]
>
> - <span data-ttu-id="30e1e-108">Quand vous définissez des options de style de code dans un fichier EditorConfig, vous configurez la façon dont vous souhaitez que les [analyseurs de style de code](overview.md#code-style-analysis) analysent votre code.</span><span class="sxs-lookup"><span data-stu-id="30e1e-108">When you define code style options in an EditorConfig file, you're configuring how you want the [code style analyzers](overview.md#code-style-analysis) to analyze your code.</span></span> <span data-ttu-id="30e1e-109">Le fichier EditorConfig est le fichier de configuration pour ces analyseurs.</span><span class="sxs-lookup"><span data-stu-id="30e1e-109">The EditorConfig file is the configuration file for these analyzers.</span></span>
>
> - <span data-ttu-id="30e1e-110">Vous pouvez également définir les options de style de code dans Visual Studio dans la boîte de dialogue Options de l' [éditeur de texte](/visualstudio/ide/code-styles-and-code-cleanup) .</span><span class="sxs-lookup"><span data-stu-id="30e1e-110">Code style options can also be set in Visual Studio in the [Text editor options](/visualstudio/ide/code-styles-and-code-cleanup) dialog.</span></span> <span data-ttu-id="30e1e-111">Il s’agit d’options par utilisateur uniquement respectées lors de la modification dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30e1e-111">These are per-user options that are only respected while editing in Visual Studio.</span></span> <span data-ttu-id="30e1e-112">Ces options ne sont pas respectées au moment de la génération ou par d’autres IDE.</span><span class="sxs-lookup"><span data-stu-id="30e1e-112">These options are not respected at build time or by other IDEs.</span></span> <span data-ttu-id="30e1e-113">En outre, si le projet ou la solution ouverts dans Visual Studio a un fichier EditorConfig, les options du fichier EditorConfig sont prioritaires.</span><span class="sxs-lookup"><span data-stu-id="30e1e-113">Additionally, if the project or solution opened inside Visual Studio has an EditorConfig file, then options from the EditorConfig file take precedence.</span></span>

<span data-ttu-id="30e1e-114">Les règles de style de code sont divisées en sous-catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="30e1e-114">Code style rules are divided into following subcategories:</span></span>

- [<span data-ttu-id="30e1e-115">Règles de langage</span><span class="sxs-lookup"><span data-stu-id="30e1e-115">Language rules</span></span>](style-rules/language-rules.md)

- [<span data-ttu-id="30e1e-116">Règles de code inutiles</span><span class="sxs-lookup"><span data-stu-id="30e1e-116">Unnecessary code rules</span></span>](style-rules/unnecessary-code-rules.md)

- [<span data-ttu-id="30e1e-117">Règles de mise en forme</span><span class="sxs-lookup"><span data-stu-id="30e1e-117">Formatting rules</span></span>](style-rules/formatting-rules.md)

- [<span data-ttu-id="30e1e-118">Règles d’affectation des noms</span><span class="sxs-lookup"><span data-stu-id="30e1e-118">Naming rules</span></span>](style-rules/naming-rules.md)

<span data-ttu-id="30e1e-119">Chacune de ces sous-catégories définit sa propre syntaxe pour la spécification des options.</span><span class="sxs-lookup"><span data-stu-id="30e1e-119">Each of these subcategories defines its own syntax for specifying options.</span></span> <span data-ttu-id="30e1e-120">Pour plus d’informations sur ces règles et les options correspondantes, consultez [référence des règles de style de code](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="30e1e-120">For more information about these rules and the corresponding options, see [Code style rule reference](style-rules/index.md).</span></span>

## <a name="example-editorconfig-file"></a><span data-ttu-id="30e1e-121">Exemple de fichier EditorConfig</span><span class="sxs-lookup"><span data-stu-id="30e1e-121">Example EditorConfig file</span></span>

<span data-ttu-id="30e1e-122">Pour vous aider à démarrer, voici un exemple de fichier *. editorconfig* avec les options par défaut.</span><span class="sxs-lookup"><span data-stu-id="30e1e-122">To help you get started, here is an example *.editorconfig* file with the default options.</span></span>

> [!TIP]
> <span data-ttu-id="30e1e-123">Dans Visual Studio, vous pouvez générer ce fichier et l’enregistrer dans un projet dans **Outils**  >  **options**  >  **éditeur de texte** > [**C#** ou de **base**] > **style de code**  >  **général**.</span><span class="sxs-lookup"><span data-stu-id="30e1e-123">In Visual Studio, you can generate this file and save it to a project at **Tools** > **Options** > **Text Editor** > [**C#** or  **Basic**] > **Code Style** > **General**.</span></span> <span data-ttu-id="30e1e-124">Ensuite, cliquez sur le bouton **générer le fichier. editorconfig à partir des paramètres** .</span><span class="sxs-lookup"><span data-stu-id="30e1e-124">Then, click the **Generate .editorconfig file from settings** button.</span></span> <span data-ttu-id="30e1e-125">Pour plus d’informations, consultez [Préférences de style de code](/visualstudio/ide/code-styles-and-code-cleanup).</span><span class="sxs-lookup"><span data-stu-id="30e1e-125">For more information, see [Code style preferences](/visualstudio/ide/code-styles-and-code-cleanup).</span></span>

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

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false
file_header_template = unset

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_operator_placement_when_wrapping = beginning_of_line
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_boolean_expressions = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

# Suppression preferences
dotnet_remove_unnecessary_suppression_exclusions = none

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_not_pattern = true:suggestion
csharp_style_prefer_pattern_matching = true:silent
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = inside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers =

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers =

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers =

# Naming styles

dotnet_naming_style.pascal_case.required_prefix =
dotnet_naming_style.pascal_case.required_suffix =
dotnet_naming_style.pascal_case.word_separator =
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix =
dotnet_naming_style.begins_with_i.word_separator =
dotnet_naming_style.begins_with_i.capitalization = pascal_case

```

## <a name="see-also"></a><span data-ttu-id="30e1e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30e1e-126">See also</span></span>

- [<span data-ttu-id="30e1e-127">Référence de règle d’analyse de style de code</span><span class="sxs-lookup"><span data-stu-id="30e1e-127">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="30e1e-128">Appliquer le style de code à la Build</span><span class="sxs-lookup"><span data-stu-id="30e1e-128">Enforce code style on build</span></span>](overview.md#code-style-analysis)
- [<span data-ttu-id="30e1e-129">Actions rapides en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30e1e-129">Quick Actions in Visual Studio</span></span>](/visualstudio/ide/quick-actions)
- [<span data-ttu-id="30e1e-130">Créer des options d’éditeur personnalisées portables dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30e1e-130">Create portable custom editor options in Visual Studio</span></span>](/visualstudio/ide/create-portable-custom-editor-options)
- [<span data-ttu-id="30e1e-131">.NET Compiler Platform le fichier « Roslyn ». editorconfig</span><span class="sxs-lookup"><span data-stu-id="30e1e-131">.NET Compiler Platform "Roslyn" .editorconfig file</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
- [<span data-ttu-id="30e1e-132">Fichier .NET Compiler Platform Runtime. editorconfig</span><span class="sxs-lookup"><span data-stu-id="30e1e-132">.NET Compiler Platform Runtime .editorconfig file</span></span>](https://github.com/dotnet/runtime/blob/master/.editorconfig)