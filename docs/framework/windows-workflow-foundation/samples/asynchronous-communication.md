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
# <a name="asynchronous-communication"></a><span data-ttu-id="167fe-102">Communication asynchrone</span><span class="sxs-lookup"><span data-stu-id="167fe-102">Asynchronous Communication</span></span>

<span data-ttu-id="167fe-103">Cet exemple montre comment la communication entre deux services de Windows Workflow Foundation différents (WF) est effectuée de façon asynchrone par défaut.</span><span class="sxs-lookup"><span data-stu-id="167fe-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="167fe-104">Illustre le</span><span class="sxs-lookup"><span data-stu-id="167fe-104">Demonstrates</span></span>  

 <span data-ttu-id="167fe-105">Communication asynchrone entre des services [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="167fe-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="167fe-106">Discussions</span><span class="sxs-lookup"><span data-stu-id="167fe-106">Discussion</span></span>  

 <span data-ttu-id="167fe-107">Cet exemple montre comment la communication entre des applications [!INCLUDE[wf1](../../../../includes/wf1-md.md)] s'effectue de façon asynchrone à l'aide des activités de messagerie fournies par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="167fe-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="167fe-108">Cet exemple est composé des trois projets suivants :</span><span class="sxs-lookup"><span data-stu-id="167fe-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="167fe-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="167fe-109">CreditCheckService</span></span>  
 <span data-ttu-id="167fe-110">Ce service reçoit le niveau de crédit d'une personne particulière ou la valeur de l'élément à acquérir, puis décide si le crédit est accordé à la personne.</span><span class="sxs-lookup"><span data-stu-id="167fe-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="167fe-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="167fe-111">RentalApprovalService</span></span>  
 <span data-ttu-id="167fe-112">Ce service reçoit une application d'une personne qui a besoin d'un crédit.</span><span class="sxs-lookup"><span data-stu-id="167fe-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="167fe-113">Il communique de façon asynchrone avec `CreditCheckService` pour décider si l'application de crédit est valide.</span><span class="sxs-lookup"><span data-stu-id="167fe-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="167fe-114">Client</span><span class="sxs-lookup"><span data-stu-id="167fe-114">Client</span></span>  
 <span data-ttu-id="167fe-115">Le client communique de façon synchrone avec `RentalApprovalService` pour savoir si le crédit est approuvé.</span><span class="sxs-lookup"><span data-stu-id="167fe-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="167fe-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="167fe-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="167fe-117">Cliquez avec le bouton droit sur la solution **AsynchronousCommunication** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="167fe-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="167fe-118">Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis sélectionnez **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="167fe-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="167fe-119">Déplacez **RentalApprovalService** à la première position de la liste, suivie de **CreditCheckService**, puis du **client**.</span><span class="sxs-lookup"><span data-stu-id="167fe-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="167fe-120">Définissez l’action de **démarrage** sur les trois projets.</span><span class="sxs-lookup"><span data-stu-id="167fe-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="167fe-121">Cliquez sur **OK**, puis appuyez sur F5 pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="167fe-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="167fe-122">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="167fe-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="167fe-123">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="167fe-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="167fe-124">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="167fe-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="167fe-125">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="167fe-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
