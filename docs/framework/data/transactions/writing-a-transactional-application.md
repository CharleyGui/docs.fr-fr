---
title: Écriture d’une application transactionnelle
description: Écrire une application transactionnelle dans .NET. Utilisez un modèle de programmation explicite ou implicite avec la classe transaction ou TransactionScope, respectivement.
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: b4cc33939128e61a69db319491a7d2d60ab9a819
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186664"
---
# <a name="writing-a-transactional-application"></a>Écriture d’une application transactionnelle

En tant que programmeur d'applications transactionnelles, vous pouvez bénéficier des deux modèles de programmation fournis par l'espace de noms <xref:System.Transactions> pour créer une transaction. Vous pouvez utiliser le modèle de programmation explicite à l’aide de la <xref:System.Transactions.Transaction> classe, ou le modèle de programmation implicite dans lequel les transactions sont gérées automatiquement par l’infrastructure, à l’aide de la <xref:System.Transactions.TransactionScope> classe. Nous vous recommandons d’utiliser le modèle de transaction implicite pour le développement. Vous trouverez plus d’informations sur l’utilisation d’une étendue de transaction dans la rubrique [implémentation d’une transaction implicite à l’aide](implementing-an-implicit-transaction-using-transaction-scope.md) d’une étendue de transaction.  
  
 Les deux modèles prennent en charge la validation d'une transaction lorsque le programme atteint un état cohérent. Si la validation réussit, la transaction est validée durablement. Si la validation échoue, la transaction est abandonnée. Si le programme d'application ne parvient pas à terminer la transaction avec succès, il tente d'abandonner et d'annuler les effets de la transaction.  
  
## <a name="in-this-section"></a>Dans cette section  
  
### <a name="creating-a-transaction"></a>Création d'une transaction  

 L'espace de noms <xref:System.Transactions> fournit deux modèles pour la création d'une transaction. Ces modèles sont présentés dans les rubriques suivantes.  
  
 [Implémentation d'une transaction implicite à l'aide de l'étendue de transaction](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions implicites à l'aide de la classe <xref:System.Transactions.TransactionScope>.  
  
 [Implémentation d'une transaction explicite à l'aide de CommittableTransaction](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions explicites à l'aide de la classe <xref:System.Transactions.CommittableTransaction>.  
  
### <a name="escalating-transaction-management"></a>Remontée de la gestion des transactions  

 Si une transaction doit accéder à une ressource dans un autre domaine d'application ou si vous voulez vous inscrire à un autre gestionnaire de ressources durables, la transaction est automatiquement remontée pour être managée par le MSDTC. La remontée des transactions est traitée dans la rubrique [remontée](transaction-management-escalation.md) de la gestion des transactions.  
  
### <a name="concurrency"></a>Accès concurrentiel  

 La rubrique [gestion de l’accès concurrentiel avec DependentTransaction](managing-concurrency-with-dependenttransaction.md) montre comment la concurrence peut être obtenue entre des tâches asynchrones à l’aide de la <xref:System.Transactions.DependentTransaction> classe.  
  
### <a name="com-interop"></a>COM+ Interop  

 La rubrique [interopérabilité avec Enterprise Services et les transactions com+](interoperability-with-enterprise-services-and-com-transactions.md) illustre la façon dont vous pouvez faire interagir vos transactions distribuées avec les transactions com+.  
  
### <a name="diagnostics"></a>Diagnostics  

 Les [suivis de diagnostic](diagnostic-traces.md) décrivent comment vous pouvez utiliser les codes de suivi générés par l' <xref:System.Transactions> infrastructure pour résoudre les erreurs dans vos applications.  
  
### <a name="working-within-aspnet"></a>Utilisation d'ASP.NET  

 La rubrique [utilisation de System. transactions dans ASP.net](using-system-transactions-in-aspnet.md) décrit comment vous pouvez utiliser correctement <xref:System.Transactions> dans une application ASP.net.
