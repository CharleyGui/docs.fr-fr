---
title: Options de configuration d’une règle de qualité du code
description: Découvrez comment spécifier des options de configuration supplémentaires pour les règles de qualité du code.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2984e73c554e8a1e1b32df9460933f86cc41be
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96587127"
---
# <a name="code-quality-rule-configuration-options"></a>Options de configuration d’une règle de qualité du code

Les règles de *qualité du code* comportent des options de configuration supplémentaires, outre la simple [configuration de leur gravité](configuration-options.md#severity-level). Par exemple, chaque analyseur de qualité du code peut être configuré pour s’appliquer uniquement à des parties spécifiques de votre code base. Vous spécifiez ces options en ajoutant des paires clé-valeur au même [EditorConfig](https://editorconfig.org) fichier où vous spécifiez des gravités de règle et des préférences générales de l’éditeur.

## <a name="option-scopes"></a>Étendues des options

Chaque option d’affinage peut être configurée pour toutes les règles, pour une catégorie de règles (par exemple, la sécurité ou la conception) ou pour une règle spécifique.

### <a name="all-rules"></a>Toutes les règles

La syntaxe de configuration d’une option pour *toutes les* règles est la suivante :

|Syntaxe| Exemple|
|-|-|
| dotnet_code_quality. Nomoptin = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Catégorie de règles

La syntaxe permettant de configurer une option pour une *catégorie* de règles (par exemple, le nom, la conception ou la performance) est la suivante :

|Syntaxe| Exemple|
|-|-|
| dotnet_code_quality. RuleCategory. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Règle spécifique

La syntaxe de configuration d’une option pour une règle *spécifique* est la suivante :

|Syntaxe| Exemple|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options"></a>Options

Cette section répertorie certaines des options disponibles. Pour afficher la liste complète des options disponibles, consultez [configuration de l’analyseur](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md).

### <a name="api_surface"></a>api_surface

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| La partie de la surface d’API à analyser | `public`<br/>`internal` ou `friend`<br/>`private`<br/>`all`<br/><br/>Séparez plusieurs valeurs par une virgule (,) | `public` | CA1000 [CA1003](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md) [CA1](quality-rules/ca1000.md)<br/>[CA1012](quality-rules/ca1012.md) - [1024](quality-rules/ca1024.md) [CA1027](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)<br/>[CA1030](quality-rules/ca1030.md) [CA1036](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)<br/>[Ca1043](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)<br/>[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) ca--le ca- [1058](quality-rules/ca1058.md)<br/>[CA1063](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)<br/>[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [ca1717](quality-rules/ca1717.md)<br/>[Ca1720](quality-rules/ca1720.md) [ca1721s](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [CA1801](quality-rules/ca1801.md)<br/>[Ca1802](quality-rules/ca1802.md) [-1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)<br/>[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [CA2234](quality-rules/ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut ignorer les méthodes asynchrones qui ne retournent pas de valeur | `true`<br/>`false` | `false` | [CA2007](quality-rules/ca2007.md) |

> [!NOTE]
> Cette option a été nommée `skip_async_void_methods` dans une version antérieure.

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut exclure les [paramètres de type](../../csharp/programming-guide/generics/generic-type-parameters.md) à un seul caractère de la règle, par exemple `S` dans `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](quality-rules/ca1715.md) |

> [!NOTE]
> Cette option a été nommée `allow_single_letter_type_parameters` dans une version antérieure.

### <a name="output_kind"></a>output_kind

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie que le code d’un projet qui génère ce type d’assembly doit être analysé | Un ou plusieurs champs de l' <xref:Microsoft.CodeAnalysis.OutputKind> énumération<br/><br/>Séparez plusieurs valeurs par une virgule (,) | Tous les types de sortie | [CA2007](quality-rules/ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Spécifie les modificateurs requis pour les API qui doivent être analysées | Une ou plusieurs valeurs de la table de modificateurs autorisées ci-dessous<br/><br/>Séparez plusieurs valeurs par une virgule (,) | Dépend de chaque règle | [CA1802](quality-rules/ca1802.md) |

| Modificateur autorisé | Résumé |
| --- | --- |
| `none` | Aucune exigence de modificateur |
| `static` ou `Shared` | Doit être déclarée comme `static` ( `Shared` dans Visual Basic) |
| `const` | Doit être déclarée comme `const` |
| `readonly` | Doit être déclarée comme `readonly` |
| `abstract` | Doit être déclarée comme `abstract` |
| `virtual` | Doit être déclarée comme `virtual` |
| `override` | Doit être déclarée comme `override` |
| `sealed` | Doit être déclarée comme `sealed` |
| `extern` | Doit être déclarée comme `extern` |
| `async` | Doit être déclarée comme `async` |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Indique s’il faut ignorer l’analyse pour le `this` paramètre des méthodes d’extension | `true`<br/>`false` | `false` | [CA1062](quality-rules/ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des méthodes de validation de contrôle null qui valident que les arguments passés à la méthode sont non null | Formats de nom de méthode autorisés (séparés par `|` ) :<br/> -Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)du symbole, avec un `M:` préfixe facultatif | None | [CA1062](quality-rules/ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des méthodes de mise en forme de chaînes supplémentaires | Formats de nom de méthode autorisés (séparés par `|` ) :<br/> -Nom de méthode uniquement (comprend toutes les méthodes portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole, avec un `M:` préfixe facultatif | None | [CA2241](quality-rules/ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Les noms des types, de telle sorte que le type et tous ses types dérivés soient exclus pour l’analyse | Formats de noms de symboles autorisés (séparés par `|` ) :<br/> -Nom de type uniquement (comprend tous les types portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole, avec un `T:` préfixe facultatif | None | [CA1303](quality-rules/ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des symboles exclus pour l’analyse | Formats de noms de symboles autorisés (séparés par `|` ) :<br/> -Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole. Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe `M:` pour les méthodes, le `T:` préfixe pour les types et le `N:` préfixe pour les espaces de noms.<br/> - `.ctor` pour les constructeurs et `.cctor` les constructeurs statiques | None | [CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [Ca2](quality-rules/ca2000.md) [ca2100](quality-rules/ca2100.md) [ca2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)<br/>[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)<br/>[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [ca3002](quality-rules/ca3002.md) - [3003](quality-rules/ca3003.md) [ca3004](quality-rules/ca3004.md)<br/>[Ca3005](quality-rules/ca3005.md) [ca3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [ca3010](quality-rules/ca3010.md)<br/>[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)<br/>[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](quality-rules/ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Description | Valeurs autorisées | Valeur par défaut | Règles configurables |
| - | - | - | - |
| Noms des symboles non autorisés dans le contexte de l’analyse | Formats de noms de symboles autorisés (séparés par `|` ) :<br/> -Nom du symbole uniquement (comprend tous les symboles portant le nom, quel que soit le type ou l’espace de noms conteneur)<br/> -Noms qualifiés complets dans le format d' [ID de documentation](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)du symbole. Chaque nom de symbole requiert un préfixe de type de symbole, tel que le préfixe `M:` pour les méthodes, le `T:` préfixe pour les types et le `N:` préfixe pour les espaces de noms.<br/> - `.ctor` pour les constructeurs et `.cctor` les constructeurs statiques | None | [CA1031](quality-rules/ca1031.md) |
