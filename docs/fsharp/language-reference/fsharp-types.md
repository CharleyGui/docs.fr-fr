---
title: Types
description: 'En savoir plus sur les types utilisés en F # et sur la manière dont les types F # sont nommés et décrits.'
ms.date: 08/15/2020
ms.openlocfilehash: a86d8e8f672d8399b02bb193ae04e1f0d46720b6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812066"
---
# <a name="f-types"></a>Types F#

Cette rubrique décrit les types utilisés dans F # et comment les types F # sont nommés et décrits.

## <a name="summary-of-f-types"></a>Résumé des types F #

Certains types sont considérés comme des *types primitifs*, tels que le type booléen `bool` et les types de virgules intégrales et à virgule flottante de différentes tailles, qui incluent des types pour les octets et les caractères. Ces types sont décrits dans [types primitifs](basic-types.md).

D’autres types intégrés au langage incluent des tuples, des listes, des tableaux, des séquences, des enregistrements et des unions discriminées. Si vous avez de l’expérience avec d’autres langages .NET et que vous apprenez F #, vous devez lire les rubriques pour chacun de ces types. Ces types spécifiques à F # prennent en charge les styles de programmation qui sont communs aux langages de programmation fonctionnelle. La plupart de ces types ont des modules associés dans la bibliothèque F # qui prennent en charge des opérations courantes sur ces types.

Le type d’une fonction comprend des informations sur les types de paramètres et le type de retour.

Le .NET Framework est la source de types d’objets, d’interfaces, de types délégués, etc. Vous pouvez définir vos propres types d’objets comme vous le feriez dans n’importe quel autre langage .NET.

En outre, le code F # peut définir des alias, qui sont des *abréviations de type*nommées, qui sont des noms alternatifs pour les types. Vous pouvez utiliser des abréviations de type lorsque le type peut changer à l’avenir et que vous souhaitez éviter de modifier le code qui dépend du type. Ou bien, vous pouvez utiliser une abréviation de type comme nom convivial pour un type qui peut rendre le code plus facile à lire et à comprendre.

F # fournit des types de collection utiles qui sont conçus avec la programmation fonctionnelle à l’esprit. L’utilisation de ces types de collections vous permet d’écrire du code plus fonctionnel dans le style. Pour plus d’informations, consultez [types de collections F #](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Syntaxe pour les types

Dans le code F #, vous devez souvent écrire les noms des types. Chaque type a une forme syntaxique, et vous utilisez ces formes syntaxiques dans les annotations de type, les déclarations de méthode abstraite, les déclarations déléguées, les signatures et d’autres constructions. Chaque fois que vous déclarez une nouvelle construction de programme dans l’interpréteur, l’interpréteur imprime le nom de la construction et la syntaxe de son type. Cette syntaxe peut être simplement un identificateur pour un type défini par l’utilisateur ou un identificateur intégré tel que pour `int` ou `string` , mais pour des types plus complexes, la syntaxe est plus complexe.

Le tableau suivant indique les aspects de la syntaxe de type pour les types F #.

