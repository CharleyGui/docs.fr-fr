---
title: Modèle de design observateur
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
ms.openlocfilehash: 5794cd1ec9b63a6e151b35c28e09e29f86dcfac6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291264"
---
# <a name="observer-design-pattern"></a>Modèle de design observateur

Le modèle de design Observateur permet à un abonné de s’inscrire auprès d’un fournisseur et d’en recevoir des notifications. Il convient pour les scénarios nécessitant des notifications selon le modèle push. Le modèle définit un *fournisseur* (également appelé un *sujet* ou un *observable*) et zéro, un ou plusieurs *observateurs*. Les observateurs s'inscrivent auprès du fournisseur et, chaque fois qu'une condition prédéfinie, un événement ou un changement d'état se produit, le fournisseur notifie automatiquement tous les observateurs en appelant l'une de leurs méthodes. Dans cet appel de méthode, le fournisseur peut également fournir des informations sur l'état actuel aux observateurs. Dans le .NET Framework, le modèle de design Observateur est appliqué en implémentant les interfaces génériques <xref:System.IObservable%601?displayProperty=nameWithType> et <xref:System.IObserver%601?displayProperty=nameWithType>. Le paramètre de type générique représente le type qui fournit les informations de notification.

## <a name="applying-the-pattern"></a>Application du modèle

Le modèle de design Observateur convient pour les notifications push distribuées, car il prend en charge une séparation nette entre deux composants différents ou deux couches applicatives différentes, comme une couche de source de données (logique métier) et une couche d'interface utilisateur (affichage). Le modèle peut être implémenté chaque fois qu’un fournisseur utilise des rappels pour fournir les informations actuelles à ses clients.

Vous devez fournir les éléments suivants pour l’implémentation du modèle :

- Un fournisseur ou un sujet, qui est l'objet qui envoie les notifications aux observateurs. Un fournisseur est une classe ou une structure qui implémente l'interface <xref:System.IObservable%601>. Le fournisseur doit implémenter une seule méthode, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, qui est appelée par les observateurs qui veulent recevoir des notifications du fournisseur.

- Un observateur, qui est un objet qui reçoit des notifications d'un fournisseur. Un observateur est une classe ou une structure qui implémente l'interface <xref:System.IObserver%601>. L'observateur doit implémenter trois méthodes, toutes étant appelées par le fournisseur :

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, qui fournit des informations nouvelles ou actuelles à l'observateur.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, qui informe l'observateur qu'une erreur s'est produite.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, qui indique que le fournisseur a terminé l'envoi des notifications.

- Un mécanisme qui permet au fournisseur d'effectuer le suivi des observateurs. En règle générale, le fournisseur utilise un objet conteneur, comme un objet <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, pour y placer les références aux implémentations de <xref:System.IObserver%601> qui se sont abonnées aux notifications. L'utilisation d'un conteneur de stockage à cet effet permet au fournisseur de gérer de zéro à un nombre illimité d'observateurs. L'ordre dans lequel les observateurs reçoivent les notifications n'est pas défini ; le fournisseur est libre d'utiliser n'importe quelle méthode pour déterminer l'ordre.

- Une implémentation de <xref:System.IDisposable> qui permet au fournisseur de supprimer les observateurs quand la notification est effectuée. Les observateurs reçoivent une référence à l'implémentation de <xref:System.IDisposable> de la part de la méthode <xref:System.IObservable%601.Subscribe%2A>, et ils peuvent donc également appeler la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> pour se désabonner avant que le fournisseur ait terminé l'envoi des notifications.

- Un objet qui contient les données que le fournisseur envoie à ses observateurs. Le type de cet objet correspond au paramètre de type générique des interfaces <xref:System.IObservable%601> et <xref:System.IObserver%601>. Bien que cet objet puisse être le même que l'implémentation de <xref:System.IObservable%601>, il s'agit généralement d'un type distinct.

> [!NOTE]
> En plus d’implémenter le modèle de design Observateur, vous pouvez être intéressé par l’exploration des bibliothèques générées à l’aide des interfaces <xref:System.IObservable%601> et <xref:System.IObserver%601>. Par exemple, les [Extensions réactives pour .NET (Rx)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) se composent d’un ensemble de méthodes d’extension et d’opérateurs de séquence standard LINQ pour prendre en charge la programmation asynchrone.

## <a name="implementing-the-pattern"></a>Implémentation du modèle

L'exemple suivant utilise le modèle de design Observateur pour implémenter un système de restitution des bagages d'un aéroport. Une classe `BaggageInfo` fournit des informations sur les vols arrivés et sur les tapis roulants où les bagages de chaque vol peuvent être récupérés. Elle est montrée dans l'exemple suivant.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

Une classe `BaggageHandler` est responsable de la réception des informations sur les vols arrivés et sur les tapis roulants de récupération des bagages. En interne, elle gère deux collections :

- `observers` : une collection des clients qui recevront les informations mises à jour.

- `flights` : une collection des vols et des tapis roulants qui leur sont affectés.

