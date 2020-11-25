---
title: Meilleures pratiques du modèle de design observateur
ms.date: 03/30/2017
helpviewer_keywords:
- observer design pattern [.NET], best practices
- best practices [.NET], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: d88b092e681258566da685e3bb130b3d6131be08
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697582"
---
# <a name="observer-design-pattern-best-practices"></a>Meilleures pratiques du modèle de design observateur

Dans .NET, le modèle de conception observateur est implémenté comme un ensemble d’interfaces. L'interface <xref:System.IObservable%601?displayProperty=nameWithType> représente le fournisseur de données, qui est également chargé de fournir une implémentation <xref:System.IDisposable> permettant aux observateurs d'annuler leur abonnement aux notifications. L'interface <xref:System.IObserver%601?displayProperty=nameWithType> représente l'observateur. Cette rubrique décrit les meilleures pratiques que les développeurs doivent suivre quand ils implémentent le modèle de conception observateur à l'aide de ces interfaces.  
  
## <a name="threading"></a>Thread  

 En général, un fournisseur implémente la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> en ajoutant un observateur à une liste d’abonnés représentée par un objet de collection, puis il implémente la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> en supprimant un observateur de la liste des abonnés. Un observateur peut appeler ces méthodes à tout moment. De plus, étant donné que le contrat fournisseur/observateur ne spécifie pas qui est responsable de l'annulation d'abonnement après la méthode de rappel <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, il est possible que le fournisseur et l'observateur tentent de supprimer le même membre de la liste. En raison de cette éventualité, les méthodes <xref:System.IObservable%601.Subscribe%2A> et <xref:System.IDisposable.Dispose%2A> doivent être thread-safe. En général, cela implique l’utilisation d’une [collection simultanée](../parallel-programming/data-structures-for-parallel-programming.md) ou d’un verrou. Les implémentations qui ne sont pas thread-safe doivent indiquer explicitement qu'elles ne le sont pas.  
  
 Les garanties supplémentaires doivent être spécifiées dans une couche supérieure au contrat fournisseur/observateur. Les implémenteurs doivent indiquer clairement lorsqu'ils imposent des conditions supplémentaires afin d'éviter la confusion des utilisateurs concernant le contrat observateur.  
  
## <a name="handling-exceptions"></a>Gestion des exceptions  

 En raison du couplage faible entre un fournisseur de données et un observateur, les exceptions du modèle de conception observateur ont un but informatif. Cela affecte la façon dont les observateurs et les fournisseurs gèrent les exceptions dans le modèle de conception observateur.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Le fournisseur – Appel de la méthode OnError  

 La méthode <xref:System.IObserver%601.OnError%2A> a pour but d'informer les observateurs, tout comme la méthode <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>. Toutefois, la méthode <xref:System.IObserver%601.OnNext%2A> sert à fournir aux observateurs des données actuelles ou mises à jour, alors que la méthode <xref:System.IObserver%601.OnError%2A> sert à indiquer que le fournisseur ne peut pas fournir de données valides.  
  
 Le fournisseur doit suivre ces meilleures pratiques lors de la gestion des exceptions et de l'appel de la méthode <xref:System.IObserver%601.OnError%2A> :  
  
- Le fournisseur doit gérer ses propres exceptions s’il a des exigences spécifiques.  
  
- Le fournisseur ne doit pas exiger ni s'attendre à ce que les observateurs gèrent les exceptions.  
  
- Le fournisseur doit appeler la méthode <xref:System.IObserver%601.OnError%2A> quand il gère une exception qui compromet sa capacité à fournir des mises à jour. Les informations sur ces exceptions peuvent être passées à l'observateur. Dans les autres cas, il est inutile d'informer les observateurs des exceptions.  
  
 Une fois que le fournisseur a appelé la méthode <xref:System.IObserver%601.OnError%2A> ou <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, il ne doit y avoir aucune autre notification et le fournisseur peut annuler l'abonnement de ses observateurs. Toutefois, les observateurs peuvent également annuler leur abonnement à tout moment, y compris avant et après la réception d'une notification <xref:System.IObserver%601.OnError%2A> ou <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Le modèle de conception observateur ne détermine pas qui du fournisseur ou de l’observateur est responsable de l’annulation d’abonnement. Par conséquent, il est possible que les deux tentent de se désabonner. En règle générale, quand les observateurs annulent un abonnement, ils sont supprimés de la collection d’abonnés. Dans une application à thread unique, l’implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> doit s’assurer qu’une référence d’objet est valide et que l’objet est membre de la collection d’abonnés avant d’essayer de le supprimer. Dans une application multithread, un objet de collection thread-safe, tel qu’un objet <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>, doit être utilisé.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>L'observateur – Implémentation de la méthode OnError  

 Quand un observateur reçoit une notification d'erreur provenant du fournisseur, celle-ci lui est fournie à titre indicatif et ne l'oblige pas à effectuer d'action particulière.  
  
 L'observateur doit utiliser ces meilleures pratiques quand il répond à un appel de méthode <xref:System.IObserver%601.OnError%2A> provenant du fournisseur :  
  
- L'observateur ne doit pas lever d'exceptions depuis ses implémentations d'interface, telles que <xref:System.IObserver%601.OnNext%2A> ou <xref:System.IObserver%601.OnError%2A>. Si l'observateur lève des exceptions, il doit s'attendre à ce qu'elles ne soient pas gérées.  
  
- Pour conserver la pile des appels, un observateur qui souhaite lever un objet <xref:System.Exception> passé à sa méthode <xref:System.IObserver%601.OnError%2A> doit encapsuler l'exception avant de la lever. Un objet d'exception standard doit être utilisé à cet effet.  
  
## <a name="additional-best-practices"></a>Autres meilleures pratiques  

 Dans la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, une tentative d'annulation d'abonnement peut entraîner une référence null. Par conséquent, nous vous recommandons d'éviter cette pratique.  
  
 Même s’il est possible d’attacher un observateur à plusieurs fournisseurs, le modèle recommandé consiste à attacher une instance <xref:System.IObserver%601> à une seule et même instance <xref:System.IObservable%601>.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de conception observateur](observer-design-pattern.md)
- [Comment : implémenter un observateur](how-to-implement-an-observer.md)
- [Comment : implémenter un fournisseur](how-to-implement-a-provider.md)
