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
ms.openlocfilehash: 928917d25b5f3f97c4b8cdff85efdaa1957be41e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399314"
---
# <a name="c-keywords"></a>Mots clés C#

Les mots clés sont des identificateurs réservés prédéfinis, qui ont des significations spécifiques pour le compilateur. Ils ne peuvent pas être utilisés comme identificateurs dans votre programme, sauf s’ils incluent `@` comme préfixe. Par exemple, `@if` est un identificateur valide, mais pas `if`, car `if` est un mot clé.  
  
 Le premier tableau de cette rubrique répertorie les mots clés qui sont des identificateurs réservés quelle que soit la partie d’un programme C#. Le deuxième tableau de cette rubrique liste les mots clés contextuels en C#. Les mots clés contextuels ont une signification spéciale dans un contexte de programme limité ; ils peuvent être utilisés comme identificateurs en dehors de ce contexte. En règle générale, lorsque de nouveaux mots clés sont ajoutés au langage C#, ils sont ajoutés comme mots clés contextuels afin d’éviter l’interruption des programmes écrits dans les versions antérieures.  
  
|||||  
|---|---|---|---|  
|[Abstrait](abstract.md)|[Comme](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[Bool](../builtin-types/bool.md)|  
|[Pause](break.md)|[Octet](../builtin-types/integral-numeric-types.md)|[cas](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[cochée](checked.md)|[Classe](class.md)|[const](const.md)|  
|[Continuer](continue.md)|[Decimales](../builtin-types/floating-point-numeric-types.md)|[Par défaut](default.md)|[Délégué](../builtin-types/reference-types.md)|  
|[faire](do.md)|[Double](../builtin-types/floating-point-numeric-types.md)|[Autre](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[Événement](event.md)|[Explicite](../operators/user-defined-conversion-operators.md)|[Extern](extern.md)|[false](../builtin-types/bool.md)|  
|[Enfin](try-finally.md)|[Fixe](fixed-statement.md)|[Flotteur](../builtin-types/floating-point-numeric-types.md)|[Pour](for.md)|  
|[Foreach](foreach-in.md)|[Goto](goto.md)|[Si](if-else.md)|[Implicite](../operators/user-defined-conversion-operators.md)|  
|[Dans](in.md)|[int](../builtin-types/integral-numeric-types.md)|[Interface](interface.md)|[Interne](internal.md)|
|[Est](is.md)|[Verrouillage](lock-statement.md)|[Long](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[Nouveau](../operators/new-operator.md)|[Null](null.md)|[Objet](../builtin-types/reference-types.md)|[Opérateur](../operators/operator-overloading.md)|
|[out](out.md)|[Substituer](override.md)|[Params](params.md)|[Privé](private.md)|
|[Protégé](protected.md)|[public](public.md)|[Readonly](readonly.md)|[ref](ref.md)|
|[Retour](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[Statique](static.md)|[String](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[Interrupteur](switch.md)|[Ce](this.md)|[Jeter](throw.md)|
|[true](../builtin-types/bool.md)|[Essayer](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[Ulong](../builtin-types/integral-numeric-types.md)|[non cochée](unchecked.md)|[Dangereux](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[Utilisant](using.md)|[using static](using-static.md)|[Virtuel](virtual.md)|[void](../builtin-types/void.md)|
|[Volatile](volatile.md)|[Tandis que](while.md)|

## <a name="contextual-keywords"></a>Mots clés contextuels

 Un mot clé contextuel sert à donner une signification spécifique dans le code, sans pour autant être un mot réservé en C#. Certains mots clés contextuels, tels que `partial` et `where`, ont des significations spéciales dans deux contextes ou plus.  
  
||||  
|---|---|---|  
|[ajouter](add.md)|[alias](extern-alias.md)|[Ascendant](ascending.md)|
|[Async](async.md)|[Attendent](../operators/await.md)|[Par](by.md)|
|[Descendant](descending.md)|[Dynamique](../builtin-types/reference-types.md)|[Égale](equals.md)|
|[De](from-clause.md)|[get](get.md)|[globale](../operators/namespace-alias-qualifier.md)|
|[groupe](group-clause.md)|[en](into.md)|[Rejoindre](join-clause.md)|
|[Laisser](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[Orderby](orderby-clause.md)|[partial (type)](partial-type.md)|[partial (méthode)](partial-method.md)|
|[retirer](remove.md)|[Sélectionnez](select-clause.md)|[Ensemble](set.md)|
|[non gestion (contrainte de type générique)](where-generic-type-constraint.md)|[value](value.md)|[Var](var.md)|
|[when (condition de filtre)](when.md)|[where (contrainte de type générique)](where-generic-type-constraint.md)|[where (clause de requête)](where-clause.md)|
|[Rendement](yield.md)| | |
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
