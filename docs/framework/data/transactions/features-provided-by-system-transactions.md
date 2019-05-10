---
title: Fonctionnalités fournies par System.Transactions
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 75277090652cd439d3466a307790f4b918ddb090
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645709"
---
# <a name="features-provided-by-systemtransactions"></a>Fonctionnalités fournies par System.Transactions
Cette section explique comment utiliser les fonctions fournies par l'espace de noms <xref:System.Transactions> pour écrire votre propre application transactionnelle et votre gestionnaire de ressources. Plus précisément, cette section explique comment créer et participer à une transaction (locale ou distribuée) avec un ou plusieurs participants.  
  
## <a name="overview-of-systemtransactions"></a>Vue d'ensemble de System.Transactions  
 L'infrastructure fournie par les classes de l'espace de noms <xref:System.Transactions> rend la programmation transactionnelle simple et efficace, grâce à la prise en charge des transactions initiées dans SQL Server, ADO.NET, Message Queuing (MSMQ) et MSDTC (Microsoft Distributed Transaction Coordinator). L’espace de noms <xref:System.Transactions> fournit à la fois un modèle de programmation explicite basé sur la classe <xref:System.Transactions.Transaction> et un modèle de programmation implicite utilisant la classe <xref:System.Transactions.TransactionScope>, dans lequel les transactions sont gérées automatiquement par l’infrastructure. Pour plus d’informations sur la création d’une application transactionnelle à l’aide de ces deux modèles, consultez [écriture d’une Application transactionnelle](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
 L'espace de noms <xref:System.Transactions> fournit également des types vous permettant d'implémenter un gestionnaire de ressources. Un gestionnaire de ressources gère les données durables ou volatiles utilisées dans une transaction et travaille en collaboration avec le gestionnaire de transactions pour garantir l'atomicité et l'isolation de l'application. Le gestionnaire de transactions fourni par l'infrastructure <xref:System.Transactions> prend en charge les transactions impliquant plusieurs ressources volatiles ou une ressource durable unique. Pour plus d’informations sur l’implémentation d’un gestionnaire de ressources, consultez [implémentation d’un gestionnaire de ressources](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md).  
  
 Le gestionnaire de transactions fait également remonter de façon transparente les transactions locales vers les transactions distribuées en s'associant avec un gestionnaire de transactions basé sur un disque, tel que le DTC, lorsqu'un gestionnaire de ressources durables supplémentaire s'inscrit à une transaction. L'infrastructure <xref:System.Transactions> offre deux façons principales d'obtenir des performances améliorées.  
  
- La remontée dynamique, qui garantit que l'infrastructure <xref:System.Transactions> n'engage le MSDTC que lorsqu'une transaction s'étend sur plusieurs ressources distribuées. Pour plus d'informations sur la remontée dynamique. consultez [Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md) rubrique.  
  
- Les inscriptions pouvant être promues, qui permettent à une ressource, telle qu’une base de données, de prendre possession de la transaction, s’il s’agit de la seule entité participant à la transaction. Ensuite, si nécessaire, l'infrastructure <xref:System.Transactions> peut remonter la gestion de la transaction vers le MSDTC. Cela réduit encore la nécessité d'utiliser le MSDTC. Inscriptions pouvant être promues sont présentées en détail dans la rubrique[optimisation à l’aide de la validation à Phase unique et la Notification de Phase unique pouvant être promue](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 L'espace de noms <xref:System.Transactions> définit trois niveaux de confiance (AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission (DTP) et confiance totale) qui permettent de restreindre l'accès aux types de ressources qu'il expose. Pour plus d’informations sur les différents niveaux de confiance, consultez [niveaux de confiance de sécurité dans l’accès aux ressources](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
### <a name="writing-a-transactional-application"></a>Écriture d'une application transactionnelle  
 L'espace de noms <xref:System.Transactions> fournit deux modèles de création d'applications transactionnelles. [Implémentation d’une Transaction implicite à l’aide de la portée de Transaction](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) décrit comment la <xref:System.Transactions> espace de noms prend en charge la création de transactions implicites à l’aide de la <xref:System.Transactions.TransactionScope> classe.  
  
 [Implémentation d’une Transaction explicite à l’aide de CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md) décrit comment la <xref:System.Transactions> espace de noms prend en charge la création de transactions explicites à l’aide de la <xref:System.Transactions.CommittableTransaction> classe.  
  
 D’autres rubriques traitant de l’écriture d’une application transactionnelle, consultez [écriture d’une Application transactionnelle](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Implémentation d'un gestionnaire des ressources  
 Pour implémenter un gestionnaire de ressources qui peut participer à une transaction, consultez [implémentation d’un gestionnaire de ressources](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md). Cette section traite de l'inscription d'une ressource, de la validation d'une transaction, de la récupération après défaillance et des meilleures pratiques d'optimisation.
