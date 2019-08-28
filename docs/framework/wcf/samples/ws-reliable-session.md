---
title: WS Reliable Session
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: cc5afdeeeea2601eb22be316302aeacee570e5f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045379"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="45424-102">WS Reliable Session</span><span class="sxs-lookup"><span data-stu-id="45424-102">WS Reliable Session</span></span>
<span data-ttu-id="45424-103">Cet exemple montre l'utilisation des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="45424-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="45424-104">Les sessions fiables fournissent la prise en charge de la messagerie et des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="45424-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="45424-105">La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages.</span><span class="sxs-lookup"><span data-stu-id="45424-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="45424-106">Les sessions conservent l'état pour les clients entre les appels.</span><span class="sxs-lookup"><span data-stu-id="45424-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="45424-107">Cet exemple implémente des sessions permettant de conserver l'état du client et spécifie des assurances de remise par ordre d'arrivée.</span><span class="sxs-lookup"><span data-stu-id="45424-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45424-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="45424-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45424-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="45424-109">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="45424-110">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="45424-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45424-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="45424-111">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="45424-112">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="45424-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="45424-113">Les fonctionnalités de sessions fiables sont activées et configurées dans les fichiers de configuration d'application respectifs du client et du service.</span><span class="sxs-lookup"><span data-stu-id="45424-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="45424-114">Dans cet exemple, le service est hébergé dans les services IIS (Internet Information Services) et le client est une application console (.exe).</span><span class="sxs-lookup"><span data-stu-id="45424-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45424-115">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="45424-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="45424-116">L'exemple utilise le fichier `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="45424-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="45424-117">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="45424-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="45424-118">Le type de liaison est spécifié dans l’attribut `binding` de l’élément de point de terminaison, tel qu’indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="45424-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="45424-119">Le point de terminaison contient un attribut `bindingConfiguration` qui référence une configuration de liaison appelée « Binding1 ».</span><span class="sxs-lookup"><span data-stu-id="45424-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="45424-120">La configuration de liaison active les sessions fiables en `enabled` affectant à `true`l’attribut de la [ \<> ReliableSession](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) la valeur.</span><span class="sxs-lookup"><span data-stu-id="45424-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="45424-121">Les assurances de remise pour les sessions ordonnées sont contrôlées en affectant `true` ou `false` à l'attribut ordonné.</span><span class="sxs-lookup"><span data-stu-id="45424-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="45424-122">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="45424-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="45424-123">La classe d'implémentation de service implémente l'instanciation <xref:System.ServiceModel.InstanceContextMode.PerSession> afin de conserver une instance de classe distincte pour chaque client, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="45424-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="45424-124">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="45424-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="45424-125">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="45424-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45424-126">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="45424-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="45424-127">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="45424-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="45424-128">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45424-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="45424-129">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45424-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="45424-130">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45424-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
