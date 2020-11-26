---
title: Modèles de transaction
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: ce7eb74a3e06df8db2e6d8261faca16650e4e4f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242264"
---
# <a name="transaction-models"></a>Modèles de transaction

Cette rubrique décrit la relation entre les modèles de programmation de transactions et les composants d'infrastructure que Microsoft fournit.  
  
 Lorsque vous utilisez des transactions dans Windows Communication Foundation (WCF), il est important de comprendre que vous ne choisissez pas entre des modèles transactionnels différents, mais que vous utilisez des couches différentes d’un modèle intégré et cohérent.  
  
 Les sections suivantes décrivent les trois composants principaux d'une transaction.  
  
## <a name="windows-communication-foundation-transactions"></a>Transactions WCF (Windows Communication Foundation)  

 La prise en charge des transactions dans WCF vous permet d’écrire des services transactionnels. En outre, grâce à sa prise en charge du protocole WS-AtomicTransaction (WS-AT), les applications peuvent transmettre des transactions aux services Web générés à l’aide de WCF ou d’une technologie tierce.  
  
 Dans un service ou une application WCF, les fonctionnalités de transaction WCF fournissent des attributs et une configuration pour spécifier de façon déclarative comment et quand l’infrastructure doit créer, transmettre et synchroniser des transactions.  
  
## <a name="systemtransactions-transactions"></a>Transactions System.Transactions  

 L’espace de noms <xref:System.Transactions> fournit un modèle de programmation explicite basé sur la classe <xref:System.Transactions.Transaction>, ainsi qu’un modèle de programmation implicite à utilisant la classe <xref:System.Transactions.TransactionScope>, dans lequel l’infrastructure gère automatiquement les transactions.  
  
 Pour plus d’informations sur la création d’une application transactionnelle à l’aide de ces deux modèles, consultez [écriture d’une application transactionnelle](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Dans un service ou une application WCF, <xref:System.Transactions> fournit le modèle de programmation pour créer des transactions dans une application cliente et pour interagir explicitement avec une transaction, si nécessaire, au sein d’un service.  
  
## <a name="msdtc-transactions"></a>Transactions MSDTC  

 MSDTC (Microsoft Distributed Transaction Coordinator) est un gestionnaire de transactions qui prend en charge les transactions distribuées.  
  
 Pour plus d’informations, consultez le [Guide de référence du programmeur DTC](/previous-versions/windows/desktop/ms686108(v=vs.85)).  
  
 Dans un service ou une application WCF, MSDTC fournit l’infrastructure pour la coordination des transactions créées au sein d’un client ou d’un service.
