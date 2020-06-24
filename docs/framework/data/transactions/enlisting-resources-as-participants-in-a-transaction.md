---
title: Inscription de ressources comme participants à une transaction
description: Inscrire des ressources en tant que participants dans une transaction .NET. Chaque ressource d’une transaction est gérée par un gestionnaire de ressources, coordonné par un gestionnaire de transactions.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: c3c777593750b3a4f05ae97ed6e26e19f58e4d72
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141873"
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Inscription de ressources comme participants à une transaction

Les ressources participant à une transaction sont managées par un gestionnaire de ressources, dont les actions sont coordonnées par un gestionnaire de transactions. La coordination s'effectue par envoi de notifications aux abonnés qui se sont inscrits à une transaction via le gestionnaire de transactions.

Cette rubrique explique comment inscrire une ressource (ou plusieurs ressources) à une transaction et traite des différents types d'inscription. La rubrique [validation d’une transaction en une seule phase et en plusieurs phases](committing-a-transaction-in-single-phase-and-multi-phase.md) couvre la manière dont l’engagement de transaction peut être coordonné parmi les ressources inscrites.

## <a name="enlisting-resources-in-a-transaction"></a>Inscription de ressources à une transaction

Pour qu'une ressource participe à une transaction, elle doit être inscrite à cette transaction. La <xref:System.Transactions.Transaction> classe définit un ensemble de méthodes dont les noms commencent par **Enlist** qui fournissent cette fonctionnalité. Les différentes méthodes d' **enrôle** correspondent aux différents types d’inscription qu’un gestionnaire de ressources peut avoir. En particulier, utilisez les méthodes <xref:System.Transactions.Transaction.EnlistVolatile%2A> pour les ressources volatiles et la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A> pour les ressources durables. La durabilité (ou à l'inverse la volatilité) d'un gestionnaire de ressources indique s'il prend en charge la récupération après défaillance. Si un gestionnaire de ressources prend en charge la récupération après défaillance, il conserve les données par stockage durable lors de la Phase1 (préparation). Ainsi, s'il connaît une défaillance, il peut à nouveau s'inscrire à la transaction après récupération et procéder aux actions indiquées par les notifications envoyées par le gestionnaire de transactions. En général, les gestionnaires de ressources volatiles gèrent les ressources volatiles, comme une structure de données en mémoire (par exemple, une table de hachage traitée en mémoire), et les gestionnaires de ressources durables gèrent les ressources qui disposent d'un magasin de stockage plus persistant (par exemple, une base de données ayant un disque comme magasin de stockage).

Pour une question de simplicité, après avoir décidé d'utiliser la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A> ou la méthode <xref:System.Transactions.Transaction.EnlistVolatile%2A>, selon la prise en charge de la durabilité de la ressource, inscrivez votre ressource pour participer à la validation en deux phases (2PC) en implémentant l'interface <xref:System.Transactions.IEnlistmentNotification> de votre gestionnaire de ressources. Pour plus d’informations sur 2PC, consultez [validation d’une transaction en une phase unique et en plusieurs phases](committing-a-transaction-in-single-phase-and-multi-phase.md).

Un participant peut s'inscrire à plusieurs de ces protocoles en appelant <xref:System.Transactions.Transaction.EnlistDurable%2A> et <xref:System.Transactions.Transaction.EnlistVolatile%2A> à plusieurs reprises.

### <a name="durable-enlistment"></a>Inscription durable

Les méthodes <xref:System.Transactions.Transaction.EnlistDurable%2A> permettent d'inscrire un gestionnaire de ressources à une transaction en tant de ressource durable.  Si un gestionnaire de ressources durables s'arrête en cours de transaction, il peut procéder à la récupération une fois sa remise en ligne effectuée par réinscription (à l'aide de la méthode <xref:System.Transactions.TransactionManager.Reenlist%2A>) à toutes les transactions auxquelles il participait et dont il n'a pas terminé la phase 2, et appeler <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> une fois le traitement de récupération terminé. Pour plus d’informations sur la récupération, voir exécution de la [récupération](performing-recovery.md).

Les méthodes <xref:System.Transactions.Transaction.EnlistDurable%2A> ont toutes un objet <xref:System.Guid> pour premier paramètre. Le gestionnaire de transactions utilise le <xref:System.Guid> pour associer une inscription durable à un gestionnaire de ressources particulier. Il est donc impératif qu'un gestionnaire de ressources utilise toujours le même <xref:System.Guid> pour son identification après redémarrage, même sur plusieurs gestionnaires de ressources, sous peine de faire échouer la récupération.

Le second paramètre des méthodes <xref:System.Transactions.Transaction.EnlistDurable%2A> est une référence à l'objet que le gestionnaire de ressources implémente pour recevoir les notifications de transaction. La surcharge que vous utilisez indique au gestionnaire de transactions si votre gestionnaire de ressources prend en charge l'optimisation de validation à phase unique (SPC). Dans la plupart des cas, vous implémenterez l'interface <xref:System.Transactions.IEnlistmentNotification> pour participer à la validation en deux phases (2PC). Cependant, si vous souhaitez optimiser le processus de validation, envisagez d'implémenter l'interface <xref:System.Transactions.ISinglePhaseNotification> pour SPC. Pour plus d’informations sur le SPC, consultez [validation d’une transaction en une phase unique et multiphase](committing-a-transaction-in-single-phase-and-multi-phase.md) et [optimisation à l’aide d’une validation à phase unique et d’une notification de phase unique pouvant être promue](optimization-spc-and-promotable-spn.md).

Le troisième paramètre est une énumération <xref:System.Transactions.EnlistmentOptions>, dont la valeur peut être <xref:System.Transactions.EnlistmentOptions.None> ou <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Si la valeur est <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>, l'inscription peut autoriser des gestionnaires de ressources supplémentaires après réception de la notification de préparation envoyée par le gestionnaire de transactions. Toutefois, vous devez savoir que ce type d'inscription n'est pas pris en charge pour l'optimisation de la validation en une phase.

### <a name="volatile-enlistment"></a>Inscription volatile

Les participants gérant des ressources volatiles telles qu'un cache doivent s'inscrire à l'aide des méthodes <xref:System.Transactions.Transaction.EnlistVolatile%2A>. Il est possible que ces objets ne puissent pas obtenir le résultat d'une transaction ou récupérer l'état d'une transaction à laquelle ils participent après une défaillance système.

Comme indiqué précédemment, un gestionnaire de ressources procède à une inscription volatile s'il manage une ressource volatile en mémoire. L'un des avantages offert par <xref:System.Transactions.Transaction.EnlistVolatile%2A> est que cela évite une remontée inutile de la transaction. Pour plus d’informations sur la remontée des transactions, consultez la rubrique [remontée](transaction-management-escalation.md) de la gestion des transactions. L’inscription de la volatilité implique à la fois une différence dans la manière dont l’inscription est gérée par le gestionnaire de transactions, ainsi que ce qui est attendu par le gestionnaire de transactions de Resource Manager. Cela est dû au fait que les gestionnaires de ressources volatiles ne prennent pas en charge la récupération. Les méthodes <xref:System.Transactions.Transaction.EnlistVolatile%2A> n'ont pas de paramètre <xref:System.Guid> car les gestionnaires de ressources volatiles ne prennent pas en charge la récupération et n'appellent donc jamais la méthode <xref:System.Transactions.TransactionManager.Reenlist%2A>, qui requiert un <xref:System.Guid>.

Comme pour les inscriptions durables, la méthode de surcharge utilisée pour vous inscrire indique au gestionnaire de transactions si votre gestionnaire de ressources prend en charge l'optimisation de la validation en une phase. Les gestionnaires de ressources volatiles ne prenant pas en charge la récupération, aucune information de récupération n'est déclarée pour une inscription volatile lors de la phase de préparation. C'est pourquoi appeler la méthode <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> entraîne une <xref:System.InvalidOperationException>.

L'exemple suivant indique comment inscrire l'un de ces objets à une transaction à l'aide de la méthode <xref:System.Transactions.Transaction.EnlistVolatile%2A>.

[!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
[!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]

### <a name="optimizing-performance"></a>Optimisation des performances

La classe <xref:System.Transactions.Transaction> fournit également la méthode <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> permettant de s'inscrire à une PSPE (Promotable Single Phase Enlistment). Cela permet à un gestionnaire de ressources durables d'héberger et de « posséder » une transaction qui peut, si nécessaire, être ensuite remontée pour être managée par le MSDTC. Pour plus d’informations, consultez [optimisation à l’aide de la validation à phase unique et de la notification à phase unique pouvant être promue](optimization-spc-and-promotable-spn.md).

## <a name="see-also"></a>Voir aussi

- [Optimisation à l’aide de la validation à phase unique et de la notification de phase unique pouvant être promue](optimization-spc-and-promotable-spn.md)
- [Validation d’une transaction en une phase unique et en plusieurs phases](committing-a-transaction-in-single-phase-and-multi-phase.md)
