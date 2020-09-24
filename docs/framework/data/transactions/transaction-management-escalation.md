---
title: Remontée de la gestion des transactions
description: En savoir plus sur la remontée de la gestion des transactions dans .NET, qui est le processus de migration d’une transaction d’un des composants d’un gestionnaire de transactions vers un autre.
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: 83abca2e2c9acf53ce3f72d6bc55a82964b99cb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155437"
---
# <a name="transaction-management-escalation"></a>Remontée de la gestion des transactions

Windows héberge un ensemble de services et de modules qui constituent ensemble un gestionnaire de transactions. La remontée de la gestion des transactions décrit le processus de migration d'une transaction de l'un des composants du gestionnaire de transactions à un autre.  
  
 <xref:System.Transactions> comprend un composant de gestionnaire de transactions qui coordonne une transaction impliquant au maximum une seule ressource durable ou plusieurs ressources volatiles. Le gestionnaire de transactions n'utilise que des appels intra-domaines d'application, il offre donc d'excellentes performances. Les développeurs n'ont pas besoin d'interagir directement avec le gestionnaire de transactions. À la place, l'espace de noms <xref:System.Transactions> fournit une infrastructure commune qui définit les interfaces, le comportement commun et les classes d'assistance.  
  
 Lorsque vous souhaitez fournir la transaction à un objet dans un autre domaine d’application (y compris au-delà des limites du processus et de l’ordinateur) sur le même ordinateur, l' <xref:System.Transactions> infrastructure remonte automatiquement la transaction à gérer par le Microsoft Distributed Transaction Coordinator (MSDTC). La remontée se produit également en cas d'inscription à un autre gestionnaire de ressources durables. Une fois remontée, la transaction reste managée à son état élevé jusqu'à ce qu'elle soit terminée.  
  
 Entre la transaction <xref:System.Transactions> et la transaction MSDTC, il existe un type intermédiaire de transaction disponible via la PSPE (Promotable Single Phase Enlistment). La PSPE est un autre mécanisme important de <xref:System.Transactions>, conçu pour l'optimisation des performances. Il permet à une ressource durable distante, située dans un domaine d'application, un processus ou un ordinateur différent, de participer à une transaction <xref:System.Transactions> sans la faire remonter vers une transaction MSDTC. Pour plus d’informations sur PSPE, consultez [inscription de ressources en tant que participants dans une transaction](enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Initialisation de la remontée  

 La remontée de transactions réduit les performances car le MSDTC réside dans un processus séparé et remonter une transaction vers le MSDTC entraîne l'envoi de messages entre les processus. Pour améliorer les performances, vous devez différer ou éviter toute remontée vers le MSDTC ; vous devez donc connaître la méthode et l'heure d'initialisation de la remontée.  
  
 Tant que l'infrastructure <xref:System.Transactions> gère plusieurs ressources volatiles et au moins une ressource durable qui prend en charge les notifications à phase unique, la transaction reste la propriété de l'infrastructure <xref:System.Transactions>. Le gestionnaire de transactions ne se rend disponible que pour les ressources qui appartiennent au même domaine d'application et pour lesquelles aucune connexion (écriture du résultat de la transaction sur le disque) n'est requise. Une remontée qui provoque le transfert de la propriété de la transaction vers le MSDTC par l'infrastructure <xref:System.Transactions> se produit :  
  
- lorsqu'au moins une ressource durable qui ne prend pas en charge les notifications à phase unique est inscrite pour la transaction.  
  
- lorsqu'au moins deux ressources durables qui prennent en charge les notifications à phase unique sont inscrites pour la transaction. Par exemple, l’inscription d’une connexion unique avec SQL Server 2005 ne provoque pas la promotion d’une transaction. Toutefois, chaque fois que vous ouvrez une deuxième connexion à une base de données SQL Server 2005, ce qui entraîne l’inscription de la base de données, l' <xref:System.Transactions> infrastructure détecte qu’il s’agit de la deuxième ressource durable de la transaction et la transmet à une transaction MSDTC.  
  
- Une requête visant à « marshaler » la transaction vers un domaine d'application ou un processus différent est appelée. Par exemple, la sérialisation de l'objet de transaction au-delà d'une limite de domaine d'application. L'objet de transaction est marshalé par valeur, ce qui signifie que chaque tentative de passage au-delà d'une limite de domaine d'application (même au sein d'un même processus) entraîne la sérialisation de l'objet de transaction. Vous pouvez passer les objets de transaction en appelant une méthode distante qui utilise <xref:System.Transactions.Transaction> en tant que paramètre ou tenter d'accéder à un composant distant pris en charge par transaction. Cette opération entraîne la sérialisation de l'objet de transaction et provoque une remontée, comme lorsqu'une transaction est sérialisée au-delà d'un domaine d'application. Il est distribué et le gestionnaire de transactions local devient inadapté.  
  
 Le tableau suivant répertorie toutes les exceptions susceptibles d'être levées lors de la remontée.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Tentative de remontée d'une transaction avec un niveau d'isolation égal à <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|Le gestionnaire de transactions est arrêté.|  
|<xref:System.Transactions.TransactionException>|La remontée échoue et l'application est abandonnée.|
