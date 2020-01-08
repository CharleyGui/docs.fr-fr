---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 1e0290a4df688d39f84086dc4c1b41712f81076a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345144"
---
# <a name="srmp"></a><span data-ttu-id="f5922-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="f5922-102">SRMP</span></span>
<span data-ttu-id="f5922-103">Cet exemple illustre comment établir une communication en file d'attente avec transaction à l'aide de MSMQ (Message Queuing) sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="f5922-104">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5922-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f5922-105">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5922-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f5922-106">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5922-106">The service receives messages from the queue.</span></span> <span data-ttu-id="f5922-107">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="f5922-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="f5922-108">Le protocole MSMQ permet d'utiliser HTTP (notamment HTTPS) pour l'envoi des messages à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5922-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="f5922-109">Dans cet exemple, nous décrivons l’utilisation de la communication en file d’attente Windows Communication Foundation (WCF) et l’envoi de messages via HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="f5922-110">Le protocole MSMQ utilise le protocole SRMP basé sur le protocole SOAP pour communiquer sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5922-111">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f5922-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f5922-112">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5922-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f5922-113">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5922-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f5922-114">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5922-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f5922-115">Avant d’exécuter l’exemple dans **Ajouter/supprimer des composants Windows**, assurez-vous que MSMQ est installé avec la prise en charge http.</span><span class="sxs-lookup"><span data-stu-id="f5922-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="f5922-116">L'installation de la prise en charge HTTP installe automatiquement les services IIS et ajoute la prise en charge de ce protocole dans IIS pour MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f5922-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="f5922-117">Si vous souhaitez vous assurer que le transport HTTP est bien utilisé pour la communication, configurez MSMQ de sorte à ce qu'il s'exécute en mode renforcé.</span><span class="sxs-lookup"><span data-stu-id="f5922-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="f5922-118">Cela garantit qu'aucun message ne peut être transmis à une file d'attente hébergée sur l'ordinateur, quelle qu'elle soit, à l'aide d'un transport autre que HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="f5922-119">Une fois que vous avez sélectionné MSMQ pour s’exécuter en mode renforcé, l’ordinateur doit être redémarré sur Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="f5922-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="f5922-120">Exécutez le service.</span><span class="sxs-lookup"><span data-stu-id="f5922-120">Run the service.</span></span>  
  
8. <span data-ttu-id="f5922-121">Exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="f5922-121">Run the client.</span></span> <span data-ttu-id="f5922-122">Assurez-vous de remplacer les occurrences de localhost de l'adresse de point de terminaison par le nom de l'ordinateur ou l'adresse IP appropriée.</span><span class="sxs-lookup"><span data-stu-id="f5922-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="f5922-123">Le client envoie un message, puis s'arrête.</span><span class="sxs-lookup"><span data-stu-id="f5922-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5922-124">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f5922-124">Requirements</span></span>  
 <span data-ttu-id="f5922-125">Pour exécuter cet exemple, le protocole MSMQ ainsi que les services IIS doivent être installés sur l'ordinateur du client et celui du service.</span><span class="sxs-lookup"><span data-stu-id="f5922-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f5922-126">Montre</span><span class="sxs-lookup"><span data-stu-id="f5922-126">Demonstrates</span></span>  
 <span data-ttu-id="f5922-127">L’exemple montre comment envoyer des messages de mise en file d’attente WCF à l’aide de MSMQ sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="f5922-128">Ce type de transmission est également appelé messagerie SRMP.</span><span class="sxs-lookup"><span data-stu-id="f5922-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="f5922-129">Lorsqu'un message en file d'attente est envoyé, le protocole MSMQ sur l'ordinateur expéditeur transfère les messages vers le gestionnaire de files d'attente de réception via le transport TCP ou HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="f5922-130">Lorsque l'utilisateur sélectionne SRMP, cela signifie que le transport HTTP sera utilisé pour le transfert des messages vers la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5922-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="f5922-131">Le protocole SRMP Secure permet d'utiliser HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f5922-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5922-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5922-132">Example</span></span>  
 <span data-ttu-id="f5922-133">L'exemple de code est basé sur l'exemple avec transaction.</span><span class="sxs-lookup"><span data-stu-id="f5922-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="f5922-134">Les modalités d'envoi et de réception des messages à et depuis la file d'attente à l'aide du protocole SRMP sont identiques à celles utilisées pour l'envoi et la réception des messages à l'aide d'un protocole natif.</span><span class="sxs-lookup"><span data-stu-id="f5922-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="f5922-135">La configuration du client est modifiée en fonction du protocole de transfert vers la file d'attente souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f5922-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="f5922-136">Il peut s'agir de l'un des protocoles suivants : natif, SRMP ou SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="f5922-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="f5922-137">Par défaut, le protocole de transfert correspond au protocole natif.</span><span class="sxs-lookup"><span data-stu-id="f5922-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="f5922-138">Dans cet exemple, les configurations du client et du service spécifient l'utilisation du protocole SRMP.</span><span class="sxs-lookup"><span data-stu-id="f5922-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="f5922-139">Le protocole SRMP présente des restrictions en matière de sécurité de niveau transport.</span><span class="sxs-lookup"><span data-stu-id="f5922-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="f5922-140">La sécurité de niveau transport MSMQ par défaut requiert Active Directory, lequel nécessite que les gestionnaires respectifs des files d'attente d'envoi et de réception figurent dans le même domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="f5922-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="f5922-141">Cette spécification n'est pas compatible avec l'envoi des messages sur la limite HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5922-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="f5922-142">Dans un tel cas, la sécurité de niveau transport par défaut ne peut pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="f5922-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="f5922-143">La sécurité de niveau transport doit avoir pour valeur Certificat lorsqu'une telle sécurité est souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f5922-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="f5922-144">La sécurité de niveau message peut également être utilisée pour sécuriser les messages.</span><span class="sxs-lookup"><span data-stu-id="f5922-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="f5922-145">Dans cet exemple, ces deux modes de sécurité sont tous deux désactivés afin d'illustrer le fonctionnement de la messagerie SRMP.</span><span class="sxs-lookup"><span data-stu-id="f5922-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="f5922-146">L'exécution de l'exemple retourne le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="f5922-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f5922-147">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f5922-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5922-148">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f5922-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f5922-149">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5922-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5922-150">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f5922-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
