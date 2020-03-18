---
title: Modèle d’événement .NET Core mis à jour
description: Découvrez toute la souplesse apportée par le modèle d’événement .NET Core et la compatibilité descendante et apprenez à implémenter un traitement sécurisé des événements grâce aux abonnés asynchrones.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170434"
---
# <a name="the-updated-net-core-event-pattern"></a>Modèle d’événement .NET Core mis à jour

[Précédent](event-pattern.md)

L’article précédent décrit les modèles d’événements les plus courants. .NET Core a un modèle plus souple. Dans cette version, la définition `EventHandler<TEventArgs>` n’a plus la contrainte selon laquelle `TEventArgs` doit être une classe dérivée de `System.EventArgs`.

Ceci accroît la flexibilité pour vous et offre une compatibilité descendante. Commençons par la flexibilité. La classe System.EventArgs introduit une méthode : `MemberwiseClone()`, qui crée une copie superficielle de l’objet.
Cette méthode doit utiliser la réflexion afin d’implémenter ses fonctionnalités pour n’importe quelle classe dérivée de `EventArgs`. Ces fonctionnalités sont plus faciles à créer dans une classe dérivée spécifique. Cela signifie concrètement que la dérivation depuis System.EventArgs est une contrainte qui limite vos conceptions, mais n’offre aucun avantage supplémentaire.
Vous pouvez en fait changer les définitions de `FileFoundArgs` et de `SearchDirectoryArgs` de façon à ce qu’ils ne dérivent pas de `EventArgs`.
Le programme fonctionnera exactement de la même façon.

Vous pouvez également changer les `SearchDirectoryArgs` en un struct si vous faites une modification de plus :

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

La modification supplémentaire consiste à appeler le constructeur sans paramètre avant d’entrer dans le constructeur qui initialise tous les champs. Sans cet ajout, les règles de C# signalent que les propriétés sont accessibles avant qu’une valeur leur soit affectée.

Vous ne devez pas changer les `FileFoundArgs` d’une classe (type référence) en un struct (type valeur). La raison en est que le protocole de gestion d’annulation nécessite que les arguments de l’événement soient passés par référence. Si vous aviez apporté cette même modification, la classe de recherche de fichier ne pourrait jamais observer les modifications apportées par les abonnés à l’événement. Une nouvelle copie de la structure serait utilisée pour chaque abonné, et cette copie serait une copie différente de celle vue par l’objet de recherche de fichier.

Voyons ensuite comment cette modification peut avoir une compatibilité descendante.
La suppression de la contrainte n’affecte aucun code existant. Les types d’arguments d’événement existants dérivent toujours de `System.EventArgs`.
La compatibilité descendante est une des raisons principales pour lesquelles ils continueront à dériver de `System.EventArgs`. Les abonnés à l’événement existants seront les abonnés à un événement qui ont suivi le modèle classique.

Selon une logique similaire, aucun type d’argument d’événement créé maintenant n’aurait aucun abonné dans aucun des codes base existants. Les nouveaux types d’événements qui ne dérivent pas de `System.EventArgs` ne vont pas arrêter ces codes base.

## <a name="events-with-async-subscribers"></a>Événements avec des abonnés asynchrones

Vous avez un modèle final à découvrir : comment écrire correctement des abonnés à l’événement qui appellent du code asynchrone. La difficulté est décrite dans l’article consacré à [async et await](async.md). Les méthodes asynchrones peuvent avoir un type de retour void, mais ceci est fortement déconseillé. Quand votre code pour l’abonné à l’événement appelle une méthode asynchrone, vous n’avez d’autre choix que de créer une méthode `async void`. La signature de gestionnaire d’événements en a besoin.

Vous devez rapprocher ces deux nécessités opposées. D’une façon ou d’une autre, vous devez créer une méthode `async void` sécurisée. Les principes de base du modèle que vous devez implémenter sont les suivants :

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

Notez d’abord que le gestionnaire est marqué en tant que gestionnaire asynchrone. Comme il est affecté à un type délégué de gestionnaire d’événements, il a un type de retour void. Cela signifie que vous devez suivre le modèle indiqué dans le gestionnaire et interdire la levée d’exceptions en dehors du contexte du gestionnaire asynchrone. Comme il ne retourne pas une tâche, aucune tâche ne peut signaler l’erreur en passant à l’état d’erreur. Comme la méthode est asynchrone, elle ne peut tout simplement pas lever l’exception. (La méthode d’appel a `async`continué l’exécution parce qu’elle est .) Le comportement réel en temps d’exécution sera défini différemment pour différents environnements. Il peut mettre fin au thread ou au processus qui possède le thread, ou laisser le processus dans un état indéterminé. Tous ces résultats potentiels sont très indésirables.

C’est pourquoi vous devez encapsuler l’instruction await pour la tâche asynchrone dans votre propre bloc try. Si elle entraîne une erreur dans une tâche, vous pouvez consigner cette erreur. Si c’est une erreur dont votre application ne peut pas récupérer, vous pouvez quitter le programme rapidement et normalement.

Ce sont les principales mises à jour du modèle d’événement .NET. Vous pouvez voir de nombreux exemples des versions précédentes dans les bibliothèques avec lesquelles vous travaillez. Il est cependant important de bien comprendre ce que sont les derniers modèles.

Le prochain article de cette série vous permet de faire la distinction entre l’utilisation de `delegates` et de `events` dans vos conceptions. Ces sont des concepts similaires : cet article vous aide à prendre la bonne décision pour vos programmes.

[Suivant](distinguish-delegates-events.md)
