---
title: Implémentation d'un gestionnaire des ressources
description: Implémentez un gestionnaire de ressources dans .NET. Un gestionnaire de ressources gère les ressources utilisées dans les transactions. Un gestionnaire de transactions coordonne les actions du gestionnaire de ressources.
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: bf40c6eaee35a5a548c6de4a286e46c4d4a66aca
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141847"
---
# <a name="implementing-a-resource-manager"></a>Implémentation d'un gestionnaire des ressources
Les ressources utilisées dans une transaction sont managées par un gestionnaire de ressources, dont les actions sont coordonnées par un gestionnaire de transactions. Les gestionnaires de ressources travaillent en coopération avec le gestionnaire de transactions pour fournir à l'application la garantie de l'atomicité et de l'isolation. Microsoft SQL Server, les files d'attente de messages durables et les tables de hachage en mémoire sont des gestionnaires de ressources.  
  
 Les gestionnaires de ressources gèrent des données durables ou volatiles. La durabilité (ou à l'inverse la volatilité) d'un gestionnaire de ressources indique s'il prend en charge la récupération après défaillance. Si un gestionnaire de ressources prend en charge la récupération après défaillance, il conserve les données par stockage durable lors de la Phase1 (préparation). Ainsi, s'il connaît une défaillance, il peut à nouveau s'inscrire à la transaction après récupération et procéder aux actions indiquées par les notifications envoyées par le gestionnaire de transactions. En général, les gestionnaires de ressources volatiles gèrent les ressources volatiles, comme une structure de données en mémoire (par exemple, une table de hachage traitée en mémoire), et les gestionnaires de ressources durables gèrent les ressources qui disposent d'un magasin de stockage plus persistant (par exemple, une base de données ayant un disque comme magasin de stockage).  
  
 Pour qu'une ressource participe à une transaction, elle doit être inscrite à cette transaction. La <xref:System.Transactions.Transaction> classe définit un ensemble de méthodes dont les noms commencent par **Enlist** qui fournissent cette fonctionnalité. Les différentes méthodes d' **enrôle** correspondent aux différents types d’inscription qu’un gestionnaire de ressources peut avoir. En particulier, utilisez les méthodes <xref:System.Transactions.Transaction.EnlistVolatile%2A> pour les ressources volatiles et la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A> pour les ressources durables. Pour une question de simplicité, après avoir décidé d'utiliser la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A> ou la méthode <xref:System.Transactions.Transaction.EnlistVolatile%2A>, selon la prise en charge de la durabilité de la ressource, inscrivez votre ressource pour participer à la validation en deux phases (2PC) en implémentant l'interface <xref:System.Transactions.IEnlistmentNotification> de votre gestionnaire de ressources. Pour plus d’informations sur 2PC, consultez [validation d’une transaction en une phase unique et en plusieurs phases](committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 En s'inscrivant, le gestionnaire de ressources s'assure de la réception des rappels du gestionnaire de transactions lors de la validation ou de l'abandon de la transaction. On compte une instance de <xref:System.Transactions.IEnlistmentNotification> par inscription. En général, on trouve une inscription par transaction, mais un gestionnaire de ressources peut choisir de s'inscrire plusieurs fois à la même transaction.  
  
 Après inscription, le gestionnaire de ressources répond aux requêtes de la transaction. Un gestionnaire de ressources durables enregistre suffisamment d'informations pour pouvoir annuler ou répéter le travail de la transaction sur les ressources qu'il manage. Il existe de nombreuses façon d'effectuer cela ; conserver des versions des données ou conserver un journal des modifications sont deux techniques communes.  
  
 Lorsque l'application valide la transaction, le gestionnaire de transactions lance le protocole de validation en deux phases. Le gestionnaire de transactions interroge d'abord chaque gestionnaire de ressources inscrit pour savoir s'il est prêt pour la validation de la transaction. Le gestionnaire de ressources doit se préparer pour la validation : il se prépare à valider ou abandonner la transaction.  
  
 Lors de la phase de préparation, le gestionnaire de ressources durables enregistre les nouvelles et anciennes données dans un espace de stockage stable de façon à ce que le gestionnaire de ressources puisse les récupérer, même en cas de défaillance système. Si le gestionnaire de ressources peut effectuer la préparation, il communique au gestionnaire de transactions son vote de validation ou d'abandon de la transaction. Si le gestionnaire de ressources signale un échec de préparation, le gestionnaire de transactions envoie une commande de restauration à chaque gestionnaire de ressources et indique l'échec de validation à l'application.  
  
 Une fois préparé, un gestionnaire de ressources doit patienter jusqu'à la réception d'un rappel à validation ou d'abandon du gestionnaire de transactions en phase 2. Généralement, l'intégralité du protocole de préparation et de validation ne prend qu'une fraction de seconde. En cas de défaillance système ou de communication, la notification de validation ou d'abandon peut ne pas arriver avant des minutes, voire des heures. Pendant ce temps, le gestionnaire de ressources ne connaît pas le résultat de la transaction. Il ne sait pas si elle est validée ou abandonnée. Tant que le gestionnaire de ressources ne connaît pas le résultat d'une transaction, il conserve les données modifiées en laissant la transaction verrouillée, isolant ces modifications des autres transactions.  
  
 Lors d'une défaillance du gestionnaire de ressources, l'ensemble des transactions inscrites sont abandonnées, à l'exception de celles préparées ou validées avant la défaillance. Lors de son redémarrage, un gestionnaire de ressources durables reconstruit l'état validé des ressources qu'il manage en récupérant les informations de préparation écrites en phase de préparation, puis valide ou abandonne ces transactions.  
  
 En résumé, le protocole de validation en deux phases et les gestionnaires de ressources s'associent pour assurer l'atomicité et la durabilité des transactions.  
  
 La classe <xref:System.Transactions.Transaction> fournit également la méthode <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> permettant de s'inscrire à une PSPE (Promotable Single Phase Enlistment). Cela permet à un gestionnaire de ressources durables d'héberger et de « posséder » une transaction qui peut, si nécessaire, être ensuite remontée pour être managée par le MSDTC. Pour plus d’informations, consultez [optimisation à l’aide de la validation à phase unique et de la notification à phase unique pouvant être promue](optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les étapes généralement suivies par un gestionnaire de ressources sont détaillées dans les rubriques suivantes.  
  
 [Inscription de ressources comme participants à une transaction](enlisting-resources-as-participants-in-a-transaction.md)  
  
 Décrit comment inscrire une ressource durable ou volatile à une transaction.  
  
 [Validation d’une transaction en une phase unique et en plusieurs phases](committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Décrit la façon dont un gestionnaire de ressources répond à la notification de validation et prépare la validation.  
  
 [Exécution de la récupération](performing-recovery.md)  
  
 Décrit comment un gestionnaire de ressources durables récupère après la défaillance.  
  
 [Niveaux de confiance de sécurité dans l’accès aux ressources](security-trust-levels-in-accessing-resources.md)  
  
 Décrit comment les trois niveaux de confiance de System.Transactions permettent de restreindre l'accès aux types de ressources que <xref:System.Transactions> expose.  
  
 [Optimisation à l’aide de la validation à phase unique et de la notification de phase unique pouvant être promue](optimization-spc-and-promotable-spn.md)  
  
 Décrit les pratiques d'optimisation disponibles pour l'implémentations des gestionnaires de ressources.
