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
ms.openlocfilehash: 251046a8bd825a90d817965f9f747d08d4492197
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102032"
---
# <a name="c-keywords"></a>Mots clés C#

Les mots clés sont des identificateurs réservés prédéfinis, qui ont des significations spécifiques pour le compilateur. Ils ne peuvent pas être utilisés comme identificateurs dans votre programme, sauf s’ils incluent `@` comme préfixe. Par exemple, `@if` est un identificateur valide, mais pas `if`, car `if` est un mot clé.  
  
 Le premier tableau de cette rubrique répertorie les mots clés qui sont des identificateurs réservés quelle que soit la partie d’un programme C#. Le deuxième tableau de cette rubrique liste les mots clés contextuels en C#. Les mots clés contextuels ont une signification spéciale dans un contexte de programme limité ; ils peuvent être utilisés comme identificateurs en dehors de ce contexte. En règle générale, lorsque de nouveaux mots clés sont ajoutés au langage C#, ils sont ajoutés comme mots clés contextuels afin d’éviter l’interruption des programmes écrits dans les versions antérieures.  
  
|||||  
|---|---|---|---|  
|[Abstrait](abstract.md)|[Comme](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[Pause](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[Cas](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[Vérifié](checked.md)|[class](class.md)|[const](const.md)|  
|[Continuer](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[Par défaut](default.md)|[Délégué](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[event](event.md)|[Explicite](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[Enfin](try-finally.md)|[Fixe](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[Goto](goto.md)|[if](if-else.md)|[Implicite](../operators/user-defined-conversion-operators.md)|  
|[Dans](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[Est](is.md)|[Verrouillage](lock-statement.md)|[Long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[Null](null.md)|[Objet](../builtin-types/reference-types.md)|[Opérateur](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[Public](public.md)|[Readonly](readonly.md)|[ref](ref.md)|
|[Retour](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[Court](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[Interrupteur](switch.md)|[this](this.md)|[Jeter](throw.md)|
|[true](../builtin-types/bool.md)|[Essayer](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[Ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[Dangereux](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[Tandis que](while.md)|

## <a name="contextual-keywords"></a>Mots clés contextuels

 Un mot clé contextuel sert à donner une signification spécifique dans le code, sans pour autant être un mot réservé en C#. Certains mots clés contextuels, tels que `partial` et `where`, ont des significations spéciales dans deux contextes ou plus.  
  
||||  
|---|---|---|  
|[add](add.md)|[Alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[Attendent](../operators/await.md)|[Par](by.md)|
|[descending](descending.md)|[dynamique](../builtin-types/reference-types.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[Mondiale](../operators/namespace-alias-qualifier.md)|
|[groupe](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[Laisser](let-clause.md)|[nameof](../operators/nameof.md)|[Sur](on.md)|
|[Orderby](orderby-clause.md)|[partielle (type)](partial-type.md)|[partielle (méthode)](partial-method.md)|
|[retirer](remove.md)|[Sélectionnez](select-clause.md)|[Ensemble](set.md)|
|[non gestion (contrainte de type générique)](where-generic-type-constraint.md)|[value](value.md)|[Var](var.md)|
|[when (condition de filtre)](when.md)|[where (contrainte de type générique)](where-generic-type-constraint.md)|[where (clause de requête)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
