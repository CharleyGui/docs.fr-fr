---
title: Fonctions locales - Guide de programmation C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170233"
---
# <a name="local-functions-c-programming-guide"></a>Fonctions locales (Guide de programmation C#)

À compter de C# 7.0, C# prend en charge les *fonctions locales*. Les fonctions locales sont des méthodes privées d’un type qui sont imbriqués dans un autre membre. Elles ne peuvent être appelées qu’à partir de leur membre conteneur. Les fonctions locales peuvent être déclarées et appelées dans et à partir des éléments suivants :

- Méthodes, tout particulièrement les méthodes iterator et async
- Constructeurs
- Accesseurs de propriété
- Accesseurs d’événement
- Méthodes anonymes
- Expressions lambda
- Finaliseurs
- Autres fonctions locales

En revanche, les fonctions locales ne peuvent pas être déclarées à l’intérieur d’un membre expression-bodied.

> [!NOTE]
> Dans certains cas, vous pouvez utiliser une expression lambda pour implémenter la fonctionnalité également prise en charge par une fonction locale. Pour obtenir une comparaison, consultez [Fonctions locales comparées aux expressions lambda](../../local-functions-vs-lambdas.md).

Les fonctions locales permettent de clarifier l’objectif de votre code. Toute personne lisant votre code peut voir que la méthode n’est pas callable, sauf par la méthode contenant. Pour les projets d’équipe, elles empêchent aussi à un autre développeur d’appeler par inadvertance la méthode directement à partir d’un autre emplacement dans la classe ou le struct.

## <a name="local-function-syntax"></a>Syntaxe des fonctions locales

Une fonction locale est définie en tant que méthode imbriquée à l’intérieur d’un membre conteneur. Sa définition présente la syntaxe suivante :

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Les fonctions locales peuvent utiliser les modificateurs [async](../../language-reference/keywords/async.md) et [unsafe](../../language-reference/keywords/unsafe.md).

Notez que toutes les variables locales définies dans le membre conteneur, y compris ses paramètres de méthode, sont accessibles dans la fonction locale.

Contrairement à une définition de méthode, une définition de fonction locale ne peut pas inclure le modificateur d’accès du membre. Comme toutes les fonctions locales sont privées, l’inclusion d’un modificateur d’accès, tel que le mot clé `private`, génère l’erreur de compilateur CS0106 : « Le modificateur « private » n’est pas valide pour cet élément ».

> [!NOTE]
> Avant le C 8.0, les fonctions locales ne peuvent pas inclure le `static` modificateur. L’inclusion du mot clé `static` génère l’erreur de compilateur CS0106 : « Le modificateur « static » n’est pas valide pour cet élément ».

Par ailleurs, les attributs ne peuvent pas être appliqués à la fonction locale ou à ses paramètres et paramètres de type.

L’exemple suivant définit une fonction locale nommée `AppendPathSeparator` qui est privée pour une méthode nommée `GetText` :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Fonctions locales et exceptions

L’une des caractéristiques intéressantes des fonctions locales est qu’elles permettent l’affichage immédiat des exceptions. Pour les itérateurs de méthode, les exceptions apparaissent uniquement au moment où la séquence retournée est énumérée, et non à la récupération de l’itérateur. Pour les méthodes async, les exceptions levées dans une méthode async sont observées quand la tâche retournée est attendue.

L’exemple suivant définit une méthode `OddSequence` qui énumère les nombres impairs dans une plage spécifiée. Sachant qu’elle passe à la méthode d’énumérateur `OddSequence` un nombre supérieur à 100, la méthode lève une exception <xref:System.ArgumentOutOfRangeException>. Comme le montre la sortie de l’exemple, l’exception apparaît uniquement au moment d’itérer les nombres, et non à la récupération de l’énumérateur.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Au lieu de cela, vous pouvez lever une exception au moment d’effectuer la validation et avant la récupération de l’itérateur en retournant l’itérateur à partir d’une fonction locale, comme dans l’exemple suivant.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Les fonctions locales peuvent être utilisées de manière similaire pour gérer les exceptions en dehors de l’opération asynchrone. D’ordinaire, les exceptions levées dans la méthode async nécessitent que vous examiniez les exceptions internes d’un <xref:System.AggregateException>. Les fonctions locales permettent à votre code d’échouer rapidement et à votre exception d’être à la fois levée et observée de manière synchrone.

L’exemple suivant utilise une méthode asynchrone nommée `GetMultipleAsync` visant à marquer une pause pendant un nombre défini de secondes et retourner une valeur qui est un multiple aléatoire de ce nombre de secondes. Le délai maximal est de 5 secondes ; une exception <xref:System.ArgumentOutOfRangeException> est obtenue si la valeur est supérieure à 5. Comme le montre l’exemple suivant, l’exception qui est levée quand une valeur de 6 est passée à la méthode `GetMultipleAsync` est encapsulée dans une exception <xref:System.AggregateException> après que la méthode `GetMultipleAsync` a démarré son exécution.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Comme nous l’avons fait avec l’itérateur de méthode, nous pouvons refactoriser le code de cet exemple pour assurer la validation avant l’appel de la méthode asynchrone. Comme le montre la sortie de l’exemple suivant, l’exception <xref:System.ArgumentOutOfRangeException> n’est pas encapsulée dans une exception <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a>Voir aussi

- [Méthodes](methods.md)
