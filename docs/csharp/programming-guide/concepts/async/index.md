---
title: Programmation asynchrone en C#
description: Vue d’ensemble de la prise en charge du langage C# pour la programmation asynchrone avec Async, Await, Task et Task<T>
ms.date: 06/04/2020
ms.openlocfilehash: 992ccd3a015653ea9ee13dfc309d47711ad0fca4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619713"
---
# <a name="asynchronous-programming-with-async-and-await"></a>Programmation asynchrone avec Async et Await

Le [modèle de programmation asynchrone de tâche (TAP)](task-asynchronous-programming-model.md) fournit une abstraction sur le code asynchrone. Pour cela, vous écrivez votre code comme d’habitude, sous la forme d’une suite d’instructions. Vous pouvez lire ce code comme si chaque instruction se terminait avant que la suivante ne commence. Le compilateur effectue un certain nombre de transformations, car certaines de ces instructions peuvent commencer le travail et retourner un <xref:System.Threading.Tasks.Task> qui représente le travail en cours.

C’est en fait l’objectif de cette syntaxe : permettre au code d’être lu comme une suite d’instructions, mais d’être exécuté dans un ordre beaucoup plus complexe, en fonction de l’allocation des ressources externes et du moment auquel se terminent les tâches. Cela revient à donner des instructions pour des processus qui comprennent des tâches asynchrones. Tout au long de cet article, vous allez utiliser un exemple d’instructions pour créer un petit-déjeuner afin de voir comment les mots clés et facilitent la création de `async` `await` code, qui comprend une série d’instructions asynchrones. Pour expliquer comment préparer un petit-déjeuner, vous pourriez écrire des instructions telles que les suivantes :

1. Verser le café dans une tasse.
1. Faire chauffer la poêle, puis faire cuire deux œufs au plat.
1. Faire frire trois tranches de bacon.
1. Faire toaster deux tranches de pain.
1. Étaler le beurre et la confiture sur les toasts.
1. Verser du jus d’orange dans un verre.

Si vous avez l’habitude de cuisiner, vous savez que ces instructions doivent être exécutées de manière **asynchrone**. En effet, vous commencez par faire chauffer la poêle pour les œufs, mais vous faites d’abord frire le bacon. Ensuite, vous mettez les tranches de pain dans le grille-pain, puis vous cassez les œufs dans la poêle. À chaque étape du processus, vous démarrez une tâche, puis déplacez votre attention vers les tâches qui sont prêtes à être réalisées.

La préparation du petit-déjeuner est un bon exemple de travail asynchrone mais non parallèle. Une personne (ou un thread) peut gérer toutes ces tâches. Pour poursuivre l’analogie avec le petit-déjeuner, une personne peut préparer le petit-déjeuner de façon asynchrone en démarrant une tâche avant que la précédente ne soit terminée. En outre, la cuisson se poursuit, que vous la surveilliez ou non. Dès que vous commencez à faire chauffer la poêle pour les œufs, vous pouvez mettre le bacon à frire. Quand le bacon est en train de frire, vous pouvez mettre les tranches de pain dans le grille-pain.

Pour un algorithme parallèle, vous auriez besoin de plusieurs cuisiniers (ou threads). L’un d’eux s’occuperait des œufs, un autre du bacon, etc. Chacun d’eux serait concentré sur une seule tâche. Chaque cuisinier (ou thread) serait bloqué de façon synchrone, car il devrait attendre que le bacon soit prêt à être retourné ou que le pain soit grillé.

Écrivons maintenant ces instructions sous la forme d’instructions C# :

:::code language="csharp" source="snippets/index/AsyncBreakfast-starter/Program.cs" highlight="8-27":::

:::image type="content" source="media/synchronous-breakfast.png" alt-text="petit-déjeuner synchrone":::

Le petit déjeuner préparé de façon synchrone a duré environ 30 minutes, car le total est la somme de chaque tâche individuelle.

> [!NOTE]
> Les `Coffee` classes,,, `Egg` `Bacon` `Toast` et `Juice` sont vides. Il s’agit simplement de classes de marqueurs à des fins de démonstration, ne contiennent aucune propriété et n’a aucune autre fonction.

