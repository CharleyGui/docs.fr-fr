---
title: Règles d’attribution de noms de style de code
description: En savoir plus sur les règles de style de code .NET pour nommer les éléments de code.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: 8ce209e64ee7f9f9028c221daedef8fc6a993ef7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588714"
---
# <a name="naming-rules"></a>Règles d’affectation des noms

Les règles de nommage concernent le nom des éléments de code du langage de programmation .NET, tels que les classes, les propriétés et les méthodes. Par exemple, vous pouvez spécifier que les membres publics doivent être en majuscules ou que les champs privés doivent commencer par `_` .

Une règle de nommage se compose de trois parties :

* Groupe de symboles auquel il s’applique.
* Style d’affectation de noms à associer à la règle.
* Gravité de l’application de la Convention.

Vous définissez des règles d’affectation de noms dans un fichier baEditorConfig.

## <a name="general-syntax"></a>Syntaxe générale

Pour définir une règle de nommage, un groupe de symboles ou un style de nom, définissez une ou plusieurs propriétés à l’aide de la syntaxe suivante :

```ini
<prefix>.<title>.<propertyName> = <propertyValue>
```

Chaque propriété ne doit être définie qu’une seule fois, mais certains paramètres autorisent plusieurs valeurs séparées par des virgules.

L’ordre des propriétés n’est pas important.

### \<prefix>

**\<prefix>** Spécifie le type d’élément défini comme &mdash; règle de nommage, groupe de symboles ou style de nom &mdash; et doit être l’un des éléments suivants :

| Pour définir une propriété pour | Utiliser le préfixe |  Exemple |
| --- | --- | -- |
| Règle de nommage | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| Groupe de symboles | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| Style de nommage | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

