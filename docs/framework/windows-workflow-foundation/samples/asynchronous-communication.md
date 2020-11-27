---
title: Communication asynchrone
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: db5a8f415479967d7579357bd0c8058c7fb961c5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255843"
---
# <a name="asynchronous-communication"></a>Communication asynchrone

Cet exemple montre comment la communication entre deux services de Windows Workflow Foundation différents (WF) est effectuée de façon asynchrone par défaut.  
  
## <a name="demonstrates"></a>Illustre le  

 Communication asynchrone entre des services [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  
  
## <a name="discussion"></a>Discussions  

 Cet exemple montre comment la communication entre des applications [!INCLUDE[wf1](../../../../includes/wf1-md.md)] s'effectue de façon asynchrone à l'aide des activités de messagerie fournies par le .NET Framework.  
  
 Cet exemple est composé des trois projets suivants :  
  
 CreditCheckService  
 Ce service reçoit le niveau de crédit d'une personne particulière ou la valeur de l'élément à acquérir, puis décide si le crédit est accordé à la personne.  
  
 RentalApprovalService  
 Ce service reçoit une application d'une personne qui a besoin d'un crédit. Il communique de façon asynchrone avec `CreditCheckService` pour décider si l'application de crédit est valide.  
  
 Client  
 Le client communique de façon synchrone avec `RentalApprovalService` pour savoir si le crédit est approuvé.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Cliquez avec le bouton droit sur la solution **AsynchronousCommunication** et sélectionnez **Propriétés**.  
  
2. Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis sélectionnez **plusieurs projets de démarrage**.  
  
3. Déplacez **RentalApprovalService** à la première position de la liste, suivie de **CreditCheckService**, puis du **client**. Définissez l’action de **démarrage** sur les trois projets.  
  
4. Cliquez sur **OK**, puis appuyez sur F5 pour exécuter l’exemple.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
