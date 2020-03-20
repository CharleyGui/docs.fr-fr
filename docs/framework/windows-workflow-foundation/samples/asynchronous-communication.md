---
title: Communication asynchrone
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142874"
---
# <a name="asynchronous-communication"></a>Communication asynchrone
Cet exemple montre comment la communication entre deux différents services de la Fondation Windows Workflow (WF) se fait par défaut.  
  
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
  
1. Cliquez à droite sur la solution **AsynchroneCommunication** et sélectionnez **propriétés**.  
  
2. Dans **Common Properties**, sélectionnez Startup **Project**, et sélectionnez **Plusieurs projets de démarrage**.  
  
3. Déplacez **RentalApprovalService** à la première position de la liste, suivi par **CreditCheckService**, suivi par **Client**. Définissez l’action **Démarrer** sur les trois projets.  
  
4. Cliquez **sur OK**, et appuyez sur F5 pour exécuter l’échantillon.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
