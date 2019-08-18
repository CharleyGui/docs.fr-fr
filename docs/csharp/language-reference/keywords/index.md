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
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 05a78def4a84fff24ff00d7c2c64320a76e4e707
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566348"
---
# <a name="c-keywords"></a>Mots clés C#

Les mots clés sont des identificateurs réservés prédéfinis, qui ont des significations spécifiques pour le compilateur. Ils ne peuvent pas être utilisés comme identificateurs dans votre programme, sauf s’ils incluent `@` comme préfixe. Par exemple, `@if` est un identificateur valide, mais pas `if`, car `if` est un mot clé.  
  
 Le premier tableau de cette rubrique répertorie les mots clés qui sont des identificateurs réservés quelle que soit la partie d’un programme C#. Le deuxième tableau de cette rubrique liste les mots clés contextuels en C#. Les mots clés contextuels ont une signification spéciale dans un contexte de programme limité ; ils peuvent être utilisés comme identificateurs en dehors de ce contexte. En règle générale, lorsque de nouveaux mots clés sont ajoutés au langage C#, ils sont ajoutés comme mots clés contextuels afin d’éviter l’interruption des programmes écrits dans les versions antérieures.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[fixed](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](object.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[try](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[using static](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Mots clés contextuels

 Un mot clé contextuel sert à donner une signification spécifique dans le code, sans pour autant être un mot réservé en C#. Certains mots clés contextuels, tels que `partial` et `where`, ont des significations spéciales dans deux contextes ou plus.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](dynamic.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[global](../operators/namespace-alias-qualifier.md)|
|[group](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[let](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[orderby](orderby-clause.md)|[partial (type)](partial-type.md)|[partial (méthode)](partial-method.md)|
|[remove](remove.md)|[select](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (condition de filtre)](when.md)|
|[where (contrainte de type générique)](where-generic-type-constraint.md)|[where (clause de requête)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
