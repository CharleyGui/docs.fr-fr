---
title: Mots clés C#
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.custom: updateeachrelease
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 3392b92cbd77e5b3f895af99a71f33d2ab43fa15
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812313"
---
# <a name="c-keywords"></a>Mots clés C#

Les mots clés sont des identificateurs réservés prédéfinis, qui ont des significations spécifiques pour le compilateur. Ils ne peuvent pas être utilisés comme identificateurs dans votre programme, sauf s’ils incluent `@` comme préfixe. Par exemple, `@if` est un identificateur valide, mais pas `if`, car `if` est un mot clé.  
  
 Le premier tableau de cette rubrique répertorie les mots clés qui sont des identificateurs réservés quelle que soit la partie d’un programme C#. Le deuxième tableau de cette rubrique liste les mots clés contextuels en C#. Les mots clés contextuels ont une signification spéciale dans un contexte de programme limité ; ils peuvent être utilisés comme identificateurs en dehors de ce contexte. En règle générale, lorsque de nouveaux mots clés sont ajoutés au langage C#, ils sont ajoutés comme mots clés contextuels afin d’éviter l’interruption des programmes écrits dans les versions antérieures.  
  
|||||  
|---|---|---|---|  
|[abstraction](abstract.md)|[servir](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[études](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[désactivé](checked.md)|[class](class.md)|[const](const.md)|  
|[pouvoir](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[variables](../builtin-types/enum.md)|  
|[event](event.md)|[explicitement](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[suivie](try-finally.md)|[des](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[Implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[Lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[nouveau](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[à](out.md)|[override](override.md)|[params](params.md)|[priv](private.md)|
|[protected](protected.md)|[public](public.md)|[seulement](readonly.md)|[ref](ref.md)|
|[renvoi](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[modélis](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[lever](throw.md)|
|[true](../builtin-types/bool.md)|[Essayez](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[à](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[durant](while.md)|

## <a name="contextual-keywords"></a>Mots clés contextuels

 Un mot clé contextuel sert à donner une signification spécifique dans le code, sans pour autant être un mot réservé en C#. Certains mots clés contextuels, tels que `partial` et `where`, ont des significations spéciales dans deux contextes ou plus.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[par](by.md)|
|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[Généralités](../operators/namespace-alias-qualifier.md)|
|[groupe](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[Explor](let-clause.md)|[nameof](../operators/nameof.md)|[NOTNULL](../../programming-guide/generics/constraints-on-type-parameters.md#notnull-constraint)|
|[actif](on.md)|[TriPar](orderby-clause.md)|[Partial (type)](partial-type.md)|
|[Partial (méthode)](partial-method.md)|[remove](remove.md)|[select](select-clause.md)|
|[set](set.md)|[non managé (contrainte de type générique)](where-generic-type-constraint.md)|[value](value.md)|
|[var](var.md)|[when (condition de filtre)](when.md)|[where (contrainte de type générique)](where-generic-type-constraint.md)|
|[where (clause de requête)](where-clause.md)|[yield](yield.md)| |
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
