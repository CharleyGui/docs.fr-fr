---
title: BasicBinding with Transport Security
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
ms.openlocfilehash: adf245d29ca57d919957276dfc54d82a0f45373b
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144875"
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="ae4df-102">BasicBinding with Transport Security</span><span class="sxs-lookup"><span data-stu-id="ae4df-102">BasicBinding with Transport Security</span></span>

<span data-ttu-id="ae4df-103">Cet exemple illustre l’utilisation de la sécurité de transport SSL avec la liaison de base.</span><span class="sxs-lookup"><span data-stu-id="ae4df-103">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="ae4df-104">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="ae4df-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae4df-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ae4df-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ae4df-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ae4df-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ae4df-107">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ae4df-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae4df-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ae4df-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`

## <a name="sample-details"></a><span data-ttu-id="ae4df-109">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae4df-109">Sample Details</span></span>

<span data-ttu-id="ae4df-110">Par défaut, la liaison de base prend en charge la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae4df-110">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="ae4df-111">L’exemple indique comment activer la sécurité de transport pour la liaison  de base.</span><span class="sxs-lookup"><span data-stu-id="ae4df-111">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="ae4df-112">Vous devez créer un certificat et l’assigner en utilisant l’Assistant Certificat de serveur web avant d’exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="ae4df-112">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>

> [!NOTE]
> <span data-ttu-id="ae4df-113">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ae4df-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ae4df-114">Le code du programme dans l’exemple est identique à celui du service [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="ae4df-114">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="ae4df-115">La définition du point de terminaison et la définition de la liaison dans les paramètres du fichier de configuration sont modifiées pour permettre une communication sécurisée, comme le montre l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="ae4df-115">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
   </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"/>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="ae4df-116">Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert. exe, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse HTTPs : dans votre navigateur, telle que `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="ae4df-116">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="ae4df-117">Pour permettre au client Windows Communication Foundation (WCF) d’utiliser un certificat de test, du code supplémentaire est ajouté au client pour supprimer l’alerte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ae4df-117">To allow the Windows Communication Foundation (WCF) client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="ae4df-118">Ce code, et la classe qui l'accompagne, n'est pas nécessaire lors de l'utilisation de vrais certificats.</span><span class="sxs-lookup"><span data-stu-id="ae4df-118">This code, and the accompanying class, is not necessary when using real certificates.</span></span>

```csharp
// This code is required only for test certificates such as those
// created by Makecert.exe.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```

<span data-ttu-id="ae4df-119">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="ae4df-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ae4df-120">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="ae4df-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae4df-121">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae4df-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ae4df-122">Installez ASP.NET 4,0 à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ae4df-122">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="ae4df-123">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae4df-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="ae4df-124">Vérifiez que vous avez effectué les [instructions d’installation du certificat de serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="ae4df-124">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="ae4df-125">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae4df-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="ae4df-126">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae4df-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>
