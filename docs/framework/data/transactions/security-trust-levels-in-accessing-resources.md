---
title: Niveaux de confiance de sécurité dans l'accès aux ressources
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 847467b964e86f6d13be6ba103162512270fa684
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596756"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Niveaux de confiance de sécurité dans l'accès aux ressources
Cette rubrique présente la restriction de l'accès aux types de ressources exposés par <xref:System.Transactions>.  
  
 Il existe trois niveaux de confiance principaux pour <xref:System.Transactions>. Les niveaux de confiance sont définis d'après les types de ressources que <xref:System.Transactions> expose et le niveau de confiance nécessaire pour accéder à ces ressources. Les ressources auxquelles <xref:System.Transactions> donne accès sont la mémoire système, les ressources partagées au niveau du processus et les ressources système. Ces niveaux sont les suivants :  
  
- **AllowPartiallyTrustedCallers** (APTCA) pour les applications utilisant des transactions au sein d’un seul domaine d’application.  
  
- **DistributedTransactionPermission** (DTP) pour les applications utilisant des transactions distribuées.  
  
- Confiance totale pour les ressources durables, les applications de gestion de configuration et les applications d'interopérabilité héritées.  
  
> [!NOTE]
>  N'appelez pas les interfaces inscrites avec des contextes personnifiés.  
  
## <a name="trust-levels"></a>Niveaux de confiance  
  
### <a name="aptca-partial-trust"></a>APTCA (confiance partielle)  
 Le <xref:System.Transactions> assembly peut être appelé par du code partiellement fiable, car il a été marqué avec la **AllowPartiallyTrustedCallers** attribut (APTCA). Cet attribut supprime essentiellement l’implicite <xref:System.Security.Permissions.SecurityAction.LinkDemand> pour le **FullTrust** jeu d’autorisations qui est habituellement automatiquement placé dans chaque méthode publiquement accessible dans chaque type. Toutefois, certains types et membres requièrent encore des autorisations plus élevées.  
  
 L'attribut APTCA permet aux applications d'utiliser des transactions en confiance partielle au sein d'un domaine d'application unique. Cela active les transactions non remontées et les inscriptions volatiles qui peuvent être utilisées pour la gestion des erreurs. Une table de hachage traitée et l'application qui l'utilise en sont des exemples. Il est possible d'ajouter ou de supprimer des données de la table de hachage sous une seule transaction. En cas de restauration ultérieure de la transaction, toutes les modifications apportées à la table de hachage sous cette transaction peuvent être annulées.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Lorsqu'une transaction <xref:System.Transactions> est remontée pour gestion par le MSDTC, <xref:System.Transactions> demande à <xref:System.Transactions.DistributedTransactionPermission> (DTP) de créer la transaction distribuée. Cela signifie que le code provoquant la remontée de la transaction (par exemple, via la sérialisation ou les inscriptions durables supplémentaires) doit se voir accorder la DTP. Le code qui a initialement permis de créer la transaction <xref:System.Transactions> ne requiert pas nécessairement cette autorisation.  
  
### <a name="fulltrust-link-demands"></a>Demandes de liaison FullTrust  
 Ce niveau d'autorisation est conçu pour restreindre les applications qui écrivent dans des ressources durables. Après défaillance, l'application doit pouvoir effectuer la récupération avec le gestionnaire de transactions pour déterminer le résultat final de la transaction, de façon à pouvoir mettre à jour les données permanentes. Ce type d'application est connu en tant que gestionnaire de source durable. SQL est un exemple classique de ce type d'application.  
  
 Pour activer la récupération, ce type d'application est capable de consommer de façon permanente des ressources système. Cela est dû au fait que le gestionnaire de transactions récupérables doit mémoriser les transactions qui ont été validées jusqu'à ce qu'il soit en mesure de confirmer que tous les gestionnaires de ressources durables participant à la transaction ont reçu le résultat. Par conséquent, ce type d'application requiert une confiance totale et ne doit pas être exécuté sans que ce niveau de confiance n'ait été accordé.  
  
 Pour plus d’informations sur les inscriptions durables et la récupération, consultez le [l’inscription de ressources comme Participants à une Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) et [exécution de la récupération](../../../../docs/framework/data/transactions/performing-recovery.md) rubriques.  
  
 Les applications qui effectuent un travail d'interopérabilité héritée avec COM+ sont également requises pour une confiance totale.  
  
 Voici une liste de types et membres qui ne sont pas partiellement pouvant être appelés par le code fiable, car elles sont décorées avec le **FullTrust** attribut de sécurité déclarative :  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Seul l’appelant immédiat est nécessaire pour disposer le **FullTrust** jeu d’autorisations à utiliser les types ou les méthodes ci-dessus.
