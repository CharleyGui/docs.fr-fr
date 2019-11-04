---
title: Contraintes
description: En savoir F# plus sur les contraintes qui s’appliquent aux paramètres de type générique pour spécifier les conditions requises pour un argument de type dans un type ou une fonction générique.
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425021"
---
# <a name="constraints"></a>Contraintes

Cette rubrique décrit les contraintes que vous pouvez appliquer aux paramètres de type générique pour spécifier les conditions requises pour un argument de type dans un type ou une fonction générique.

## <a name="syntax"></a>Syntaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Notes

Vous pouvez appliquer plusieurs contraintes pour limiter les types qui peuvent être utilisés dans un type générique. Le tableau suivant répertorie et décrit ces contraintes.

|Contrainte|Syntaxe|Description|
|----------|------|-----------|
|Contrainte de type|*paramètre de type* : *type* de&gt;|Le type fourni doit être égal au ou dérivé du type spécifié, ou, si le type est une interface, le type fourni doit implémenter l’interface.|
|Contrainte null|*paramètre de type* : null|Le type fourni doit prendre en charge le littéral null. Cela comprend tous les types d’objets .NET F# , mais pas les types de liste, de tuple, de fonction, de classe, d’enregistrement ou d’Union.|
|Contrainte de membre explicite|[(]*paramètre de type* [ou... ou *paramètre de type*)] : (*signature de membre*)|Au moins un des arguments de type fourni doit avoir un membre qui a la signature spécifiée ; non destiné à une utilisation courante. Les membres doivent être définis explicitement sur le type ou une partie d’une extension de type implicite comme des cibles valides pour une contrainte de membre explicite.|
|Contrainte de constructeur|*paramètre de type* : (New : unit-&gt; 'a)|Le type fourni doit avoir un constructeur sans paramètre.|
|Contrainte de type valeur|: struct|Le type fourni doit être un type valeur .NET.|
|Contrainte de type référence|: non struct|Le type fourni doit être un type référence .NET.|
|Contrainte de type énumération|: enum&lt;&gt; *de type sous-jacent*|Le type fourni doit être un type énuméré qui a le type sous-jacent spécifié ; non destiné à une utilisation courante.|
|Déléguer la contrainte|: Delegate&lt;*Tuple-Parameter-type*, *Return-type*&gt;|Le type fourni doit être un type délégué qui a les arguments et la valeur de retour spécifiés ; non destiné à une utilisation courante.|
|Contrainte de comparaison|: comparaison|Le type fourni doit prendre en charge la comparaison.|
|Contrainte d’égalité|: égalité|Le type fourni doit prendre en charge l’égalité.|
|Contrainte non managée|: non managé|Le type fourni doit être un type non managé. Les types non managés sont soit certains types primitifs (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, ou `decimal`), les types énumération, `nativeptr<_>`ou une structure non générique dont les champs sont tous des types non managés.|

Vous devez ajouter une contrainte lorsque votre code doit utiliser une fonctionnalité qui est disponible sur le type de contrainte, mais pas sur les types en général. Par exemple, si vous utilisez la contrainte de type pour spécifier un type de classe, vous pouvez utiliser l’une des méthodes de cette classe dans la fonction ou le type générique.

La spécification de contraintes est parfois nécessaire lors de l’écriture explicite des paramètres de type, car sans contrainte, le compilateur n’a aucun moyen de vérifier que les fonctionnalités que vous utilisez seront disponibles sur tous les types susceptibles d’être fournis au moment de l’exécution pour le type paramètre.

Les contraintes les plus courantes que vous F# utilisez dans le code sont les contraintes de type qui spécifient des classes ou des interfaces de base. Les autres contraintes sont utilisées par la F# bibliothèque pour implémenter certaines fonctionnalités, telles que la contrainte de membre explicite, qui est utilisée pour implémenter la surcharge d’opérateur pour les opérateurs arithmétiques, ou F# qui sont fournies principalement parce que prend en charge l’ensemble complet de contraintes qui est pris en charge par l’common language runtime.

Pendant le processus d’inférence de type, certaines contraintes sont déduites automatiquement par le compilateur. Par exemple, si vous utilisez l’opérateur `+` dans une fonction, le compilateur déduit une contrainte de membre explicite sur les types de variable utilisés dans l’expression.

Le code suivant illustre certaines déclarations de contrainte :

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> =
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>Voir aussi

- [Génériques](index.md)
- [Contraintes](constraints.md)
