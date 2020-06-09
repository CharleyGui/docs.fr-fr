---
title: Multiple Contracts
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: e8451c49395a1dad55c5afca419f47a8e856b61f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602503"
---
# <a name="multiple-contracts"></a><span data-ttu-id="f1e65-102">Multiple Contracts</span><span class="sxs-lookup"><span data-stu-id="f1e65-102">Multiple Contracts</span></span>
<span data-ttu-id="f1e65-103">L'exemple Multiples Contracts montre comment implémenter plusieurs contrats sur un service et comment configurer des points de terminaison pour communiquer avec chacun des contrats implémentés.</span><span class="sxs-lookup"><span data-stu-id="f1e65-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="f1e65-104">Cet exemple est basé sur le [prise en main](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f1e65-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="f1e65-105">Le service a été modifié afin de définir deux contrats, le contrat `ICalculator` et le contrat `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="f1e65-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1e65-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f1e65-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f1e65-107">La classe de service implémente à la fois les contrats `ICalculator` et `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="f1e65-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="f1e65-108">Vu que l'un des contrats requiert une session, le service utilise le mode d'instance <xref:System.ServiceModel.InstanceContextMode.PerSession> pour maintenir l'état sur la durée de vie de la session.</span><span class="sxs-lookup"><span data-stu-id="f1e65-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="f1e65-109">La configuration du service a été modifiée afin de définir deux points de terminaison et exposer chaque contrat.</span><span class="sxs-lookup"><span data-stu-id="f1e65-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="f1e65-110">Le point de terminaison `ICalculator` est exposé à l'adresse de base à l'aide d'une `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f1e65-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="f1e65-111">Le point de terminaison `ICalculatorSession` est exposé à l'adresse/la session de base à l'aide d'une `wsHttpBinding` avec l'attribut `bindingConfiguration` ayant la valeur `BindingWithSession`, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="f1e65-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="f1e65-112">Le code client généré inclut maintenant une classe de client pour le contrat `ICalculator` d'origine et pour le nouveau contrat `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="f1e65-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="f1e65-113">La configuration et le code client ont été modifiés pour communiquer avec chaque contrat au point de terminaison de service approprié.</span><span class="sxs-lookup"><span data-stu-id="f1e65-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="f1e65-114">Le client est une application console Windows (.exe).</span><span class="sxs-lookup"><span data-stu-id="f1e65-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="f1e65-115">Le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="f1e65-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="f1e65-116">La fenêtre de console cliente affiche les opérations envoyées à chacun des points de terminaison, d'abord le point de terminaison de base, puis le point de terminaison sécurisé.</span><span class="sxs-lookup"><span data-stu-id="f1e65-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f1e65-117">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f1e65-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f1e65-118">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1e65-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f1e65-119">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1e65-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f1e65-120">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1e65-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f1e65-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1e65-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1e65-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f1e65-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f1e65-123">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f1e65-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1e65-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f1e65-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
