---
title: Local Channel
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714883"
---
# <a name="local-channel"></a><span data-ttu-id="5e2bd-102">Local Channel</span><span class="sxs-lookup"><span data-stu-id="5e2bd-102">Local Channel</span></span>
<span data-ttu-id="5e2bd-103">Le canal local est un canal de transport Windows Communication Foundation (WCF) qui est utilisé pour la communication dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="5e2bd-104">Cela peut être utile pour les scénarios où le client et le service s’exécutent dans le même domaine d’application et où la charge liée à la pile de canaux WCF classique (sérialisation et désérialisation de messages) doit être évitée.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5e2bd-105">Montre</span><span class="sxs-lookup"><span data-stu-id="5e2bd-105">Demonstrates</span></span>  
 <span data-ttu-id="5e2bd-106">Local Channel</span><span class="sxs-lookup"><span data-stu-id="5e2bd-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5e2bd-107">Discussion</span><span class="sxs-lookup"><span data-stu-id="5e2bd-107">Discussion</span></span>  
 <span data-ttu-id="5e2bd-108">Cet exemple est composé de deux fichiers projet :</span><span class="sxs-lookup"><span data-stu-id="5e2bd-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="5e2bd-109">**LocalChannel**: représentation par programmation du canal local dans le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="5e2bd-110">Dans ce projet, le composant expéditeur place le message dans une file d'attente en mémoire et le composant récepteur retire le message de la file d'attente pour le recevoir.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="5e2bd-111">**ClientAndService**: ce projet héberge un service dans une application console, puis exécute un client pour appeler le service à partir du même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="5e2bd-112">Le canal local est conçu pour ignorer la pile de canaux et le processus de sérialisation afin de gagner en vitesse.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="5e2bd-113">Le canal de transport local est implémenté à l'aide d'une file d'attente pour transporter les appels de service du client au service et pour retourner la valeur au client.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="5e2bd-114">Au lieu de sérialiser des paramètres et des valeurs de retour, l'exemple copie les objets.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e2bd-115">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5e2bd-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5e2bd-116">Générez et exécutez la solution LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="5e2bd-117">L'hôte du service démarre et le client appelle le service en utilisant le canal local.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="5e2bd-118">Une fenêtre de console apparaît pour afficher le résultat de l'appel de service.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5e2bd-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e2bd-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5e2bd-121">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e2bd-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e2bd-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5e2bd-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
