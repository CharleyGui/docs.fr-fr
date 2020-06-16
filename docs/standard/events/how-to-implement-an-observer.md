---
title: 'Comment : implémenter une méthode Observer'
description: Implémentez un observateur dans .NET. Le modèle de conception observateur requiert une division entre un observateur, qui s’inscrit pour les notifications et un fournisseur.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: 43236ead15be0777f4284ba553a2f2f5e09d0a73
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768993"
---
# <a name="how-to-implement-an-observer"></a>Comment : implémenter une méthode Observer
Le modèle de design observateur requiert une division entre un observateur, qui s’inscrit pour recevoir des notifications, et un fournisseur, qui surveille les données et envie des notifications à un ou plusieurs observateurs. Cette rubrique décrit comment créer un observateur. Une rubrique connexe, [Guide pratique pour implémenter un fournisseur](how-to-implement-a-provider.md), explique comment créer un fournisseur.  
  
### <a name="to-create-an-observer"></a>Pour créer un observateur  
  
1. Définissez l’observateur, qui est un type qui implémente l’interface <xref:System.IObserver%601?displayProperty=nameWithType>. Par exemple, le code suivant définit un type intitulé `TemperatureReporter`, qui est une implémentation <xref:System.IObserver%601?displayProperty=nameWithType> construite avec un argument de type générique `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Si l’observateur peut cesser de recevoir des notifications avant que le fournisseur appelle son implémentation <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, définissez une variable privée qui contiendra l’implémentation <xref:System.IDisposable> retournée par la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> du fournisseur. Vous devez également définir une méthode d’abonnement qui appelle la méthode <xref:System.IObservable%601.Subscribe%2A> du fournisseur et stocke l’objet <xref:System.IDisposable> retourné. Par exemple, le code suivant définit une variable privée nommée `unsubscriber` et une méthode `Subscribe` qui appelle la méthode <xref:System.IObservable%601.Subscribe%2A> du fournisseur, puis affecte l’objet retourné à la variable `unsubscriber`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Définissez une méthode qui permet à l’observateur de cesser de recevoir des notifications avant que le fournisseur appelle son implémentation <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, si cette fonctionnalité est nécessaire. L'exemple suivant définit une méthode `Unsubscribe`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Fournissez des implémentations des trois méthodes définies par l’interface <xref:System.IObserver%601> : <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Selon le fournisseur et les besoins de l’application, les méthodes <xref:System.IObserver%601.OnError%2A> et <xref:System.IObserver%601.OnCompleted%2A> peuvent être des implémentations de type stub. Notez que la méthode <xref:System.IObserver%601.OnError%2A> ne doit pas gérer l’objet <xref:System.Exception> transmis en tant qu’exception, et la méthode <xref:System.IObserver%601.OnCompleted%2A> est libre d’appeler l’implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> du fournisseur. L’exemple suivant illustre l’implémentation <xref:System.IObserver%601> de la classe `TemperatureReporter`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient le code source complet de la classe `TemperatureReporter`, qui fournit l’implémentation <xref:System.IObserver%601> pour une application de surveillance de la température.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IObserver%601>
- [Modèle de conception observateur](observer-design-pattern.md)
- [Comment : implémenter un fournisseur](how-to-implement-a-provider.md)
- [Meilleures pratiques du modèle de design observateur](observer-design-pattern-best-practices.md)