Les deux collections sont représentées par des objets <xref:System.Collections.Generic.List%601> génériques qui sont instanciés dans le constructeur de classe `BaggageHandler`. Le code source de la classe `BaggageHandler` est montré dans l'exemple suivant.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Les clients qui veulent recevoir des informations mises à jour appellent la méthode `BaggageHandler.Subscribe`. Si le client ne s'est pas auparavant abonné aux notifications, une référence à l'implémentation de <xref:System.IObserver%601> du client est ajoutée à la collection `observers`.

La méthode `BaggageHandler.BaggageStatus` surchargée peut être appelée pour indiquer que les bagages d'un vol sont en cours de déchargement ou que leur déchargement est terminé. Dans le premier cas, les informations suivantes sont passées à la méthode : un numéro de vol, l'aéroport de provenance du vol et le tapis roulant où les bagages sont déchargés. Dans le deuxième cas, seul un numéro de vol est passé à la méthode. Pour les bagages en cours de déchargement, la méthode vérifie si les informations `BaggageInfo` passées à la méthode existent dans la collection `flights`. Si elles n'y existent pas, la méthode ajoute les informations et appelle la méthode `OnNext` de chaque observateur. Pour les vols dont le déchargement des bagages est terminé, la méthode vérifie si les informations de ce vol sont stockées dans la collection `flights`. Si c’est le cas, la méthode appelle la méthode `OnNext` de chaque observateur et supprime l’objet `BaggageInfo` de la collection `flights`.

Quand le dernier vol de la journée a atterri et que ses bagages ont été traités, la méthode `BaggageHandler.LastBaggageClaimed` est appelée. Cette méthode appelle la méthode `OnCompleted` de chaque observateur pour indiquer que toutes les notifications ont été effectuées, puis supprime la collection `observers`.

La méthode <xref:System.IObservable%601.Subscribe%2A> du fournisseur retourne une implémentation de <xref:System.IDisposable> qui permet aux observateurs d'arrêter de recevoir des notifications avant que la méthode <xref:System.IObserver%601.OnCompleted%2A> soit appelée. Le code source de cette classe `Unsubscriber(Of BaggageInfo)` est montré dans l'exemple suivant. Quand la classe est instanciée dans la méthode `BaggageHandler.Subscribe`, deux références lui sont passées : une référence à la collection `observers` et une référence à l’observateur qui est ajouté à la collection. Ces références sont affectées à des variables locales. Quand la méthode `Dispose` de l’objet est appelée, elle vérifie si l’observateur existe toujours dans la collection `observers` et, le cas échéant, elle supprime l’observateur.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

L'exemple suivant fournit une implémentation de <xref:System.IObserver%601> nommée `ArrivalsMonitor`, qui est une classe de base qui affiche les informations sur la récupération des bagages. Les informations sont affichées par ordre alphabétique, selon le nom de la ville d'origine. Les méthodes de `ArrivalsMonitor` sont marquées `overridable` (en Visual Basic) ou `virtual` (en C#), et elles peuvent donc toutes être remplacées par une classe dérivée.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

La classe `ArrivalsMonitor` comprend les méthodes `Subscribe` et `Unsubscribe`. La méthode `Subscribe` permet à la classe d'enregistrer l'implémentation de <xref:System.IDisposable> retournée par l'appel à <xref:System.IObservable%601.Subscribe%2A> dans une variable privée. La méthode `Unsubscribe` permet à la classe de se désabonner des notifications en appelant l'implémentation de <xref:System.IDisposable.Dispose%2A> du fournisseur. `ArrivalsMonitor` fournit également des implémentations des méthodes <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A> et <xref:System.IObserver%601.OnCompleted%2A>. Seule l'implémentation de <xref:System.IObserver%601.OnNext%2A> contient une quantité importante de code. La méthode fonctionne avec un objet <xref:System.Collections.Generic.List%601> privé, trié et générique, qui gère les informations sur les aéroports d'origine des vols arrivés et sur les tapis roulants où leurs bagages sont disponibles. Si la classe `BaggageHandler` signale l'arrivée d'un nouveau vol, l'implémentation de la méthode <xref:System.IObserver%601.OnNext%2A> ajoute des informations sur ce vol à la liste. Si la classe `BaggageHandler` signale que les bagages du vol ont été déchargées, la méthode <xref:System.IObserver%601.OnNext%2A> supprime ce vol de la liste. Chaque fois qu'une modification est apportée, la liste est triée et affichée sur la console.

L'exemple suivant contient le point d'entrée de l'application qui instancie la classe `BaggageHandler` ainsi que deux instances de la classe `ArrivalsMonitor`, et qui utilise la méthode `BaggageHandler.BaggageStatus` pour ajouter et supprimer des informations sur les vols arrivés. Dans chaque cas, les observateurs reçoivent des mises à jour et affichent correctement les informations de récupération des bagages.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Meilleures pratiques du modèle de design observateur](observer-design-pattern-best-practices.md)|Décrit les meilleures pratiques à adopter lors du développement d'applications qui implémentent le modèle de design Observateur.|
|[Comment : implémenter un fournisseur](how-to-implement-a-provider.md)|Fournit une implémentation pas à pas d'un fournisseur pour une application de surveillance de la température.|
|[Comment : implémenter un observateur](how-to-implement-an-observer.md)|Fournit une implémentation pas à pas d'un observateur pour une application de surveillance de la température.|
