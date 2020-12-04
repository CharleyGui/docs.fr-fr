---
title: Règles de mise en forme du style de code
description: En savoir plus sur les règles de style de code pour mettre en forme les retraits, les espaces et les nouvelles lignes.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 61e6f6a6afdc6aaf9710eef3143af8ae700ef612
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "96587753"
---
# <a name="formatting-rules"></a>Règles de mise en forme

Les règles de mise en forme affectent la manière dont les retraits, les espaces et les nouvelles lignes sont alignés autour des constructions du langage de programmation .NET. Les règles sont classées dans les catégories suivantes :

- [Règles de mise en forme .net](#net-formatting-rules): règles qui s’appliquent à la fois à C# et Visual Basic. Les noms des options EditorConfig pour ces règles commencent par le `dotnet_` préfixe.
- [Règles de mise en forme c#](#c-formatting-rules): règles spécifiques au langage c# uniquement. Les noms des options EditorConfig pour ces règles commencent par le `csharp_` préfixe.

## <a name="rule-id-ide0055-fix-formatting"></a>ID de règle : « IDE0055 » (correction de la mise en forme)

Toutes les options de mise en forme ont un ID `IDE0055` et un titre de règle `Fix formatting` . Définissez la gravité d’une violation de mise en forme dans un fichier baEditorConfig à l’aide de la ligne de configuration suivante.

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

La valeur de gravité doit être ou doit être `warning` `error` [appliquée lors de la génération](../overview.md#code-style-analysis). Pour toutes les valeurs de gravité possibles, consultez [niveau de gravité](../configuration-options.md#severity-level).

## <a name="option-format"></a>Format d’option

Les options de mise en forme des règles peuvent être spécifiées dans un fichier EditorConfig au format suivant :

`rule_name = value`

Pour de nombreuses règles, vous spécifiez `true` (préférer ce style) ou `false` (ne pas préférer ce style) pour `value`. Pour les autres règles, vous spécifiez une valeur comme `flush_left` ou `before_and_after` pour décrire quand et où appliquer la règle. Vous ne spécifiez pas un niveau de gravité.

## <a name="net-formatting-rules"></a>Règles de mise en forme .NET

Les règles de mise en forme de cette section s’appliquent à C# et Visual Basic.

- [Organiser les using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organiser les directives using

Ces règles de mise en forme concernent le tri et l’affichage des directives `using` et instructions `Imports`.

Exemple de fichier *.editorconfig* :

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet\_sort\_system\_directives_first

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | dotnet_sort_system_directives_first |
| **Langues applicables** | C# et Visual Basic |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` -Trier `System.*` `using` les directives par ordre alphabétique et les placer avant les autres directives using.<br /><br />`false` -Ne pas placer de `System.*` `using` directives avant d’autres `using` directives. |

Exemples de code :

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet\_separate\_import\_directive\_groups

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | dotnet_separate_import_directive_groups |
| **Langues applicables** | C# et Visual Basic |
| **Version introduite** | Visual Studio 2017 version 15.5 |
| **Valeurs d’option** | `true` - Placer une ligne vide entre les groupes de directives `using`.<br /><br />`false` - Ne pas placer de ligne vide entre les groupes de directives `using`. |

Exemples de code :

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a>Règles de mise en forme C#

Les règles de mise en forme mentionnées dans cette section s’appliquent uniquement au code C#.

- [Options de saut de ligne](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Options de mise en retrait](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Options d’espacement](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Options d’encapsulage](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks
- [Utilisation des options de directive](#using-directive-options)
  - csharp_using_directive_placement

### <a name="new-line-options"></a>Options de nouvelle ligne

Ces règles de mise en forme concernent l’utilisation de nouvelles lignes pour mettre en forme du code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_new\_line\_before\_open_brace

Cette règle vise à déterminer si une accolade ouvrante `{` doit être placée sur la même ligne que le code précédent, ou sur une nouvelle ligne. Pour cette règle, vous spécifiez à la place **all**, **none**, ou un ou plusieurs éléments de code tels que **methods** ou **proprerties**, pour définir quand cette règle doit être appliquée. Pour spécifier plusieurs éléments de code, séparez-les par une virgule (,).

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_before_open_brace |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `all` - Les accolades doivent se trouver sur une nouvelle ligne pour toutes les expressions (style « Allman »).<br /><br />`none` - Les accolades doivent se trouver sur la même ligne pour toutes les expressions ("K&R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Nécessiter la présence d’accolades sur une nouvelle ligne pour l’élément de code spécifié (style « Allman »). |

Exemples de code :

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a>csharp\_new\_line\_before_else

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_before_else |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Placer les instructions `else` sur une nouvelle ligne.<br /><br />`false` - Placer les instructions `else` sur la même ligne. |

Exemples de code :

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a>csharp\_new\_line\_before_catch

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_before_catch |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Placer les instructions `catch` sur une nouvelle ligne.<br /><br />`false` - Placer les instructions `catch` sur la même ligne. |

Exemples de code :

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a>csharp\_new\_line\_before_finally

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_before_finally |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Les instructions `finally` doivent se trouver sur une nouvelle ligne après l’accolade fermante.<br /><br />`false` - Les instructions `finally` doivent se trouver sur la même ligne que l’accolade fermante. |

Exemples de code :

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_before_members_in_object_initializers |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Les membres d’initialiseurs d’objet doivent être sur des lignes distinctes<br /><br />`false` - Les membres d’initialiseurs d’objet doivent être sur la même ligne |

Exemples de code :

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_before_members_in_anonymous_types |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Les membres de types anonymes doivent être sur des lignes distinctes<br /><br />`false` - Les membres de types anonymes doivent être sur la même ligne |

Exemples de code :

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_new_line_between_query_expression_clauses |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Les éléments des clauses d’expression de requête doivent se trouver sur des lignes distinctes<br /><br />`false` - Les éléments des clauses d’expression de requête doivent se trouver sur la même ligne |

Exemples de code :

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>Options d’indentation

Ces règles de mise en forme concernent l’utilisation de l’indentation pour mettre en forme du code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a>csharp\_indent\_case_contents

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_indent_case_contents |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Mettre en retrait le contenu de `switch` case<br /><br />`false` - Ne pas mettre en retrait le contenu de `switch` case |

- Quand cette règle est définie sur **true**, i.
- Quand cette règle est définie sur **false**, d.

Exemples de code :

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a>csharp\_indent\_switch_labels

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_indent_switch_labels |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Mettre en retrait les étiquettes `switch`<br /><br />`false` - Ne pas mettre en retrait les étiquettes `switch` |

Exemples de code :

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a>csharp\_indent_labels

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_indent_labels |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `flush_left` - Les étiquettes sont positionnées au niveau de la colonne la plus à gauche<br /><br />`one_less_than_current` - Les étiquettes sont positionnées d’un retrait à gauche par rapport au contexte actuel<br /><br />`no_change` - Les étiquettes sont placées au même niveau de retrait que le contexte actuel |

Exemples de code :

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_indent_block_contents |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - <br /><br />`false` -  |

Exemples de code :

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_indent_braces |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - <br /><br />`false` -  |

Exemples de code :

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_indent_case_contents_when_block |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - <br /><br />`false` -  |

Exemples de code :

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Options d’espacement

Ces règles de mise en forme concernent l’utilisation de caractères d’espacement pour mettre en forme du code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a>csharp\_space\_after_cast

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_after_cast |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Placer un espace entre un cast et la valeur<br /><br />`false` - Supprimer l’espace entre le cast et la valeur |

Exemples de code :

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_after_keywords_in_control_flow_statements |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Placer un espace après un mot clé dans une instruction de flux de contrôle, par exemple une boucle `for`<br /><br />`false` - Supprimer l’espace après un mot clé dans une instruction de flux de contrôle, par exemple une boucle `for` |

Exemples de code :

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_parentheses |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `control_flow_statements` - Placer un espace entre les parenthèses d’instructions de flux de contrôle<br /><br />`expressions` - Placer un espace entre les parenthèses d’expressions<br /><br />`type_casts` - Placer un espace entre les parenthèses dans les casts de type |

Si vous omettez cette règle, ou si vous utilisez une valeur autre que `control_flow_statements`, `expressions` ou `type_casts`, le paramètre n’est pas appliqué.

Exemples de code :

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_before_colon_in_inheritance_clause |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs d’option** | `true` - Placer un espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type<br /><br />`false` - Supprimer l’espace avant le signe deux-points pour les bases ou les interfaces dans une déclaration de type |

Exemples de code :

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_after_colon_in_inheritance_clause |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs d’option** | `true` - Placer un espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type<br /><br />`false` - Supprimer l’espace après le signe deux-points pour les bases ou les interfaces dans une déclaration de type |

Exemples de code :

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a>csharp\_space\_around\_binary_operators

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_around_binary_operators |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs d’option** | `before_and_after` - Insérer un espace avant et après l’opérateur binaire<br /><br />`none` - Supprimer les espaces avant et après l’opérateur binaire<br /><br />`ignore` - Ignorer les espaces autour des opérateurs binaires |

Si vous omettez cette règle, ou si vous utilisez une valeur autre que `before_and_after`, `none` ou `ignore`, le paramètre n’est pas appliqué.

Exemples de code :

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Placez un espace après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode.<br /><br />`false` - Supprimer les espaces après la parenthèse ouvrante et avant la parenthèse fermante d’une liste de paramètres de déclaration de méthode |

Exemples de code :

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs d’option** | `true` - Insérer un espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode<br /><br />`false` - Supprimer l’espace dans les parenthèses de liste de paramètres vides pour une déclaration de méthode |

Exemples de code :

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Placer un espace entre le nom de la méthode et la parenthèse ouvrante dans la déclaration de méthode<br /><br />`false` - Supprimer les espaces entre le nom de la méthode et la parenthèse ouvrante dans la déclaration de méthode |

Exemples de code :

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_method_call_parameter_list_parentheses |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Placer un caractère d’espacement après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode<br /><br />`false` - Supprimer les espaces après la parenthèse ouvrante et avant la parenthèse fermante d’un appel de méthode |

Exemples de code :

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs d’option** | `true` - Insérer un espace dans les parenthèses de la liste d’arguments vide<br /><br />`false` - Supprimer un espace dans les parenthèses de la liste d’arguments vide |

Exemples de code :

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.7 |
| **Valeurs d’option** | `true` - Insérer un espace entre le nom d’appel de méthode et la parenthèse ouvrante<br /><br />`false` - Supprimer l’espace entre le nom d’appel de méthode et la parenthèse ouvrante |

Exemples de code :

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_after_comma |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace après une virgule<br /><br />`false` - Supprimer l’espace après une virgule |

Exemples de code :

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_before_comma |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace avant une virgule<br /><br />`false` - Supprimer l’espace avant une virgule |

Exemples de code :

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_after_dot |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace après un point<br /><br />`false` - Supprimer l’espace après un point |

Exemples de code :

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_before_dot |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace avant un point <br /><br />`false` - Supprimer l’espace avant un point |

Exemples de code :

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_after_semicolon_in_for_statement |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace après chaque point-virgule dans une instruction `for`<br /><br />`false` - Supprimer l’espace après chaque point-virgule dans une instruction `for` |

Exemples de code :

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_before_semicolon_in_for_statement |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace avant chaque point-virgule dans une instruction `for` <br /><br />`false` - Supprimer l’espace avant chaque point-virgule dans une instruction `for` |

Exemples de code :

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_around_declaration_statements |
| **Langues applicables** | C# |
| **Valeurs d’option** | `ignore` - Ne pas supprimer les espaces supplémentaires dans les instructions de déclaration<br /><br />`false` - Supprimer les espaces supplémentaires dans les instructions de déclaration |

Exemples de code :

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_before_open_square_brackets |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace avant les crochets ouvrants `[` <br /><br />`false` - Supprimer l’espace avant les crochets ouvrants `[` |

Exemples de code :

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_empty_square_brackets |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer un espace entre des crochets vides `[ ]` <br /><br />`false` - Supprimer l’espace entre des crochets vides `[]` |

Exemples de code :

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_space_between_square_brackets |
| **Langues applicables** | C# |
| **Valeurs d’option** | `true` - Insérer des espaces entre des crochets non vides `[ 0 ]` <br /><br />`false` - Supprimer des espaces entre des crochets non vides `[0]` |

Exemples de code :

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Options d’encapsulage

Ces règles de mise en forme concernent l’utilisation de lignes uniques ou de lignes distinctes pour les instructions et les blocs de code.

Exemple de fichier *.editorconfig* :

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_preserve_single_line_statements |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Laisser les instructions et les déclarations de membre sur la même ligne<br /><br />`false` - Laisser les instructions et les déclarations de membre sur des lignes différentes |

Exemples de code :

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_preserve_single_line_blocks |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2017 version 15.3 |
| **Valeurs d’option** | `true` - Laisser le bloc de code sur une seule ligne<br /><br />`false` - Laisser le bloc de code sur des lignes distinctes |

Exemples de code :

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a>Utilisation des options de directive

Cette règle de mise en forme concerne l’utilisation des directives using placées à l’intérieur et à l’extérieur d’un espace de noms.

Exemple de fichier *.editorconfig* :

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|Propriété|Valeur|
|-|-|
| **Nom de l’option** | csharp_using_directive_placement |
| **Langues applicables** | C# |
| **Version introduite** | Visual Studio 2019 version 16.1 |
| **Valeurs d’option** | `outside_namespace` -Laissez les directives using en dehors de l’espace de noms<br /><br />`inside_namespace` -Laissez les directives using à l’intérieur de l’espace de noms |

Exemples de code :

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a>Voir aussi

- [Règles de langage](language-rules.md)
- [Règles d’affectation des noms](naming-rules.md)
- [Référence des règles de style de code .NET](index.md)
