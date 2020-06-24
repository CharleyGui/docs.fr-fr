---
title: Fonctionnalités fournies par System.Transactions
description: Passez en revue les fonctionnalités fournies par l’espace de noms System. transactions dans .NET pour écrire votre propre application de transaction et Resource Manager.
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 0278e9248305572c6156c6500f1fe51a8b3f3338
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141860"
---
# <a name="features-provided-by-systemtransactions"></a>Fonctionnalités fournies par System.Transactions
Cette section explique comment utiliser les fonctions fournies par l'espace de noms <xref:System.Transactions> pour écrire votre propre application transactionnelle et votre gestionnaire de ressources. Plus précisément, cette section explique comment créer et participer à une transaction (locale ou distribuée) avec un ou plusieurs participants.  
  
## <a name="overview-of-systemtransactions"></a>Vue d'ensemble de System.Transactions  
 L'infrastructure fournie par les classes de l'espace de noms <xref:System.Transactions> rend la programmation transactionnelle simple et efficace, grâce à la prise en charge des transactions initiées dans SQL Server, ADO.NET, Message Queuing (MSMQ) et MSDTC (Microsoft Distributed Transaction Coordinator). L’espace de noms <xref:System.Transactions> fournit à la fois un modèle de programmation explicite basé sur la classe <xref:System.Transactions.Transaction> et un modèle de programmation implicite utilisant la classe <xref:System.Transactions.TransactionScope>, dans lequel les transactions sont gérées automatiquement par l’infrastructure. Pour plus d’informations sur la création d’une application transactionnelle à l’aide de ces deux modèles, consultez [écriture d’une application transactionnelle](writing-a-transactional-application.md).  
  
 L'espace de noms <xref:System.Transactions> fournit également des types vous permettant d'implémenter un gestionnaire de ressources. Un gestionnaire de ressources gère les données durables ou volatiles utilisées dans une transaction et travaille en collaboration avec le gestionnaire de transactions pour garantir l'atomicité et l'isolation de l'application. Le gestionnaire de transactions fourni par l'infrastructure <xref:System.Transactions> prend en charge les transactions impliquant plusieurs ressources volatiles ou une ressource durable unique. Pour plus d’informations sur l’implémentation d’un gestionnaire de ressources, consultez [implémentation d’un gestionnaire des ressources](implementing-a-resource-manager.md).  
  
 Le gestionnaire de transactions fait également remonter de façon transparente les transactions locales vers les transactions distribuées en s'associant avec un gestionnaire de transactions basé sur un disque, tel que le DTC, lorsqu'un gestionnaire de ressources durables supplémentaire s'inscrit à une transaction. L'infrastructure <xref:System.Transactions> offre deux façons principales d'obtenir des performances améliorées.  
  
- La remontée dynamique, qui garantit que l'infrastructure <xref:System.Transactions> n'engage le MSDTC que lorsqu'une transaction s'étend sur plusieurs ressources distribuées. Pour plus d'informations sur la remontée dynamique. consultez la rubrique [remontée](transaction-management-escalation.md) de la gestion des transactions.  
  
- Les inscriptions pouvant être promues, qui permettent à une ressource, telle qu’une base de données, de prendre possession de la transaction, s’il s’agit de la seule entité participant à la transaction. Ensuite, si nécessaire, l'infrastructure <xref:System.Transactions> peut remonter la gestion de la transaction vers le MSDTC. Cela réduit encore la nécessité d'utiliser le MSDTC. Les inscriptions pouvant être promues sont traitées en détail dans la rubrique[optimisation à l’aide de la validation à phase unique et de la notification de phase unique pouvant être promue](optimization-spc-and-promotable-spn.md).  
  
 L'espace de noms <xref:System.Transactions> définit trois niveaux de confiance (AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission (DTP) et confiance totale) qui permettent de restreindre l'accès aux types de ressources qu'il expose. Pour plus d’informations sur les différents niveaux de confiance, consultez [niveaux de confiance de sécurité dans accès aux ressources](security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
### <a name="writing-a-transactional-application"></a>Écriture d'une application transactionnelle  
 L'espace de noms <xref:System.Transactions> fournit deux modèles de création d'applications transactionnelles. L' [implémentation d’une transaction implicite à l’aide de la portée transaction](implementing-an-implicit-transaction-using-transaction-scope.md) décrit comment l' <xref:System.Transactions> espace de noms prend en charge la création de transactions implicites à l’aide de <xref:System.Transactions.TransactionScope>  
  
 L' [implémentation d’une transaction explicite avec CommittableTransaction](implementing-an-explicit-transaction-using-committabletransaction.md) décrit comment l' <xref:System.Transactions> espace de noms prend en charge la création de transactions explicites à l’aide de la <xref:System.Transactions.CommittableTransaction> classe.  
  
 Pour obtenir des rubriques supplémentaires couvrant l’écriture d’une application transactionnelle, consultez [écriture d’une application transactionnelle](writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Implémentation d'un gestionnaire des ressources  
 Pour implémenter un gestionnaire de ressources qui peut participer à une transaction, consultez [implémentation d’un gestionnaire des ressources](implementing-a-resource-manager.md). Cette section traite de l'inscription d'une ressource, de la validation d'une transaction, de la récupération après défaillance et des meilleures pratiques d'optimisation.
