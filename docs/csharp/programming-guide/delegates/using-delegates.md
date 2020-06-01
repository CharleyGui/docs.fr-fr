---
title: Utilisation de délégués - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: 9a81ee5ccdc2697ca435d40be27568b651977f96
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241589"
---
# <a name="using-delegates-c-programming-guide"></a>Utilisation de délégués (guide de programmation C#)

Un [délégué](../../language-reference/builtin-types/reference-types.md) est un type qui encapsule sans risque une méthode ; il est similaire à un pointeur de fonction en C et C++. Toutefois, à la différence des pointeurs de fonction C, les délégués sont orientés objet, de type sécurisé et sûrs. Le type d'un délégué est défini par le nom du délégué. L’exemple suivant déclare un délégué nommé `Del` qui peut encapsuler une méthode acceptant une chaîne ([string](../../language-reference/builtin-types/reference-types.md)) comme argument et qui retourne [void](../../language-reference/builtin-types/void.md) :

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Un objet de délégué est normalement construit en fournissant le nom de la méthode que le délégué encapsule, ou avec une [fonction anonyme](../statements-expressions-operators/anonymous-functions.md). Une fois qu'un délégué est instancié, un appel de méthode fait au délégué est transmis par le délégué à cette méthode. Les paramètres passés au délégué par l'appelant sont passés à la méthode et la valeur de retour de la méthode, le cas échéant, est retournée à l'appelant par le délégué. Cette opération est connue sous le nom d'appel du délégué. Un délégué instancié peut être appelé comme s'il s'agissait de la méthode encapsulée elle-même. Par exemple :

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

Les types délégués sont dérivés de la <xref:System.Delegate> classe dans .net. Les types délégués sont scellés ([sealed](../../language-reference/keywords/sealed.md)), c’est-à-dire qu’ils ne peuvent pas être faire l’objet d’une dérivation, et il n’est pas possible de dériver des classes personnalisées à partir de <xref:System.Delegate>. Étant donné que le délégué instancié est un objet, il peut être passé comme paramètre ou assigné à une propriété. Cela permet à une méthode d'accepter un délégué comme paramètre et d'appeler le délégué ultérieurement. Cette opération est connue sous le nom de rappel asynchrone et constitue une méthode courante pour notifier un appelant quand un long processus s'est achevé. Lorsqu'un délégué est ainsi utilisé, le code qui utilise le délégué n'a pas besoin de connaître l'implémentation de la méthode utilisée. La fonctionnalité est semblable à l'encapsulation que fournissent les interfaces.

Une autre utilisation courante des rappels consiste à définir une méthode de comparaison personnalisée et à passer ce délégué à une méthode de tri. Le code de l'appelant peut ainsi faire partie de l'algorithme de tri. L'exemple de méthode suivant utilise le type `Del` comme paramètre :

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Vous pouvez ensuite passer le délégué créé ci-dessus à cette méthode :

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

et vous recevez le résultat suivant sur la console :

```console
The number is: 3
```

En utilisant le délégué comme abstraction, `MethodWithCallback` n'a pas besoin d'appeler la console directement. La méthode n'a pas à être conçue en l'associant obligatoirement à une console. En effet, `MethodWithCallback` se contente de préparer une chaîne et de la passer à une autre méthode. Cela est particulièrement efficace, car une méthode déléguée peut utiliser n'importe quel nombre de paramètres.

Quand un délégué est construit pour encapsuler une méthode d'instance, le délégué fait référence à l'instance et à la méthode. Un délégué n'ayant aucune connaissance du type d'instance hormis la méthode qu'il encapsule, un délégué peut faire référence à n'importe quel type d'objet tant qu'il existe une méthode sur l'objet correspondant à la signature du délégué. Quand un délégué est construit pour encapsuler une méthode statique, il fait uniquement référence à la méthode. Prenons les déclarations suivantes :

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

Avec la méthode statique `DelegateMethod` montrée précédemment, nous avons désormais trois méthodes pouvant être encapsulées par une instance `Del`.

Un délégué peut appeler plusieurs méthodes quand il est appelé. Cette opération se nomme multidiffusion. L'ajout d'une méthode supplémentaire à la liste des méthodes du délégué – la liste d'invocation – nécessite simplement l'ajout de deux délégués à l'aide des opérateurs d'addition ou d'assignation d'addition (« + » ou « += »). Par exemple :

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

À ce stade, `allMethodsDelegate` contient trois méthodes dans sa liste d'invocation : `Method1`, `Method2` et `DelegateMethod`. Les trois délégués initiaux, `d1`, `d2` et `d3`, restent inchangés. Lors de l'appel de `allMethodsDelegate`, les trois méthodes sont appelées dans l'ordre. Si le délégué utilise des paramètres de référence, la référence est passée séquentiellement à chacune des trois méthodes et toute modification apportée par une méthode est visible dans la méthode suivante. Quand l'une des méthodes lève une exception qui n'est pas interceptée dans la méthode, cette exception est passée à l'appelant du délégué et aucune des méthodes suivantes dans la liste d'invocation n'est appelée. Si le délégué a une valeur de retour et/ou des paramètres out, il retourne la valeur de retour et les paramètres de la dernière méthode appelée. Pour supprimer une méthode de la liste d’appel, utilisez les opérateurs d’assignation de soustraction [ou de soustraction](../../language-reference/operators/subtraction-operator.md) ( `-` ou `-=` ). Par exemple :

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Étant donné que les types délégués sont dérivés de `System.Delegate`, les méthodes et les propriétés définies par cette classe peuvent être appelées sur le délégué. Par exemple, pour rechercher le nombre de méthodes dans la liste d'invocation d'un délégué, vous pouvez écrire :

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Les délégués ayant plusieurs méthodes dans leur liste d'invocation dérivent de <xref:System.MulticastDelegate>, qui est une sous-classe de `System.Delegate`. Le code ci-dessus fonctionne dans les deux cas, car les deux classes prennent en charge `GetInvocationList`.

Les délégués multicast sont largement utilisés dans la gestion des événements. Les objets sources d'événements envoient des notifications d'événement aux objets destinataires qui se sont inscrits pour recevoir cet événement. Pour s'inscrire à un événement, le destinataire crée une méthode conçue pour gérer l'événement, puis crée un délégué pour cette méthode et passe le délégué à la source d'événements. La source appelle le délégué quand l'événement se produit. Le délégué appelle ensuite la méthode de gestion d'événement sur le destinataire, en fournissant les données d'événement. Le type délégué d'un événement donné est défini par la source de l'événement. Pour plus d’informations, consultez [Événements](../events/index.md).

La comparaison de délégués de deux types différents assignés au moment de la compilation provoque une erreur de compilation. Si les instances de délégué sont statiquement du type `System.Delegate`, la comparaison est alors autorisée, mais retourne la valeur false à l'exécution. Par exemple :

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Délégués](./index.md)
- [Utilisation de la variance dans les délégués](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Variance dans les délégués](../concepts/covariance-contravariance/variance-in-delegates.md)
- [Utilisation de la variance pour les délégués génériques Func et Action](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Événements](../events/index.md)
