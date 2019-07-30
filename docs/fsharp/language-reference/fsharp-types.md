---
title: Types F#
description: En savoir plus sur les types utilisés dans F# et sur F# la manière dont les types sont nommés et décrits.
ms.date: 05/16/2016
ms.openlocfilehash: 44bd9d985e0ce1afa1bf2a8457dcd9470b13dfe1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630219"
---
# <a name="f-types"></a>Types F#

Cette rubrique décrit les types utilisés dans F# et la manière dont F# les types sont nommés et décrits.

## <a name="summary-of-f-types"></a>Résumé des F# types
Certains types sont considérés comme des *types primitifs*, tels `bool` que le type booléen et les types de virgules intégrales et à virgule flottante de différentes tailles, qui incluent des types pour les octets et les caractères. Ces types sont décrits dans [types primitifs](primitive-types.md).

D’autres types intégrés au langage incluent des tuples, des listes, des tableaux, des séquences, des enregistrements et des unions discriminées. Si vous avez de l’expérience avec d’autres langages F#.net et que vous apprenez, vous devez lire les rubriques pour chacun de ces types. Des liens vers des informations supplémentaires sur ces types sont inclus dans la section [Rubriques connexes](https://msdn.microsoft.com/library/#rel) de cette rubrique. Ces F#types spécifiques à prennent en charge des styles de programmation communs aux langages de programmation fonctionnelle. Un grand nombre de ces types ont des modules F# associés dans la bibliothèque qui prennent en charge des opérations courantes sur ces types.

Le type d’une fonction comprend des informations sur les types de paramètres et le type de retour.

Le .NET Framework est la source de types d’objets, d’interfaces, de types délégués, etc. Vous pouvez définir vos propres types d’objets comme vous le feriez dans n’importe quel autre langage .NET.

En outre F# , le code peut définir des alias, qui sont des abréviations de *type*nommées, qui sont des noms alternatifs pour les types. Vous pouvez utiliser des abréviations de type lorsque le type peut changer à l’avenir et que vous souhaitez éviter de modifier le code qui dépend du type. Ou bien, vous pouvez utiliser une abréviation de type comme nom convivial pour un type qui peut rendre le code plus facile à lire et à comprendre.

F#fournit des types de collection utiles conçus avec la programmation fonctionnelle à l’esprit. L’utilisation de ces types de collections vous permet d’écrire du code plus fonctionnel dans le style. Pour plus d’informations, consultez [ F# types de collections](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Syntaxe pour les types
Dans F# le code, vous devez souvent écrire les noms des types. Chaque type a une forme syntaxique, et vous utilisez ces formes syntaxiques dans les annotations de type, les déclarations de méthode abstraite, les déclarations déléguées, les signatures et d’autres constructions. Chaque fois que vous déclarez une nouvelle construction de programme dans l’interpréteur, l’interpréteur imprime le nom de la construction et la syntaxe de son type. Cette syntaxe peut être simplement un identificateur pour un type défini par l’utilisateur ou un identificateur intégré tel que pour `int` ou `string`, mais pour des types plus complexes, la syntaxe est plus complexe.

Le tableau suivant indique les aspects de la syntaxe de F# type pour les types.

