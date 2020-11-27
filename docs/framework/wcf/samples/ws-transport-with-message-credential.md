---
title: WS Transport With Message Credential
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 673eb864bd21a2092f30a9f3ad6f6e6c368eea00
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252307"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="0d9f8-102">WS Transport With Message Credential</span><span class="sxs-lookup"><span data-stu-id="0d9f8-102">WS Transport With Message Credential</span></span>

<span data-ttu-id="0d9f8-103">Cet exemple montre l'utilisation de la sécurité de transport SSL en association avec les informations d'identification du client contenues dans le message.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="0d9f8-104">Cet exemple utilise la liaison `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="0d9f8-105">Par défaut, la liaison `wsHttpBinding` assure la communication HTTP.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="0d9f8-106">En cas de configuration pour la sécurité du transport, la liaison prend en charge la communication HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="0d9f8-107">HTTPS assure la protection de la confidentialité et de l'intégrité des messages transmis sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="0d9f8-108">Toutefois l'ensemble des mécanismes d'authentification qui peuvent être utilisés pour authentifier le client auprès du service est limité à ceux pris en charge par le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="0d9f8-109">Windows Communication Foundation (WCF) offre un `TransportWithMessageCredential` mode de sécurité conçu pour surmonter cette limitation.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="0d9f8-110">Lorsque ce mode de sécurité est configuré, la sécurité du transport est utilisée pour assurer la confidentialité et l'intégrité des messages transmis et procéder à l'authentification du service.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="0d9f8-111">Cependant, l'authentification du client est effectuée en plaçant les informations d'identification du client directement dans le message.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="0d9f8-112">Vous pouvez ainsi utiliser tout type d'information d'identification pris en charge par le mode de sécurité du message pour authentifier le client, tout en conservant les avantages du mode de sécurité du transport en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="0d9f8-113">Dans cet exemple, un type d'information d'identification `UserName` est utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="0d9f8-114">Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-114">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0d9f8-115">La liaison `wsHttpBinding` est spécifiée et configurée dans les fichiers de configuration de l'application pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d9f8-116">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0d9f8-117">Le code du programme dans l’exemple est presque identique à celui du service [prise en main](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="0d9f8-117">The program code in the sample is almost identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="0d9f8-118">Il y a une opération supplémentaire fournie par le contrat de service : `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="0d9f8-119">Cette opération retourne le nom de l'identité de l'appelant à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="0d9f8-120">Vous devez créer un certificat et l'assigner en utilisant l'Assistant Certificat de serveur Web avant de générer et exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="0d9f8-121">La définition du point de terminaison et la définition de la liaison dans les paramètres du fichier de configuration activent le mode de sécurité `TransportWithMessageCredential`, comme le montre l'exemple de configuration suivant pour le client.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0d9f8-122">L’adresse spécifiée utilise le `https://` schéma.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-122">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="0d9f8-123">La configuration de la liaison définit le mode de sécurité au mode `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="0d9f8-124">Le même mode de sécurité doit être spécifié dans le fichier Web.config du service.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="0d9f8-125">Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert.exe, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse https : par exemple  `https://localhost/servicemodelsamples/service.svc` , à partir de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="0d9f8-126">Pour permettre au client WCF de fonctionner avec un certificat de test sur place, du code supplémentaire a été ajouté au client pour supprimer l’alerte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="0d9f8-127">Ce code, et la classe qui l'accompagne, n'est pas requis lors de l'utilisation de certificats de production.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="0d9f8-128">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0d9f8-129">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="0d9f8-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d9f8-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="0d9f8-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0d9f8-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d9f8-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0d9f8-132">Vérifiez que vous avez effectué les [instructions d’installation du certificat de serveur Internet Information Services (IIS)](iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="0d9f8-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="0d9f8-133">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d9f8-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="0d9f8-134">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d9f8-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
