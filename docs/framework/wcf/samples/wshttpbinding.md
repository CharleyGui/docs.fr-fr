---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 9eed3cbef75981b2b57eb24298aef1a5b0b4f15c
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876016"
---
# <a name="wshttpbinding"></a><span data-ttu-id="ab501-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ab501-102">WSHttpBinding</span></span>
<span data-ttu-id="ab501-103">Cet exemple montre comment implémenter un service et un client standard à l’aide de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ab501-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ab501-104">Cet exemple se compose d'un programme de console cliente (client.exe) et d'une bibliothèque de service hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="ab501-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="ab501-105">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="ab501-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="ab501-106">Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="ab501-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="ab501-107">Le client adresse des demandes synchrones à une opération mathématique donnée et le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="ab501-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="ab501-108">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ab501-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab501-109">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ab501-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab501-110">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ab501-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ab501-111">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="ab501-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab501-112">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ab501-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="ab501-113">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ab501-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ab501-114">Cet exemple expose le `ICalculator` de contrat à l’aide de la [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ab501-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="ab501-115">La configuration de cette liaison a été développée dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="ab501-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ab501-116">Sur l'élément de `binding` de base, la valeur `maxReceivedMessageSize` vous permet de configurer la taille maximale d'un message entrant (en octets).</span><span class="sxs-lookup"><span data-stu-id="ab501-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="ab501-117">La valeur `hostNameComparisonMode` vous permet de configurer la prise en compte du nom d'hôte lors du démultiplexage des messages vers le service.</span><span class="sxs-lookup"><span data-stu-id="ab501-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="ab501-118">La valeur `messageEncoding` vous permet de configurer l'utilisation de l'encodage texte ou MTOM pour les messages.</span><span class="sxs-lookup"><span data-stu-id="ab501-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="ab501-119">La valeur `textEncoding` vous permet de configurer l'encodage de caractères pour les messages.</span><span class="sxs-lookup"><span data-stu-id="ab501-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="ab501-120">La valeur `bypassProxyOnLocal` vous permet de configurer l'utilisation d'un proxy HTTP pour les communications locales.</span><span class="sxs-lookup"><span data-stu-id="ab501-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="ab501-121">La valeur `transactionFlow` configure la transmission de la transaction en cours (si une opération est configurée en ce sens).</span><span class="sxs-lookup"><span data-stu-id="ab501-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="ab501-122">Sur le [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) élément, la valeur booléenne détermine si les sessions fiables sont activées.</span><span class="sxs-lookup"><span data-stu-id="ab501-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="ab501-123">La valeur `ordered` configure l'activation du classement des messages.</span><span class="sxs-lookup"><span data-stu-id="ab501-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="ab501-124">La valeur `inactivityTimeout` configure la durée d'inactivité maximale avant son expiration.</span><span class="sxs-lookup"><span data-stu-id="ab501-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="ab501-125">Sur le [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), le `mode` valeur configure le mode de sécurité doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="ab501-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="ab501-126">Dans cet exemple, sécurité des messages est utilisée, c’est pourquoi le [ \<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) est spécifié à l’intérieur de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ab501-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="ab501-127">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="ab501-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ab501-128">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="ab501-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab501-129">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ab501-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ab501-130">Installer ASP.NET 4.0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="ab501-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ab501-131">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab501-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ab501-132">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab501-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ab501-133">Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab501-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
