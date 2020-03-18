---
title: 'Comment : implémenter un fournisseur'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
ms.openlocfilehash: f5bb3cda0caa39ba3fd094b80e0b769a4bfc1f85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141558"
---
# <a name="how-to-implement-a-provider"></a>Comment : implémenter un fournisseur
Le modèle de design observateur requiert une division entre un fournisseur, qui surveille les données et envoie des notifications, et un ou plusieurs observateurs, qui reçoivent des notifications (rappels) du fournisseur. Cette rubrique décrit comment créer un fournisseur. Une rubrique connexe, [Guide pratique pour implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md), explique comment créer un observateur.  
  
### <a name="to-create-a-provider"></a>Pour créer un fournisseur  
  
1. Définissez les données que le fournisseur est chargé d’envoyer aux observateurs. Bien que le fournisseur et les données qu’il envoie aux observateurs puissent être de type unique, ils sont généralement représentés par différents types. Par exemple, dans une application de surveillance de la température, la structure `Temperature` définit les données que le fournisseur (qui est représenté par la classe `TemperatureMonitor` définie à l’étape suivante) surveille et auxquelles les observateurs s’abonnent.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Définissez le fournisseur de données, qui est un type qui implémente l’interface <xref:System.IObservable%601?displayProperty=nameWithType>. L’argument de type générique du fournisseur est le type que le fournisseur envoie aux observateurs. L’exemple suivant définit une classe `TemperatureMonitor`, qui est une implémentation <xref:System.IObservable%601?displayProperty=nameWithType> construite avec un argument de type générique `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Déterminez comment le fournisseur stockera les références aux observateurs afin que chaque observateur puisse être averti lorsque nécessaire. Plus couramment, un objet de collection comme un objet <xref:System.Collections.Generic.List%601> générique est utilisé à cet effet. L’exemple suivant définit un objet <xref:System.Collections.Generic.List%601> privé instancié dans le constructeur de classe `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Définissez une implémentation <xref:System.IDisposable> que le fournisseur peut retourner aux abonnés afin qu’ils cessent de recevoir des notifications à tout moment. L’exemple suivant définit une classe `Unsubscriber` imbriquée à laquelle une référence à la collection d’abonnés et à l’abonné est passée lorsque la classe est instanciée. Ce code permet à l’abonné d’appeler l’implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> de l’objet pour se supprimer lui-même de la collection d’abonnés.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implémentez la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>. Une référence à l’interface <xref:System.IObserver%601?displayProperty=nameWithType> est passée à la méthode et doit être stockée dans l’objet conçu à cet effet à l’étape 3. La méthode doit ensuite retourner l’implémentation <xref:System.IDisposable> développée à l’étape 4. L’exemple suivant illustre l’implémentation de la méthode <xref:System.IObservable%601.Subscribe%2A> dans la classe `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Informez les observateurs si nécessaire en appelant leurs implémentations <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Dans certains cas, un fournisseur peut ne pas appeler la méthode <xref:System.IObserver%601.OnError%2A> lorsqu’une erreur se produit. Par exemple, la méthode `GetTemperature` suivante simule un moniteur qui lit les données de température toutes les cinq secondes et avertit les observateurs si la température a changé d’au moins 1 degré depuis la lecture précédente. Si l’appareil ne signale pas de température (autrement dit, si sa valeur est Null), le fournisseur avertit les observateurs que la transmission est terminée. Notez que, en plus d’appeler la méthode <xref:System.IObserver%601.OnCompleted%2A> de chaque observateur, la méthode `GetTemperature` efface la collection <xref:System.Collections.Generic.List%601>. Dans ce cas, le fournisseur ne fait aucun appel à la méthode <xref:System.IObserver%601.OnError%2A> de ses observateurs.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a> Exemple  
 L’exemple suivant contient le code source complet permettant de définir une implémentation <xref:System.IObservable%601> pour une application de surveillance de la température. Il inclut la structure `Temperature`, qui correspond aux données envoyées aux observateurs, et la classe `TemperatureMonitor`, qui est l’implémentation <xref:System.IObservable%601>.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IObservable%601>
- [Modèle de conception Observateur](../../../docs/standard/events/observer-design-pattern.md)
- [Comment : implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Meilleures pratiques du modèle de design observateur](../../../docs/standard/events/observer-design-pattern-best-practices.md)
