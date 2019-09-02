---
title: Écriture d’une application transactionnelle
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 318771c83a5b7ebc0f3fb2bb8c59240269a2dea9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205825"
---
# <a name="writing-a-transactional-application"></a>Écriture d’une application transactionnelle
En tant que programmeur d'applications transactionnelles, vous pouvez bénéficier des deux modèles de programmation fournis par l'espace de noms <xref:System.Transactions> pour créer une transaction. Vous pouvez utiliser le modèle de programmation explicite à l' <xref:System.Transactions.Transaction> aide de la classe, ou le modèle de programmation implicite dans lequel les transactions sont gérées automatiquement <xref:System.Transactions.TransactionScope> par l’infrastructure, à l’aide de la classe. Nous vous recommandons d’utiliser le modèle de transaction implicite pour le développement. Vous trouverez plus d’informations sur l’utilisation d’une étendue de transaction dans la rubrique [implémentation d’une transaction implicite à l’aide](implementing-an-implicit-transaction-using-transaction-scope.md) d’une étendue de transaction.  
  
 Les deux modèles prennent en charge la validation d'une transaction lorsque le programme atteint un état cohérent. Si la validation réussit, la transaction est validée durablement. Si la validation échoue, la transaction est abandonnée. Si le programme d'application ne parvient pas à terminer la transaction avec succès, il tente d'abandonner et d'annuler les effets de la transaction.  
  
## <a name="in-this-section"></a>Dans cette section  
  
### <a name="creating-a-transaction"></a>Création d'une transaction  
 L'espace de noms <xref:System.Transactions> fournit deux modèles pour la création d'une transaction. Ces modèles sont présentés dans les rubriques suivantes.  
  
 [Implémentation d’une transaction implicite à l’aide de l’étendue de transaction](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions implicites à l'aide de la classe <xref:System.Transactions.TransactionScope>.  
  
 [Implémentation d’une transaction explicite à l’aide de CommittableTransaction](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions explicites à l'aide de la classe <xref:System.Transactions.CommittableTransaction>.  
  
### <a name="escalating-transaction-management"></a>Remontée de la gestion des transactions  
 Si une transaction doit accéder à une ressource dans un autre domaine d'application ou si vous voulez vous inscrire à un autre gestionnaire de ressources durables, la transaction est automatiquement remontée pour être managée par le MSDTC. La remontée des transactions est traitée dans la rubrique remontée de la [gestion des transactions](transaction-management-escalation.md) .  
  
### <a name="concurrency"></a>Concurrence  
 La rubrique [gestion de l’accès concurrentiel avec DependentTransaction](managing-concurrency-with-dependenttransaction.md) montre comment la concurrence peut être obtenue entre des tâches asynchrones à l’aide de la <xref:System.Transactions.DependentTransaction> classe.  
  
### <a name="com-interop"></a>COM+ Interop  
 La rubrique [interopérabilité avec Enterprise Services et les transactions com+](interoperability-with-enterprise-services-and-com-transactions.md) illustre la façon dont vous pouvez faire interagir vos transactions distribuées avec les transactions com+.  
  
### <a name="diagnostics"></a>Diagnostics  
 Les suivis de [diagnostic](diagnostic-traces.md) décrivent comment vous pouvez utiliser les codes de suivi <xref:System.Transactions> générés par l’infrastructure pour résoudre les erreurs dans vos applications.  
  
### <a name="working-within-aspnet"></a>Utilisation d'ASP.NET  
 La rubrique [utilisation de System. transactions dans ASP.net](using-system-transactions-in-aspnet.md) décrit comment vous pouvez utiliser <xref:System.Transactions> correctement dans une application ASP.net.
