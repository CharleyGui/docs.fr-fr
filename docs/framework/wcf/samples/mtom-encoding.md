---
title: MTOM Encoding
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: ab8abdf79304037f2b4039407115a3f64a0afa4e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424069"
---
# <a name="mtom-encoding"></a><span data-ttu-id="c2e1c-102">MTOM Encoding</span><span class="sxs-lookup"><span data-stu-id="c2e1c-102">MTOM Encoding</span></span>
<span data-ttu-id="c2e1c-103">Cet exemple montre l'utilisation de l'encodage de message MTOM (Message Transmission Optimization Mechanism) à l'aide de WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="c2e1c-104">MTOM est un mécanisme permettant de transmettre des pièces jointes binaires de grande taille avec des messages SOAP sous forme d'octets bruts, et d'obtenir ainsi des messages plus petits.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2e1c-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2e1c-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-106">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c2e1c-107">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2e1c-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2e1c-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-108">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="c2e1c-109">Par défaut, WSHttpBinding envoie et reçoit des messages sous forme de texte XML normal.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="c2e1c-110">Pour permettre l’envoi et la réception de messages MTOM, définissez l’attribut `messageEncoding` sur la configuration de la liaison (tel qu’indiqué dans l’exemple de code suivant), ou directement sur la liaison à l’aide de la propriété `MessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="c2e1c-111">Le service ou le client peut maintenant envoyer et recevoir des messages MTOM.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="c2e1c-112">L'encodeur MTOM permet d'optimiser des tableaux d'octets et des flux.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="c2e1c-113">Dans cet exemple, l'opération utilise un paramètre `Stream` et peut donc être optimisée.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="c2e1c-114">Le contrat choisi pour cet exemple transmet les données binaires au service et reçoit le nombre d'octets téléchargé comme valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="c2e1c-115">Lorsque le service est installé et que le client est exécuté, il imprime le nombre 1 000, qui indique que tous l'ensemble des 1 000 octets ont été reçus.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="c2e1c-116">Le reste de la sortie répertorie les tailles de message optimisées et non optimisées des diverses charges utiles.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c2e1c-117">Le but de l'utilisation de MTOM est d'optimiser la transmission de charges utiles binaires de grande taille.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="c2e1c-118">L'envoi d'un message SOAP à l'aide de MTOM entraîne une surcharge significative pour les charges utiles binaires de petite taille, mais s'avère très avantageux lorsqu'elles passent à quelques milliers d'octets.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="c2e1c-119">La raison à cela est que le texte XML normal encode des données binaires à l'aide de Base64, qui requiert quatre caractères tous les trois octets, et augmente la taille des données d'un tiers.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="c2e1c-120">MTOM peut transmettre des données binaires sous forme d'octets bruts, ce qui permet de gagner du temps lors de l'encodage et du décodage et d'obtenir des messages plus petits.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="c2e1c-121">Le seuil de quelques milliers d'octets est petit comparé aux photographies numériques et documents professionnels actuels.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2e1c-122">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c2e1c-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2e1c-123">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c2e1c-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="c2e1c-124">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2e1c-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="c2e1c-125">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2e1c-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c2e1c-126">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2e1c-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
