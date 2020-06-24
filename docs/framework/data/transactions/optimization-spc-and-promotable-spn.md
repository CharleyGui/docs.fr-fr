---
title: Optimisation à l'aide de la validation à phase unique et de la notification de phase unique pouvant être promue
description: Optimiser les performances à l’aide de la validation à phase unique et de la notification de phase unique pouvant être promue. En savoir plus sur l’infrastructure System. transactions dans .NET.
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: 89ce82e673340c93254983c078f78a2501129383
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141976"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Optimisation à l'aide de la validation à phase unique et de la notification de phase unique pouvant être promue

Cette rubrique décrit les mécanismes fournis par l'infrastructure <xref:System.Transactions> pour l'optimisation des performances.

## <a name="promotable-single-phase-enlistment"></a>Inscription à phase unique pouvant être promue (PSPE)

L'infrastructure <xref:System.Transactions> gère une transaction dans un domaine d'application unique qui comprend une seule ressource durable ou plusieurs ressources volatiles. L'infrastructure <xref:System.Transactions> n'utilise que des appels intra-domaines d'application, elle offre donc le meilleur débit et d'excellentes performances.

Cependant, si la transaction est fournie à l'objet d'un autre domaine d'application (y compris au-delà de limites de processus et d'ordinateurs) du même ordinateur ou si vous tentez d'inscrire un autre gestionnaire de ressources durables, l'infrastructure <xref:System.Transactions> remonte automatiquement la transaction pour gestion par le MSDTC. Une transaction managée par le MSDTC n'est pas aussi performante qu'une transaction managée par l'infrastructure <xref:System.Transactions>.

Pour optimiser les performances, l'infrastructure <xref:System.Transactions> propose la PSPE qui permet à une ressource durable distante, située dans un domaine d'application, processus ou ordinateur différent, de participer à une transaction <xref:System.Transactions> sans entraîner sa remontée en transaction MSDTC. Cela permet au gestionnaire de ressources d'héberger et de « posséder » une transaction qui peut, si nécessaire, être ensuite remontée vers une transaction distribuée (ou une transaction MSDTC). Cela réduit l'utilisation du MSDTC.

Ce gestionnaire de ressources spécifique dispose généralement de ses propres transaction non distribuées internes et doit prendre en charge leur conversion en transactions distribuées lors de l'exécution. SQL Server 2005 fait, par exemple, partie de ces gestionnaires de ressources. Dans ce cas, l'infrastructure <xref:System.Transactions> joue un rôle de gestion passif et se contente de surveiller la transaction pour une remontée éventuelle. Pour prendre en charge l'interaction entre l'infrastructure <xref:System.Transactions> et le gestionnaire de ressources, ce dernier doit implémenter l'interface <xref:System.Transactions.IPromotableSinglePhaseNotification>.

La méthode <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> permet d'inscrire une ressource durable unique qui peut être remontée ultérieurement. Cette méthode garantit la remontée possible de l'inscription si besoin. Si l'inscription aboutit, le gestionnaire de ressources crée sa transaction interne et l'associe à la transaction <xref:System.Transactions>. Si l'inscription PSPE échoue, le gestionnaire de ressources doit s'inscrire à l'aide de la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A>. Il est impossible de s'inscrire à la PSPE lorsqu'il s'agit déjà d'une transaction distribuée ou lorsqu'un autre gestionnaire de ressources a déjà procédé à une inscription PSPE

Une fois l'inscription effectuée, les appels des clients pour la validation ou l'abandon de la transaction <xref:System.Transactions> sont convertis en appels vers le gestionnaire de ressources par appel à la méthode <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> ou <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A>, respectivement.

Si la transaction <xref:System.Transactions> ne nécessite jamais de remontée, le gestionnaire de ressources reçoit une notification <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> lors de la validation de la transaction Il peut ensuite valider la transaction interne qui avait été initialement créée.

Si la transaction <xref:System.Transactions> nécessite d'être remontée (pour prendre en charge plusieurs gestionnaires de ressources par exemple), <xref:System.Transactions> en informe le gestionnaire de ressources en appelant la méthode <xref:System.Transactions.ITransactionPromoter.Promote%2A> via l'interface <xref:System.Transactions.ITransactionPromoter>, à partir de laquelle l'interface <xref:System.Transactions.IPromotableSinglePhaseNotification> est dérivée. Le gestionnaire de ressources convertit ensuite la transaction en interne, à partir d'une transaction locale (ne nécessitant aucune connexion) en un objet de transaction pouvant participer à une transaction DTC, et l'associe au travail déjà effectué. Lors de la demande de validation de la transaction, le gestionnaire de transactions continue d'envoyer la notification <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> au gestionnaire de ressources, qui valide la transaction distribuée créée lors de la remontée.

