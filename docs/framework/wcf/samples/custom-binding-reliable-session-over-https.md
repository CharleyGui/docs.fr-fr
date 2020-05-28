---
title: Custom Binding Reliable Session over HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: c31f8a5b4e3771f6c6e8de41e6b098474c34cf77
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144862"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="838b6-102">Custom Binding Reliable Session over HTTPS</span><span class="sxs-lookup"><span data-stu-id="838b6-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="838b6-103">Cet exemple illustre l'utilisation de la sécurité de transport SSL avec des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="838b6-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="838b6-104">Les sessions fiables implémentent le protocole WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="838b6-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="838b6-105">Vous pouvez obtenir une session fiable sécurisée en composant WS-Security sur des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="838b6-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="838b6-106">Mais parfois, vous pouvez choisir d'utiliser à la place la sécurité de transport HTTP avec SSL.</span><span class="sxs-lookup"><span data-stu-id="838b6-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="838b6-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="838b6-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="838b6-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="838b6-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="838b6-109">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="838b6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="838b6-110">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="838b6-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="838b6-111">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="838b6-111">Sample Details</span></span>  
 <span data-ttu-id="838b6-112">SSL garantit que les paquets eux-mêmes sont sécurisés.</span><span class="sxs-lookup"><span data-stu-id="838b6-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="838b6-113">Il est important de noter que cela diffère de la sécurisation de la session fiable à l'aide de WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="838b6-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="838b6-114">Pour utiliser la session fiable sur HTTPS, vous devez créer une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="838b6-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="838b6-115">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="838b6-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="838b6-116">Une liaison personnalisée est créée à l’aide de l’élément de liaison de session fiable et du [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) .</span><span class="sxs-lookup"><span data-stu-id="838b6-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="838b6-117">La configuration suivante est celle de la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="838b6-117">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="838b6-118">Le code du programme dans l’exemple est identique à celui du service [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="838b6-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="838b6-119">Vous devez créer un certificat et l'assigner en utilisant l'Assistant Certificat de serveur Web avant de générer et exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="838b6-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="838b6-120">La définition du point de terminaison et la définition de la liaison dans les paramètres du fichier de configuration permettent l’utilisation de la liaison personnalisée comme le montre l’exemple de configuration suivant pour le client.</span><span class="sxs-lookup"><span data-stu-id="838b6-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="838b6-121">L’adresse spécifiée utilise le `https://` schéma.</span><span class="sxs-lookup"><span data-stu-id="838b6-121">The address specified uses the `https://` scheme.</span></span>  
  
 <span data-ttu-id="838b6-122">Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert. exe, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse https : par exemple `https://localhost/servicemodelsamples/service.svc` , à partir de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="838b6-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="838b6-123">Pour permettre au client Windows Communication Foundation (WCF) d’utiliser un certificat de test sur place, du code supplémentaire a été ajouté au client pour supprimer l’alerte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="838b6-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="838b6-124">Ce code, et la classe qui l'accompagne, n'est pas requis lors de l'utilisation de certificats de production.</span><span class="sxs-lookup"><span data-stu-id="838b6-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="838b6-125">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="838b6-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="838b6-126">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="838b6-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="838b6-127">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="838b6-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="838b6-128">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="838b6-128">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="838b6-129">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="838b6-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="838b6-130">Vérifiez que vous avez effectué les [instructions d’installation du certificat de serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="838b6-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="838b6-131">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="838b6-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="838b6-132">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="838b6-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
