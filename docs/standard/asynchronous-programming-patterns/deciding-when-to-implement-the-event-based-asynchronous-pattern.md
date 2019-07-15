---
title: Choix du moment auquel implémenter le modèle asynchrone basé sur les événements
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: 5fca32953af91184fe99d8ef6afe5a2374f325d6
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663714"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Choix du moment auquel implémenter le modèle asynchrone basé sur les événements

Le modèle asynchrone basé sur des événements fournit un modèle pour exposer le comportement asynchrone d’une classe. Avec l’introduction de ce modèle, le .NET Framework définit deux modèles pour exposer le comportement asynchrone : le modèle asynchrone basé sur l’interface <xref:System.IAsyncResult?displayProperty=nameWithType> et le modèle basé sur les événements. Cette rubrique décrit les cas où il convient d’implémenter les deux modèles.

Pour plus d’informations sur la programmation asynchrone avec l’interface <xref:System.IAsyncResult>, consultez [Modèle de programmation asynchrone](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).

## <a name="general-principles"></a>Principes généraux

En règle générale, vous devez, dans la mesure du possible, exposer les fonctionnalités asynchrones à l’aide du modèle asynchrone basé sur les événements. Ce modèle ne répond toutefois pas à certaines exigences spécifiques. Dans ces cas particuliers, vous devez implémenter le modèle <xref:System.IAsyncResult> en plus du modèle basé sur les événements.

> [!NOTE]
> Il est rare d’implémenter le modèle <xref:System.IAsyncResult> sans implémenter également le modèle basé sur les événements.

## <a name="guidelines"></a>Recommandations

La liste suivante décrit les instructions à suivre si vous devez implémenter le modèle asynchrone basé sur les événements :

- Utilisez le modèle basé sur les événements comme API par défaut pour exposer le comportement asynchrone de votre classe.

- N’exposez pas le modèle <xref:System.IAsyncResult> si votre classe est principalement utilisée dans une application cliente, par exemple Windows Forms.

- Exposez uniquement le modèle <xref:System.IAsyncResult> s’il est nécessaire pour répondre à vos exigences. Par exemple, la compatibilité avec une API existante peut nécessiter l’exposition du modèle <xref:System.IAsyncResult>.

- N’exposez pas le modèle <xref:System.IAsyncResult> sans exposer également le modèle basé sur les événements.

- Si vous devez exposer le modèle <xref:System.IAsyncResult>, faites-le en tant qu’option avancée. Par exemple, si vous générez un objet proxy, générez le modèle basé sur les événements par défaut, avec une option pour générer le modèle <xref:System.IAsyncResult>.

- Effectuez votre implémentation du modèle basé sur les événements à partir de votre implémentation du modèle <xref:System.IAsyncResult>.

- Évitez d’exposer à la fois le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur la même classe. Exposez le modèle basé sur les événements sur des classes de « niveau supérieur », et le modèle <xref:System.IAsyncResult> sur des classes de « niveau inférieur ». Par exemple, comparez le modèle basé sur les événements sur le composant <xref:System.Net.WebClient> avec le modèle <xref:System.IAsyncResult> sur la classe <xref:System.Web.HttpRequest>.

  - Exposez le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur la même classe quand la compatibilité l’exige. Par exemple, si vous avez déjà publié une API qui utilise le modèle <xref:System.IAsyncResult>, vous devez conserver le modèle <xref:System.IAsyncResult> pour la compatibilité descendante.

  - Exposez le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur la même classe si la complexité du modèle objet résultant empêche de tirer avantage de la séparation des implémentations. Il vaut mieux exposer les deux modèles sur une même classe que de ne pas exposer le modèle basé sur les événements.

  - Si vous devez exposer à la fois le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur une même classe, utilisez l’attribut <xref:System.ComponentModel.EditorBrowsableAttribute> défini sur <xref:System.ComponentModel.EditorBrowsableState.Advanced> pour marquer l’implémentation du modèle <xref:System.IAsyncResult> comme une fonctionnalité avancée. Cela indique aux environnements de conception, comme Visual Studio IntelliSense, de ne pas afficher les méthodes et les propriétés <xref:System.IAsyncResult>. Ces méthodes et propriétés sont toujours utilisables, mais le développeur qui travaille avec IntelliSense a une vue plus claire de l’API.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Critères pour l’exposition du modèle IAsyncResult en plus du modèle basé sur les événements

Le modèle asynchrone basé sur les événements présente de nombreux avantages dans les cas mentionnés précédemment, mais également quelques inconvénients que vous devez prendre en compte si les performances sont essentielles pour vous.

Il existe trois scénarios dans lesquels le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> ne fonctionnent pas :

- Blocage de l’attente sur un <xref:System.IAsyncResult>

- Blocage de l’attente sur de nombreux objets <xref:System.IAsyncResult>

- Interrogation pour connaître l’état d’avancement sur le <xref:System.IAsyncResult>

Vous pouvez gérer ces scénarios à l’aide du modèle basé sur les événements, mais cela s’avère plus fastidieux que d’utiliser du modèle <xref:System.IAsyncResult>.

Les développeurs utilisent souvent le modèle <xref:System.IAsyncResult> pour les services qui exigent généralement de très hautes performances. Par exemple, l’interrogation pour connaître l’état d’avancement est une technique serveur hautes performances.

Par ailleurs, le modèle basé sur les événements est moins efficace que le modèle <xref:System.IAsyncResult> parce qu’il crée davantage d’objets, en particulier d’arguments <xref:System.EventArgs>, et qu’il se synchronise à travers les différents threads.

La liste suivante fournit quelques recommandations à suivre si vous décidez d’utiliser le modèle <xref:System.IAsyncResult> :

- Exposez uniquement le modèle <xref:System.IAsyncResult> si vous avez besoin de prendre spécifiquement en charge des objets <xref:System.Threading.WaitHandle> ou <xref:System.IAsyncResult>.

- Exposez uniquement le modèle <xref:System.IAsyncResult> si vous avez une API existante qui utilise le modèle <xref:System.IAsyncResult>.

- Si vous avez une API existante basée sur le modèle <xref:System.IAsyncResult>, vous pouvez également exposer le modèle basé sur les événements dans votre prochaine version.

- Exposez uniquement le modèle <xref:System.IAsyncResult> si vous exigez de hautes performances qui ne peuvent pas être atteintes avec le modèle basé sur les événements, mais qui peuvent l’être avec le modèle <xref:System.IAsyncResult>.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Implémentation du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