|Type|Syntaxe de type|Exemples|
|----|-----------|--------|
|type primitif|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|type d’agrégat (Class, structure, Union, record, enum, etc.)|*type-name*|`System.DateTime`<br /><br />`Color`|
|abréviation de type|*type-abbreviation-name*|`bigint`|
|type qualifié complet|*namespaces.type-name*<br /><br />ou Gestionnaire de configuration<br /><br />*modules.type-name*<br /><br />ou Gestionnaire de configuration<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|array|*nom du type* [] ou<br /><br />tableau *de noms de types*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|tableau à deux dimensions|*type-name*[,]|`int[,]`<br /><br />`float[,]`|
|tableau à trois dimensions|*type-name*[,,]|`float[,,]`|
|tuple|*type-name1* &#42; *type-name2* ...|Par exemple, `(1,'b',3)` a le type`int * char * int`|
|type générique|*paramètre de type* *generic-type-name*<br /><br />ou Gestionnaire de configuration<br /><br />&lt;type de nom générique-*paramètre-liste*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|type construit (type générique qui a un argument de type spécifique fourni)|*argument de type* *generic-type-name*<br /><br />ou Gestionnaire de configuration<br /><br />*generic-type-name*&lt;*type-argument-List*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|type de fonction qui a un seul paramètre|*parameter-type1* -&gt; *return-type*|Une fonction qui prend un `int` et retourne un `string` type a`int -> string`|
|type de fonction qui a plusieurs paramètres|*paramètre-type1*  - Parameter- - type2&gt; ...-Return-type&gt; &gt;|Une fonction qui accepte un `int` et un `float` et retourne un `string` type.`int -> float -> string`|
|fonction d’ordre supérieur en tant que paramètre|(*fonction-type*)|`List.map`a le type`('a -> 'b) -> 'a list -> 'b list`|
|délégué|délégué de *type fonction*|`delegate of unit -> int`|
|type flexible|#*type-name*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Rubriques connexes

|Rubrique|Description|
|-----|-----------|
|[Types primitifs](primitive-types.md)|Décrit les types simples intégrés tels que les types intégraux, le type booléen et les types de caractères.|
|[Type d’unité](unit-type.md)|Décrit le `unit` type, un type qui a une valeur et qui est indiqué par (); équivaut à `void` dans C# et `Nothing` à Visual Basic.|
|[Tuples](tuples.md)|Décrit le type de tuple, un type qui se compose de valeurs associées de tout type groupées par paires, triples, quadruples, et ainsi de suite.|
|[Options](options.md)|Décrit le type d’option, un type qui peut avoir une valeur ou être vide.|
|[Listes](lists.md)|Décrit les listes, qui sont des séries immuables et ordonnées d’éléments du même type.|
|[Tableaux](arrays.md)|Décrit les tableaux, qui sont des jeux ordonnés d’éléments mutables du même type qui occupent un bloc de mémoire contigu et dont la taille est fixe.|
|[Séquences](sequences.md)|Décrit le type de séquence, qui représente une série logique de valeurs; les valeurs individuelles sont calculées uniquement si nécessaire.|
|[Enregistrements](records.md)|Décrit le type d’enregistrement, un petit agrégat des valeurs nommées.|
|[Unions discriminées](discriminated-unions.md)|Décrit le type d’union discriminée, un type dont les valeurs peuvent être l’un des ensembles de types possibles.|
|[Fonctions](./functions/index.md)|Décrit les valeurs de fonction.|
|[Classes](classes.md)|Décrit le type de classe, un type d’objet qui correspond à un type référence .NET. Les types de classe peuvent contenir des membres, des propriétés, des interfaces implémentées et un type de base.|
|[Structures](structures.md)|Décrit le `struct` type, un type d’objet qui correspond à un type valeur .net. Le `struct` type représente généralement un petit agrégat de données.|
|[Interfaces](interfaces.md)|Décrit les types d’interfaces, qui sont des types qui représentent un jeu de membres qui fournissent certaines fonctionnalités, mais qui ne contiennent pas de données. Un type d’interface doit être implémenté par un type d’objet pour être utile.|
|[Délégués](delegates.md)|Décrit le type délégué, qui représente une fonction sous la forme d’un objet.|
|[Énumérations](enumerations.md)|Décrit les types énumération, dont les valeurs appartiennent à un ensemble de valeurs nommées.|
|[Attributs](attributes.md)|Décrit les attributs, qui sont utilisés pour spécifier des métadonnées pour un autre type.|
|[Types d'exceptions](/.exception-handling/exception-types.md)|Décrit les exceptions, qui spécifient les informations d’erreur.|