> [!NOTE]
> Les traces **TransactionCommitted** (générées lorsqu’une validation est appelée sur la transaction remontée) contiennent l’ID d’activité de la transaction DTC.

Pour plus d’informations sur la remontée de la gestion, consultez [remontée](transaction-management-escalation.md)de la gestion des transactions.

## <a name="transaction-management-escalation-scenario"></a>Scénario de remontée de la gestion des transactions

Le scénario suivant présente une remontée vers une transaction distribuée effectuée avec le nom d'espaces <xref:System.Data> utilisé comme « proxy » pour le gestionnaire de ressources. Ce scénario suppose qu'une connexion <xref:System.Data> à la base de données (CN1), impliquée dans la transaction, est déjà établie et que l'application veut établir une seconde connexion <xref:System.Data>, (CN2). La transaction doit être remontée vers le DTC, en tant que transaction à validation en deux phases entièrement distribuée.

Dans ce scénario,

1. CN1 appelle la méthode <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> pour s'inscrire à la transaction. La transaction restant locale et aucune autre inscription ne pouvant être promue pour la transaction, l'appel <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> aboutit.

2. Lorsque CN2, la seconde connexion, appelle <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, l'appel échoue car une autre inscription pouvant être promue est impliquée. CN2 doit donc obtenir une transaction DTC pour la passer à SQL. Pour cela, elle utilise l'une des méthodes fournies par la classe <xref:System.Transactions.TransactionInterop> pour produire une transaction à un format pouvant être envoyé à SQL.

3. <xref:System.Transactions> appelle la méthode <xref:System.Transactions.ITransactionPromoter.Promote%2A> via l'interface <xref:System.Transactions.ITransactionPromoter> implémentée par CN1.

4. CN1 remonte alors la transaction grâce à un mécanisme spécifique à SQL 2005 et <xref:System.Data>.

5. La valeur de retour de la méthode <xref:System.Transactions.ITransactionPromoter.Promote%2A> est un tableau d'octets qui contient un jeton de propagation de la transaction. <xref:System.Transactions>utilise ce jeton de propagation pour créer une transaction DTC qu’il peut incorporer dans la transaction locale.

6. CN2 peut alors utiliser les données reçues par appel à l'une des méthodes par <xref:System.Transactions.TransactionInterop> pour passer la transaction à SQL.

7. Les deux connexions sont désormais inscrites à une transaction distribuée DTC.

## <a name="single-phase-commit-optimization"></a>Optimisation de la validation en une phase

Le protocole de validation en une phase est plus efficace lors de l'exécution car toutes les mises à jour sont effectuées sans coordination explicite. Pour tirer partie de cette optimisation, implémentez un gestionnaire de ressources via l'interface <xref:System.Transactions.ISinglePhaseNotification> pour la ressource et inscrivez-vous à une transaction à l'aide de la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A> ou <xref:System.Transactions.Transaction.EnlistVolatile%2A>. Plus précisément, le paramètre *EnlistmentOptions* doit être égal à pour <xref:System.Transactions.EnlistmentOptions.None> garantir qu’une validation à phase unique serait effectuée.

L'interface <xref:System.Transactions.ISinglePhaseNotification> étant dérivée de l'interface <xref:System.Transactions.IEnlistmentNotification>, si votre gestionnaire de ressources ne peut pas prétendre à la validation en une phase, il peut tout de même recevoir les notifications relatives à la validation en deux phases. Si votre gestionnaire de ressources reçoit une notification <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> du gestionnaire de transactions, il doit tenter d'effectuer le nécessaire pour la validation et informer le gestionnaire de transactions de la validation ou de la restauration de la transaction en appelant la méthode <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A> ou <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> pour le paramètre <xref:System.Transactions.SinglePhaseEnlistment>. À ce stade, une réponse de la <xref:System.Transactions.Enlistment.Done%2A> pour l'inscription implique la sémantique ReadOnly. Par conséquent, ne répondez pas à la <xref:System.Transactions.Enlistment.Done%2A> en plus des autres méthodes.

S'il n'y a qu'une inscription volatile et aucune inscription durable, l'inscription volatile reçoit la notification SPC. S’il existe des enlistions volatiles et une seule inscription durable, les enlistions volatiles reçoivent 2PC. Une fois terminée, l'inscription durable reçoit la notification SPC.

## <a name="see-also"></a>Voir aussi

- [Inscription de ressources comme participants à une transaction](enlisting-resources-as-participants-in-a-transaction.md)
- [Validation d’une transaction en une phase unique et en plusieurs phases](committing-a-transaction-in-single-phase-and-multi-phase.md)
