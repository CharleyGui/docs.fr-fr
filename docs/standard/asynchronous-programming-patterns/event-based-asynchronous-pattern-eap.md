---
title: Modèle asynchrone basé sur les événements (EAP)
description: Consultez des liens vers des articles sur le modèle asynchrone basé sur les événements (EAP) dans .NET, tels que l’implémentation, les meilleures pratiques, l’implémentation d’un client EAP, et bien plus encore.
ms.date: 07/23/2018
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: c15bb6c9ec6ea737e6f240376e12bf8de3aa61bc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830400"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Modèle asynchrone basé sur les événements (EAP)

Il existe plusieurs façons d’exposer des fonctionnalités asynchrones à du code client. Le modèle asynchrone basé sur les événements recommande une méthode pour obtenir des classes un comportement asynchrone.  
  
> [!NOTE]
> À partir de .NET Framework 4, la bibliothèque parallèle de tâches fournit un nouveau modèle pour la programmation asynchrone et parallèle. Pour plus d’informations, consultez [Bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md) et [Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>Dans cette section

 [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)  
 Explique comment le modèle asynchrone basé sur les événements permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.  
  
 [Implémentation du modèle asynchrone basé sur des événements](implementing-the-event-based-asynchronous-pattern.md)  
 Décrit la façon standardisée de placer dans un package une classe qui possède des fonctionnalités asynchrones.  
  
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Décrit les exigences liées à l’exposition de fonctionnalités asynchrones conformément au modèle asynchrone basé sur les événements.  
  
 [Choix du moment auquel implémenter le modèle asynchrone basé sur les événements](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Explique comment savoir quand vous devez implémenter le modèle asynchrone basé sur les événements au lieu du modèle <xref:System.IAsyncResult> représenté par le [ modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md).
  
 [Procédure : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Décrit comment créer un composant qui implémente le modèle asynchrone basé sur les événements. Il est implémenté à l'aide de classes d'assistance à partir de l'espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>, ce qui garantit le bon fonctionnement du composant avec n'importe quel modèle d'application.  

 [Procédure : implémenter un client du modèle asynchrone basé sur des événements](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Décrit comment créer un client qui utilise un composant implémentant le modèle asynchrone basé sur les événements.
  
 [Procédure : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Explique comment créer un composant qui prend en charge le modèle asynchrone basé sur les événements.  
  
## <a name="reference"></a>Informations de référence

 <xref:System.ComponentModel.AsyncOperation>  
 Décrit la classe <xref:System.ComponentModel.AsyncOperation> et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Décrit la classe <xref:System.ComponentModel.AsyncOperationManager> et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Décrit le composant <xref:System.ComponentModel.BackgroundWorker> et propose des liens vers tous ses membres.  
  
## <a name="related-sections"></a>Sections connexes

 [Bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md)  
 Décrit un modèle de programmation pour les opérations asynchrones et parallèles.  
  
 [Thread](../threading/index.md)  
 Décrit les fonctionnalités de multithreading dans .NET.  
  
## <a name="see-also"></a>Voir aussi

- [Meilleures pratiques pour le threading managé](../threading/managed-threading-best-practices.md)
- [Événements](../events/index.md)
- [Modèles de conception de la programmation asynchrone](index.md)