|Type|Syntaxe de type|Exemples|
|----|-----------|--------|
|type primitif|*nom du type*|`int`<br /><br />`float`<br /><br />`string`|
|type d’agrégat (Class, structure, Union, record, enum, etc.)|*nom du type*|`System.DateTime`<br /><br />`Color`|
|abréviation de type|*type-abréviation-Name*|`bigint`|
|type qualifié complet|*Namespaces. type-name*<br /><br />ou<br /><br />*modules. type-nom*<br /><br />ou<br /><br />*Namespaces. modules. type-name*|`System.IO.StreamWriter`|
|tableau|*nom-type*[] ou<br /><br />tableau *de noms de types*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|tableau à deux dimensions|*nom-type*[,]|`int[,]`<br /><br />`float[,]`|
|tableau à trois dimensions|*nom-type*[,,]|`float[,,]`|
|tuple|*tapez-nom1* &#42; *type-name2* ...|Par exemple, `(1,'b',3)` a le type `int * char * int`|
|type générique|*type-* *type-generic-type-name*<br /><br />ou<br /><br />*generic-type-name* &lt; *type-parameter-list*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|type construit (type générique qui a un argument de type spécifique fourni)|*type-argument* *générique-type-nom*<br /><br />ou<br /><br />*generic-type-name* &lt; *type-argument-List*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|type de fonction qui a un seul paramètre|*paramètre-type1*  - &gt; *type de retour*|Une fonction qui prend un `int` et retourne un `string` type a `int -> string`|
|type de fonction qui a plusieurs paramètres|*paramètre-type1*  - &gt; *paramètre-type2*  - &gt; ...- &gt; *Return-type*|Une fonction qui accepte un `int` et un `float` et retourne un `string` type. `int -> float -> string`|
|fonction d’ordre supérieur en tant que paramètre|(*fonction-type*)|`List.map` a le type `('a -> 'b) -> 'a list -> 'b list`|
|délégué|délégué de *type fonction*|`delegate of unit -> int`|
|type flexible|#*nom du type*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Rubriques connexes

|Rubrique|Description|
|-----|-----------|
|[Types primitifs](basic-types.md)|Décrit les types simples intégrés tels que les types intégraux, le type booléen et les types de caractères.|
|[Unit, type](unit-type.md)|Décrit le `unit` type, un type qui a une valeur et qui est indiqué par (); équivalent à `void` en C# et `Nothing` en Visual Basic.|
|[Tuples](tuples.md)|Décrit le type de tuple, un type qui se compose de valeurs associées de tout type groupées par paires, triples, quadruples, et ainsi de suite.|
|[Options](options.md)|Décrit le type d’option, un type qui peut avoir une valeur ou être vide.|
|[Listes](lists.md)|Décrit les listes, qui sont des séries immuables et ordonnées d’éléments du même type.|
|[Tableaux](arrays.md)|Décrit les tableaux, qui sont des jeux ordonnés d’éléments mutables du même type qui occupent un bloc de mémoire contigu et dont la taille est fixe.|
|[Séquences](sequences.md)|Décrit le type de séquence, qui représente une série logique de valeurs ; les valeurs individuelles sont calculées uniquement si nécessaire.|
|[Enregistrements](records.md)|Décrit le type d’enregistrement, un petit agrégat des valeurs nommées.|
|[Unions discriminées](discriminated-unions.md)|Décrit le type d’union discriminée, un type dont les valeurs peuvent être l’un des ensembles de types possibles.|
|[Fonctions](./functions/index.md)|Décrit les valeurs de fonction.|
|[Classes](classes.md)|Décrit le type de classe, un type d’objet qui correspond à un type référence .NET. Les types de classe peuvent contenir des membres, des propriétés, des interfaces implémentées et un type de base.|
|[Structures](structures.md)|Décrit le `struct` type, un type d’objet qui correspond à un type valeur .net. Le `struct` type représente généralement un petit agrégat de données.|
|[Interfaces](interfaces.md)|Décrit les types d’interfaces, qui sont des types qui représentent un jeu de membres qui fournissent certaines fonctionnalités, mais qui ne contiennent pas de données. Un type d’interface doit être implémenté par un type d’objet pour être utile.|
|[Délégués](delegates.md)|Décrit le type délégué, qui représente une fonction sous la forme d’un objet.|
|[Énumérations](enumerations.md)|Décrit les types énumération, dont les valeurs appartiennent à un ensemble de valeurs nommées.|
|[Attributs](attributes.md)|Décrit les attributs, qui sont utilisés pour spécifier des métadonnées pour un autre type.|
|[Types d'exceptions](./exception-handling/exception-types.md)|Décrit les exceptions, qui spécifient les informations d’erreur.|
