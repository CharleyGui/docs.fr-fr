---
title: Les valeurs de retour de référence et variables locales ref (Guide C#)
description: Découvrir comment définir et utiliser des valeurs de retour de référence et des variables locales ref
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170071"
---
# <a name="ref-returns-and-ref-locals"></a>Retours ref et variables locales ref

À compter de C# 7.0, C# prend en charge les valeurs de retour de référence (retours ref). Une valeur de retour de référence permet à une méthode de retourner à un appelant une référence à une variable, plutôt qu’à une valeur. L’appelant peut alors choisir de traiter la variable retournée comme si elle était retournée par valeur ou par référence. L’appelant peut créer une nouvelle variable qui est elle-même une référence à la valeur retournée, appelée variable locale ref.

## <a name="what-is-a-reference-return-value"></a>Qu’est-ce qu’une valeur de retour de référence ?

La plupart des développeurs sont familiarisés avec le passage d’un argument à une méthode appelée *par référence*. La liste d’arguments d’une méthode appelée inclut une variable passée par référence. Chaque modification de sa valeur par la méthode appelée est respectée par l’appelant. Une *valeur de retour de référence* signifie qu’une méthode retourne une *référence* (ou un alias) à une variable. L’étendue de cette variable doit inclure la méthode. La durée de vie de cette variable doit s’étendre au-delà du retour de la méthode. Des modifications apportées par l’appelant à la valeur de retour de la méthode portent sur la variable qui est retournée par la méthode.

La déclaration qu’une méthode retourne une *valeur de retour de référence* indique que la méthode retourne un alias vers une variable. L’intention de conception est souvent que le code appelant ait accès à cette variable à travers l’alias, et qu’il puisse également la modifier. C’est pourquoi les méthodes de retour par référence ne peuvent pas avoir le type de retour `void`.

Certaines restrictions s’appliquent à l’expression qu’une méthode peut retourner comme valeur de retour de référence. Les restrictions sont les suivantes :

- La valeur de retour doit avoir une durée de vie qui s’étend au-delà de l’exécution de la méthode. En d’autres termes, il ne peut pas s’agir d’une variable locale dans la méthode qui la retourne. Il peut s’agir d’un champ d’instance ou statique d’une classe, ou bien un argument passé à la méthode. Une tentative de retour d’une variable locale génère l’erreur du compilateur CS8168, « Impossible de retourner la variable locale 'obj' par référence, car il ne s’agit pas d’une variable locale de référence ».

- La valeur de retour ne peut pas être le littéral `null`. Le retour de `null` génère l’erreur de compilateur CS8156, « Impossible d’utiliser une expression dans ce contexte, car elle ne peut pas être retournée par référence ».

   Une méthode avec un retour d’arbitre peut retourner un alias à une variable dont la valeur est actuellement la valeur nulle (non corroborée) ou un [type de valeur nul](../../language-reference/builtin-types/nullable-value-types.md) pour un type de valeur.

- La valeur de retour ne peut pas être une constante, un membre d’énumération, la valeur de retour par valeur d’une propriété, ou une méthode d’une `class` ou d’un `struct`. Le non-respect de cette règle génère l’erreur de compilateur CS8156, « Impossible d’utiliser une expression dans ce contexte, car elle ne peut pas être retournée par référence ».

En outre, les valeurs de retour de référence ne sont pas autorisées sur les méthodes asynchrones. Une méthode asynchrone peut être retournée avant la fin de son exécution, même si sa valeur de retour est encore inconnue.

## <a name="defining-a-ref-return-value"></a>Définition d’une valeur de retour de référence

Une méthode qui retourne une *valeur de retour de référence* doit remplir les deux conditions suivantes :

- Dans la signature de méthode, le mot clé [ref](../../language-reference/keywords/ref.md) précède le type de retour.
- Pour chaque instruction [return](../../language-reference/keywords/return.md) dans le corps de la méthode, le mot clé [ref](../../language-reference/keywords/ref.md) précède le nom de l’instance retournée.

L’exemple suivant montre une méthode qui remplit ces conditions et retourne une référence à un objet `Person` nommé `p` :

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Utilisation d’une valeur de retour de référence

La valeur de retour de référence est l’alias vers une autre variable dans l’étendue de la méthode appelée. Toute utilisation d’une valeur de retour de référence revient à utiliser la variable dont elle est l’alias :

- Quand vous lui affectez une valeur, vous affectez une valeur à la variable dont elle est l’alias.
- Quand vous lisez sa valeur, vous lisez la valeur de la variable dont elle est l’alias.
- Si vous la retournez *par référence*, vous retournez un alias vers cette même variable.
- Si vous la passez à une autre méthode *par référence*, vous passez une référence à la variable dont elle est l’alias.
- Quand vous créez un alias de [variable locale ref](#ref-locals), vous créez un nouvel alias vers la même variable.

## <a name="ref-locals"></a>Variables locales ref

Partez du principe que la méthode `GetContactInformation` est déclarée comme un retour de référence :

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Une affectation par valeur lit la valeur d’une variable et l’affecte à une nouvelle variable :

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

L’affectation précédente déclare `p` comme une variable locale. Sa valeur initiale est copiée à partir de la lecture de la valeur retournée par `GetContactInformation`. Toute affectation future à `p` ne modifiera en rien la valeur de la variable renvoyée par `GetContactInformation`. La variable `p` n’est plus un alias vers la variable retournée.

Vous déclarez une variable *locale ref* pour copier l’alias vers la valeur d’origine. Dans l’affectation suivante, `p` est un alias vers la variable retournée à partir de `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

L’utilisation ultérieure de `p` revient à utiliser la variable retournée par `GetContactInformation`, car `p` est un alias de cette variable. Les modifications apportées à `p` modifient également la variable retournée à partir de `GetContactInformation`.

Le mot clé `ref` est utilisé à la fois avant la déclaration de la variable locale *et* avant l’appel de la méthode.

Vous pouvez accéder à une valeur par référence de la même façon. Dans certains cas, l’accès à une valeur par référence augmente les performances en évitant une opération de copie potentiellement coûteuse. Par exemple, l’instruction suivante montre comment il est possible de définir une valeur locale ref qui est utilisée pour référencer une valeur.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Le mot clé `ref` est utilisé à la fois avant la déclaration de la variable locale *et* avant la valeur du second exemple. Si les deux mots clés `ref` ne sont pas inclus dans la déclaration et l’affectation de la variable dans les deux exemples, l’erreur du compilateur CS8172, « Impossible d’initialiser une variable par référence avec une valeur » est générée.

Dans les versions antérieures à C# 7.3, les variables locales ref ne pouvaient pas être réassignées pour référencer un stockage différent après avoir été initialisées. Cette restriction a été supprimée. L’exemple suivant illustre une réassignation :

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Les variables locales ref doivent toujours être initialisées quand elles sont déclarées.

## <a name="ref-returns-and-ref-locals-an-example"></a>Retours ref et variables locales ref : exemple

L’exemple suivant définit une classe `NumberStore` qui stocke un tableau de valeurs entières. La méthode `FindNumber` retourne par référence le premier nombre supérieur ou égal au nombre passé comme argument. Si aucun nombre n’est supérieur ou égal à l’argument, la méthode retourne le nombre se trouvant à l’index 0.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

L’exemple suivant appelle la méthode `NumberStore.FindNumber` pour récupérer la première valeur supérieure ou égale à 16. L’appelant multiplie ensuite par deux la valeur retournée par la méthode. La sortie de l’exemple montre comment la modification est reflétée dans la valeur des éléments de tableau de l’instance `NumberStore`.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Si les valeurs de retour de référence ne sont pas prises en charge, une telle opération est effectuée en retournant l’index de l’élément de tableau ainsi que sa valeur de retour. L’appelant peut ensuite utiliser cet index pour modifier la valeur dans un appel de méthode distinct. Toutefois, l’appelant peut également modifier l’index pour accéder à d’autres valeurs de tableau et éventuellement les modifier.  

L’exemple suivant montre comment réécrire la méthode `FindNumber` à compter de C# 7.3 pour utiliser la réassignation des variables locales ref :

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Cette deuxième version est plus efficace avec des séquences plus longues dans les scénarios où le nombre recherché est proche de la fin du tableau.

## <a name="see-also"></a>Voir aussi

- [ref, mot clé](../../language-reference/keywords/ref.md)
- [Écrire du code sécurisé et efficace](../../write-safe-efficient-code.md)