Les ordinateurs n’interprètent pas ces instructions de la même façon que les humains. L’ordinateur se bloque à chaque instruction jusqu’à ce que le travail soit terminé, avant de passer à l’instruction suivante. Avec une telle manière de procéder, notre petit-déjeuner risque de ne pas être très satisfaisant. En effet, chacune des tâches ne pourrait être démarrée qu’une fois la précédente terminée. De cette façon, la préparation du petit-déjeuner prendrait beaucoup plus de temps, et certains aliments refroidiraient avant d’être servis.

Si vous souhaitez que l’ordinateur exécute les instructions ci-dessus de façon asynchrone, vous devez écrire du code asynchrone.

De nos jours, ces remarques sont très importantes pour l’écriture de programmes. Lorsque vous écrivez des programmes clients, l’interface utilisateur doit être réactive aux entrées utilisateur. Votre application ne doit pas donner l’impression que votre smartphone se bloque pour télécharger des données à partir du web. Lorsque vous écrivez des programmes de serveur, vous ne devez pas bloquer les threads. En effet, ces threads peuvent servir à d’autres requêtes. Lorsque d’autres alternatives sont possibles, il est dommage d’utiliser du code synchrone, car celui-ci ne vous permet pas de réduire les frais des scale-out. Les threads bloqués ont un prix.

Une application moderne efficace a besoin de code asynchrone. Avant la prise en charge du langage, l’écriture de code asynchrone nécessitait des rappels, des événements de complétion ou d’autres méthodes qui masquaient l’objectif premier du code. L’avantage du code synchrone est qu’il est facile à comprendre. Les actions détaillées étape par étape facilitent son parcours et sa compréhension. Les modèles asynchrones traditionnels vous obligeaient à vous concentrer sur la nature asynchrone du code, et non sur ses actions fondamentales.

## <a name="dont-block-await-instead"></a>Éviter les blocages avec Await

Le code précédent montre une pratique déconseillée : écrire du code synchrone pour effectuer des opérations asynchrones. Comme nous l’avons vu, ce code bloque le thread, qui ne peut pas exécuter d’autres tâches. Il ne sera pas interrompu tant que l’une des tâches est en cours d’exécution. Ce serait comme rester les yeux fixés sur le grille-pain après avoir mis le pain dedans. Vous n’écouteriez personne tant que le pain ne serait pas ressorti du grille-pain.

Commençons par mettre à jour ce code pour que le thread ne se bloque pas pendant l’exécution des tâches. Le mot clé `await` permet de démarrer une tâche sans bloquer le thread, puis de poursuivre l’exécution une fois cette tâche terminée. La version asynchrone du code de préparation du petit-déjeuner ressemblerait à l’extrait de code suivant :

:::code language="csharp" source="snippets/index/AsyncBreakfast-V2/Program.cs" id="SnippetMain":::

> [!IMPORTANT]
> Le temps total écoulé est à peu près identique à la version initiale de Synchonous. Le code n’a pas encore pu tirer parti de certaines des fonctionnalités clés de la programmation asynchrone.