Chaque type de &mdash; [règle d’attribution de noms](#naming-rule-properties)de définitions, de groupe de [symboles](#symbol-group-properties)ou de [style de nom](#naming-style-properties) &mdash; possède ses propres propriétés prises en charge, comme décrit dans les sections suivantes.

### \<title>

**\<title>** est un nom descriptif que vous choisissez qui associe plusieurs paramètres de propriété dans une définition unique. Par exemple, les propriétés suivantes produisent deux définitions de groupe de symboles, `interface` et `types` , chacune d’entre elles ayant deux propriétés définies.

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a>Propriétés de la règle d’affectation de noms

Toutes les propriétés de règle de nommage sont requises pour que la règle prenne effet.

| Propriété | Description |
| -- | -- |
| `symbols` | Titre du groupe de symboles, définissant les symboles auxquels cette règle doit être appliquée |
| `style` | Titre du style d’affectation de noms qui doit être associé à cette règle |
| `severity` |  Définit la gravité avec laquelle appliquer la règle de nommage. Définissez la valeur associée sur l’un des [niveaux de gravité](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level)disponibles. <sup>1</sup> |

**Remarques :**

1. La spécification de gravité dans une règle de nommage n’est respectée que dans des environnements IDE de développement, tels que Visual Studio. Ce paramètre n’est pas compris par les compilateurs C# ou VB, il n’est donc pas respecté pendant la génération. Au lieu de cela, pour appliquer des règles de style d’affectation de noms à la build, vous devez définir la gravité en utilisant la configuration de gravité basée sur l’ID de règle, comme expliqué dans [cette section](#rule-id-ide1006-naming-rule-violation). Pour plus d’informations, consultez ce [problème GitHub](https://github.com/dotnet/roslyn/issues/44201).

## <a name="rule-order"></a>Ordre des règles

L’ordre dans lequel les règles d’affectation de noms sont définies dans un fichier EditorConfig n’a pas d’importance. Les règles d’affectation de noms sont automatiquement triées en fonction de la définition des règles proprement dites. L' [extension du service de langage EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) peut analyser un fichier EditorConfig et signaler les cas où l’ordonnancement des règles dans le fichier est différent de ce que le compilateur utilisera au moment de l’exécution.

> [!NOTE]
>
> Si vous utilisez une version de Visual Studio antérieure à Visual Studio 2019 version 16,2, les règles de nommage doivent être classées de la plus spécifique à la moins spécifique dans le fichier EditorConfig. La première règle applicable rencontrée est la seule règle appliquée. Toutefois, s’il existe plusieurs *propriétés* de règle portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire. Pour plus d’informations, consultez [Priorité et hiérarchie des fichiers](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).

## <a name="symbol-group-properties"></a>Propriétés du groupe de symboles

Vous pouvez définir les propriétés suivantes pour les groupes de symboles, afin de limiter les symboles inclus dans le groupe. Pour spécifier plusieurs valeurs dans un même paramètre de propriété, séparez-les par une virgule.

| Propriété | Description | Valeurs autorisées | Obligatoire |
| -- | -- | -- | -- |
| `applicable_kinds` | Genres de symboles dans le groupe <sup>1</sup> | `*` (Utilisez cette valeur pour spécifier tous les symboles.)<br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | Oui |
| `applicable_accessibilities` | Niveaux d’accessibilité des symboles dans le groupe | `*` (Utilisez cette valeur pour spécifier tous les niveaux d’accessibilité.)<br/>`public`<br/>`internal` ou `friend`<br/>`private`<br/>`protected`<br/>`protected_internal` ou `protected_friend`<br/>`private_protected`<br/>`local` (pour les symboles définis dans une méthode) | Oui |
| `required_modifiers` | Faire correspondre uniquement les symboles avec _tous_ les modificateurs spécifiés <sup>2</sup> | `abstract` ou `must_inherit`<br/>`async`<br/>`const`<br/>`readonly`<br/>`static` ou `shared` <sup>3</sup> | Non |

**Remarques :**

1. Les membres de tuple ne sont actuellement pas pris en charge dans `applicable_kinds` .
2. Le groupe de symboles correspond à _tous_ les modificateurs de la `required_modifiers` propriété.  Si vous omettez cette propriété, aucun modificateur spécifique n’est requis pour une correspondance. Cela signifie que les modificateurs d’un symbole n’ont aucun effet sur l’application ou non de cette règle.
3. Si votre groupe possède `static` ou `shared` dans la `required_modifiers` propriété, le groupe inclut également des `const` symboles, car ils sont implicitement `static` / `Shared` . Toutefois, si vous ne souhaitez pas que la `static` règle d’affectation de noms s’applique aux `const` symboles, vous pouvez créer une nouvelle règle de nommage avec un groupe de symboles `const` .

## <a name="naming-style-properties"></a>Propriétés de style de nom

Un style d’affectation de noms définit les conventions que vous souhaitez appliquer à la règle. Par exemple :

* Mettre en majuscules `PascalCase`
* Commence par `m_`
* Se termine par `_g`
* Séparer les mots avec `__`

Vous pouvez définir les propriétés suivantes pour un style d’affectation de noms :

| Propriété | Description | Valeurs autorisées | Obligatoire |
| -- | -- | -- | -- |
| `capitalization` | Style de mise en majuscules pour les mots dans le symbole | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | Oui<sup>1</sup> |
| `required_prefix` | Doit commencer par ces caractères | | Non |
| `required_suffix` | Doit se terminer par ces caractères | | Non |
| `word_separator` | Les mots contenus dans le symbole doivent être séparés par ce caractère | | Non |

**Remarques :**

1. Vous devez spécifier un style de mise en majuscules dans le cadre de votre style de nommage, sans quoi votre style de nommage risque d’être ignoré.

## <a name="default-naming-styles"></a>Styles de dénomination par défaut

Si vous ne spécifiez aucune règle de nommage personnalisée, les styles par défaut suivants sont utilisés :

- Pour les classes, structures, énumérations, propriétés et événements avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal.

- Pour les interfaces avec l’accessibilité `public`, `private`, `internal`, `protected` ou `protected_internal`, le style de dénomination par défaut est la casse Pascal avec le préfixe **I** requis.

## <a name="example"></a> Exemple

Le fichier *.editorconfig* suivant contient une convention de nommage qui spécifie que les propriétés publiques, les méthodes, les champs, les événements et les délégués doivent être mis en majuscules. Notez que cette convention de nommage spécifie plusieurs types de symboles auxquels appliquer la règle, en utilisant une virgule pour séparer les valeurs.

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a>ID de règle : « IDE1006 » (violation de règle de nommage)

Toutes les options d’attribution de noms ont un ID `IDE1006` et un titre de règle `Naming rule violation` . Vous pouvez configurer le niveau de gravité des violations de nom globalement dans un fichier EditorConfig avec la syntaxe suivante :

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

La valeur de gravité doit être ou doit être `warning` `error` [appliquée lors de la génération](../overview.md#code-style-analysis). Pour toutes les valeurs de gravité possibles, consultez [niveau de gravité](../configuration-options.md#severity-level).

## <a name="see-also"></a>Voir aussi

- [Règles de langage](language-rules.md)
- [Règles de mise en forme](formatting-rules.md)
- [Règles d’affectation de noms Roslyn](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Référence des règles de style de code .NET](index.md)
