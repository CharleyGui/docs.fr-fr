---
title: 'Modèles de conception : Publication/Abonnement par liste'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 5aaea5b0def544f8b3e963d71e269592b9b40784
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592344"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="697d4-102">Modèles de conception : Publication/Abonnement par liste</span><span class="sxs-lookup"><span data-stu-id="697d4-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="697d4-103">Cet exemple illustre le modèle de publication/abonnement basé sur une liste implémenté en tant que programme Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="697d4-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="697d4-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="697d4-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="697d4-105">Le modèle de conception de publication/abonnement basé sur une liste est décrit dans la publication Microsoft Patterns & Practices, [modèles d’intégration](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="697d4-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="697d4-106">Le modèle de publication/abonnement transmet des informations à une collection des destinataires qui se sont abonnés une rubrique d'informations.</span><span class="sxs-lookup"><span data-stu-id="697d4-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="697d4-107">Ce modèle gère une liste d'abonnés.</span><span class="sxs-lookup"><span data-stu-id="697d4-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="697d4-108">Lorsque des informations doivent être partagées, une copie est envoyée à chaque abonné de la liste.</span><span class="sxs-lookup"><span data-stu-id="697d4-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="697d4-109">Cet exemple illustre un modèle de publication/abonnement basé sur liste dynamique, où les clients peuvent s’abonner ou annuler leur abonnement aussi souvent que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="697d4-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="697d4-110">Il se compose d'un client, d'un service et d'un programme de source de données.</span><span class="sxs-lookup"><span data-stu-id="697d4-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="697d4-111">Il peut y avoir plusieurs clients et plusieurs programmes de source de données en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="697d4-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="697d4-112">Les clients s'abonnent au service, reçoivent des notifications et annulent leur abonnement.</span><span class="sxs-lookup"><span data-stu-id="697d4-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="697d4-113">Les programmes de source de données envoient des informations au service à partager avec tous les abonnés actuels.</span><span class="sxs-lookup"><span data-stu-id="697d4-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="697d4-114">Dans cet exemple, le client et la source de données sont des programmes de console (fichiers .exe) et le service est une bibliothèque (.dll) hébergée par les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="697d4-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="697d4-115">L'activité du client et de la source de données sont visibles sur le Bureau.</span><span class="sxs-lookup"><span data-stu-id="697d4-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="697d4-116">Le service utilise la communication duplex.</span><span class="sxs-lookup"><span data-stu-id="697d4-116">The service uses duplex communication.</span></span> <span data-ttu-id="697d4-117">Le contrat de service `ISampleContract` est associé à un contrat de rappel `ISampleClientCallback`.</span><span class="sxs-lookup"><span data-stu-id="697d4-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="697d4-118">Le service implémente les opérations d'abonnement et d'annulation d'abonnement que les clients utilisent pour rejoindre ou quitter la liste des abonnés.</span><span class="sxs-lookup"><span data-stu-id="697d4-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="697d4-119">Le service implémente également l'opération de service `PublishPriceChange` que le programme de source de données appelle pour fournir le service avec de nouvelles informations.</span><span class="sxs-lookup"><span data-stu-id="697d4-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="697d4-120">Le logiciel client implémente l'opération de service `PriceChange` que le service appelle pour prévenir tous les abonnés d'une modification de prix.</span><span class="sxs-lookup"><span data-stu-id="697d4-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="697d4-121">Le service utilise un événement .NET Framework comme mécanisme pour informer tous les abonnés à propos des nouvelles informations.</span><span class="sxs-lookup"><span data-stu-id="697d4-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="697d4-122">Lorsqu'un client rejoint le service en appelant l'opération d'abonnement, il fournit un gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="697d4-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="697d4-123">Lorsqu'un client part, il annule son gestionnaire d'événements de l'événement.</span><span class="sxs-lookup"><span data-stu-id="697d4-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="697d4-124">Lorsqu'une source de données appelle le service pour signaler une modification de prix, le service déclenche l'événement.</span><span class="sxs-lookup"><span data-stu-id="697d4-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="697d4-125">Il appelle chaque instance du service, une pour chaque client qui s'est abonné, et entraîne l'exécution de leurs gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="697d4-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="697d4-126">Chaque gestionnaire d'événements transmet les informations à son client via sa fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="697d4-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="697d4-127">Lorsque vous exécutez l'exemple, lancez plusieurs clients.</span><span class="sxs-lookup"><span data-stu-id="697d4-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="697d4-128">Les clients s'abonnent au service.</span><span class="sxs-lookup"><span data-stu-id="697d4-128">The clients subscribe to the service.</span></span> <span data-ttu-id="697d4-129">Exécutez ensuite le programme de source de données qui envoie des informations au service.</span><span class="sxs-lookup"><span data-stu-id="697d4-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="697d4-130">Le service transmet les informations à tous les abonnés.</span><span class="sxs-lookup"><span data-stu-id="697d4-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="697d4-131">Vous pouvez consulter l'activité sur chaque console cliente qui confirme que les informations ont été reçues.</span><span class="sxs-lookup"><span data-stu-id="697d4-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="697d4-132">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="697d4-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="697d4-133">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="697d4-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="697d4-134">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="697d4-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="697d4-135">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="697d4-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="697d4-136">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="697d4-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="697d4-137">Vérifiez que vous pouvez accéder au service à l’aide d’un navigateur en entrant l’adresse suivante : `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="697d4-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="697d4-138">Une page de confirmation doit s'afficher en réponse.</span><span class="sxs-lookup"><span data-stu-id="697d4-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="697d4-139">Exécutez client. exe à partir de \client\bin \\ , dans le dossier propre à la langue.</span><span class="sxs-lookup"><span data-stu-id="697d4-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="697d4-140">L'activité du client s'affiche dans sa fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="697d4-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="697d4-141">Lancez plusieurs clients.</span><span class="sxs-lookup"><span data-stu-id="697d4-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="697d4-142">Exécutez DataSource. exe à partir de \datasource\bin \\ , dans le dossier propre à la langue.</span><span class="sxs-lookup"><span data-stu-id="697d4-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="697d4-143">L'activité de source de données est affichée sur la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="697d4-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="697d4-144">Une fois que la source de données envoie des informations au service, elles doivent être transmises à chaque client.</span><span class="sxs-lookup"><span data-stu-id="697d4-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="697d4-145">Si le client, la source de données et les programmes de service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="697d4-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="697d4-146">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="697d4-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="697d4-147">Installez l'ordinateur de service:</span><span class="sxs-lookup"><span data-stu-id="697d4-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="697d4-148">Créez un répertoire virtuel nommé ServiceModelSamples sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="697d4-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="697d4-149">Le fichier de commandes Setupvroot. bat de la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) peut être utilisé pour créer le répertoire de disque et le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="697d4-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="697d4-150">Copiez les fichiers du programme de service depuis %SystemDrive%\Inetpub\wwwroot\servicemodelsamples vers le répertoire virtuel ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="697d4-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="697d4-151">Assurez-vous d'intégrer les fichiers au répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="697d4-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="697d4-152">Assurez-vous que le service est accessible depuis l'ordinateur du client en utilisant un navigateur.</span><span class="sxs-lookup"><span data-stu-id="697d4-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="697d4-153">Installez les ordinateurs clients :</span><span class="sxs-lookup"><span data-stu-id="697d4-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="697d4-154">Copiez les fichiers de programme client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="697d4-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="697d4-155">Dans chaque fichier de configuration client, modifiez l'adresse de la définition du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="697d4-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="697d4-156">Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="697d4-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="697d4-157">Installez l'ordinateur de source de données:</span><span class="sxs-lookup"><span data-stu-id="697d4-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="697d4-158">Copiez les fichiers du programme de source de données du dossier \datasource\bin\ (dans le dossier correspondant à votre langue) sur l’ordinateur de source de données.</span><span class="sxs-lookup"><span data-stu-id="697d4-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="697d4-159">Dans le fichier de configuration de la source de données, modifiez l'adresse de la définition du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="697d4-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="697d4-160">Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="697d4-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="697d4-161">Sur les ordinateurs clients, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="697d4-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="697d4-162">Sur l'ordinateur de source de données, lancez Datasource.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="697d4-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="697d4-163">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="697d4-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="697d4-164">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="697d4-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="697d4-165">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="697d4-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="697d4-166">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="697d4-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