> [!TIP]
> Les corps de méthode des `FryEggsAsync` , `FryBaconAsync` et `ToastBreadAsync` ont tous été mis à jour pour retourner `Task<Egg>` , `Task<Bacon>` et `Task<Toast>` respectivement. Les méthodes sont renommées à partir de leur version d’origine pour inclure le suffixe « Async ». Leurs implémentations sont indiquées dans le cadre de la [version finale](#final-version) plus loin dans cet article.

Ce code ne se bloque pas pendant la cuisson des œufs ou du bacon. Cependant, il ne démarre pas d’autres tâches. Cela reviendrait, une nouvelle fois, à rester les yeux fixés sur le grille-pain en attendant que le pain ressorte. Mais au moins, vous seriez en mesure de répondre à quelqu’un qui aurait besoin de votre attention. Dans un restaurant qui doit gérer plusieurs commandes en même temps, le chef peut commencer un petit-déjeuner pendant qu’un autre est en cours de préparation.

Ici, le thread qui prépare le petit-déjeuner n’est pas bloqué en attendant qu’une tâche démarrée se termine. Pour certaines applications, cette modification est la seule nécessaire. Ce simple changement permet à une application GUI de continuer à répondre à l’utilisateur. Toutefois, pour ce scénario, d’autres modifications sont nécessaires. Il n’est pas souhaitable que chaque tâche de composant soit exécutée de manière séquentielle. Il est préférable de démarrer chacune des tâches de composant avant d’attendre l’achèvement de la tâche précédente.

## <a name="start-tasks-concurrently"></a>Démarrer plusieurs tâches simultanément

Dans de nombreux scénarios, il est nécessaire de démarrer plusieurs tâches immédiatement. Ensuite, à la fin de chaque tâche, vous pouvez passer aux autres tâches qui sont prêtes. C’est de cette façon que nous pouvons accélérer la préparation de notre petit-déjeuner. Cela permet également de tout terminer en même temps, ou presque. Cette façon de procéder vous garantit que vous mangerez votre petit-déjeuner bien chaud.

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et les types associés sont des classes que vous pouvez utiliser pour organiser les tâches en cours. Cela vous permet d’écrire du code qui se rapproche davantage de la façon dont vous devez préparer un petit-déjeuner, puisque vous commencez à faire cuire les œufs, à faire frire le bacon et à faire griller le pain simultanément. Puisque toutes ces tâches nécessitent une action, vous devez porter votre attention sur une tâche, démarrer l’action suivante, puis attendre qu’une autre tâche nécessite votre attention.

Vous démarrez une tâche puis vous gardez l’objet <xref:System.Threading.Tasks.Task> qui représente le travail. Vous devez attendre (`await`) chaque tâche avant d’utiliser ses résultats.

À présent, apportons ces modifications au code de notre petit-déjeuner. La première étape consiste à stocker les tâches des opérations dès leur démarrage, plutôt que d’attendre la fin de leur exécution :

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");

Task<Bacon> baconTask = FryBaconAsync(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Task<Toast> toastTask = ToastBreadAsync(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");

Juice oj = PourOJ();
Console.WriteLine("oj is ready");
Console.WriteLine("Breakfast is ready!");
```

Ensuite, vous pouvez déplacer les instructions `await` pour le bacon et les œufs à la fin de la méthode, avant de servir le petit-déjeuner :

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Task<Bacon> baconTask = FryBaconAsync(3);
Task<Toast> toastTask = ToastBreadAsync(2);

Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

:::image type="content" source="media/asynchronous-breakfast.png" alt-text="petit-déjeuner asynchrone":::

Le petit déjeuner préparé de façon asynchrone a duré environ 20 minutes, car certaines tâches pouvaient s’exécuter simultanément.

Le code précédent est plus efficace. Vous y démarrez toutes les tâches asynchrones en même temps. Vous n’attendez la fin d’une tâche que si vous avez besoin des résultats. Le code précédent est semblable au code des applications web qui envoient des requêtes à différents microservices, puis qui combinent les résultats au sein d’une même page. Vous allez exécuter toutes les requêtes en même temps, puis vous allez attendre (`await`) toutes ces tâches pour composer la page web.

## <a name="composition-with-tasks"></a>Composition de tâches

 Tout est prêt en même temps pour votre petit-déjeuner, sauf les toasts. La préparation des toasts correspond à la composition d’une opération asynchrone (faire griller le pain) et d’opérations synchrones (ajouter du beurre et de la confiture). Le code ci-dessous illustre un concept important :

> [!IMPORTANT]
> La composition d’une opération asynchrone et d’une tâche synchrone constitue une opération asynchrone. Autrement dit, si une partie d’une opération est asynchrone, cela rend asynchrone l’intégralité de l’opération.

Le code précédent montre que vous pouvez utiliser les objets <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> pour attendre les tâches en cours d’exécution. Vous attendez (`await`) la fin de chaque tâche avant d’utiliser ses résultats. L’étape suivante consiste à créer des méthodes qui représentent la combinaison d’autres tâches. Avant de servir le petit-déjeuner, vous devez attendre la fin de la tâche qui correspond à l’action de faire griller le pain, avant d’ajouter le beurre et la confiture. Vous pouvez représenter cette tâche à l’aide du code suivant :

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" id="SnippetComposeToastTask":::

La signature de la méthode précédente comprend le modificateur `async`. Cela signale au compilateur que cette méthode contient une instruction `await`. Elle contient des opérations asynchrones. Cette méthode représente la tâche qui consiste à faire griller le pain, puis à ajouter le beurre et la confiture. Cette méthode retourne un <xref:System.Threading.Tasks.Task%601> qui représente la composition de ces trois opérations. Le bloc de code principal devient alors :

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" id="SnippetMain":::

La modification précédente montre une technique importante pour l’utilisation du code asynchrone. Pour composer des tâches, vous devez séparer les opérations dans une nouvelle méthode qui retourne une tâche. Vous pouvez choisir dans quels cas attendre les tâches. Vous pouvez démarrer d’autres tâches simultanément.

## <a name="await-tasks-efficiently"></a>Attendre efficacement la fin des tâches

La série d’instructions `await` à la fin du code précédent peut être améliorée à l’aide des méthodes de la classe `Task`. L’une de ces API est <xref:System.Threading.Tasks.Task.WhenAll%2A>, qui retourne un <xref:System.Threading.Tasks.Task> se terminant lorsque toutes les tâches de sa liste d’arguments sont terminées, comme indiqué dans le code suivant :

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

Une autre option consiste à utiliser <xref:System.Threading.Tasks.Task.WhenAny%2A>, qui retourne un `Task<Task>` se terminant lorsque l’un de ses arguments se termine. Vous pouvez attendre la tâche retournée, tout en sachant qu’elle est déjà terminée. Le code suivant montre comment utiliser <xref:System.Threading.Tasks.Task.WhenAny%2A> pour attendre la fin de la première tâche, puis traiter ses résultats. Après avoir traité les résultats de la tâche terminée, vous pouvez la supprimer de la liste des tâches passée à `WhenAny`.

```csharp
var breakfastTasks = new List<Task> { eggsTask, baconTask, toastTask };
while (breakfastTasks.Count > 0)
{
    Task finishedTask = await Task.WhenAny(breakfastTasks);
    if (finishedTask == eggsTask)
    {
        Console.WriteLine("eggs are ready");
    }
    else if (finishedTask == baconTask)
    {
        Console.WriteLine("bacon is ready");
    }
    else if (finishedTask == toastTask)
    {
        Console.WriteLine("toast is ready");
    }
    breakfastTasks.Remove(finishedTask);
}
```

Après toutes ces modifications, la version finale du code ressemble à ceci :<a id="final-version"></a>
:::code language="csharp" source="snippets/index/AsyncBreakfast-final/Program.cs" highlight="9-40":::

:::image type="content" source="media/whenany-async-breakfast.png" alt-text="quand tout petit déjeuner asynchrone":::

La version finale du petit-déjeuner préparé de façon asynchrone a duré environ 15 minutes. cela est dû au fait que certaines tâches pouvaient s’exécuter simultanément et que le code était en mesure de surveiller plusieurs tâches à la fois et d’agir uniquement lorsque cela était nécessaire.

Le code final est asynchrone. Il reflète plus précisément la façon dont nous préparons habituellement le petit-déjeuner. Comparez le code précédent au premier exemple de code de cet article. Les actions de base sont toujours claires lorsque nous lisons le code. Ce code est tout aussi lisible que les instructions de préparation du petit-déjeuner au début de cet article. Les fonctionnalités de langage pour `async` et `await` traduisent ce que chaque personne fait lorsqu’elle suit des instructions : démarrer les tâches dès que possible et ne pas attendre qu’une tâche soit terminée avant de passer à la suivante.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [En savoir plus sur le modèle de programmation asynchrone de tâche](task-asynchronous-programming-model.md)
