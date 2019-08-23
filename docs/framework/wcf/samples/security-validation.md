---
title: Security Validation
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 5d37c6a46f807d5f1634348044e04bbc60f7eb98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965462"
---
# <a name="security-validation"></a><span data-ttu-id="6d081-102">Security Validation</span><span class="sxs-lookup"><span data-stu-id="6d081-102">Security Validation</span></span>
<span data-ttu-id="6d081-103">Cet exemple montre comment utiliser un comportement personnalisé pour valider des services sur un ordinateur afin de garantir qu'ils répondent à des critères spécifiques.</span><span class="sxs-lookup"><span data-stu-id="6d081-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="6d081-104">Dans cet exemple, les services sont validés par le comportement personnalisé en analysant chaque point de terminaison sur le service et en vérifiant s'ils contiennent des éléments de liaison sécurisés.</span><span class="sxs-lookup"><span data-stu-id="6d081-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="6d081-105">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6d081-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d081-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6d081-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="6d081-107">Comportement personnalisé de validation de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="6d081-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="6d081-108">En ajoutant le code utilisateur à la méthode `Validate` contenue dans l'interface <xref:System.ServiceModel.Description.IServiceBehavior>, le comportement personnalisé peut être attribué à un service ou un point de terminaison pour effectuer des actions définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d081-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="6d081-109">Le code suivant est utilisé pour parcourir chaque point de terminaison contenu dans un service et rechercher des liaisons sécurisées dans leurs collections de liaisons.</span><span class="sxs-lookup"><span data-stu-id="6d081-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their    
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="6d081-110">L’ajout du code suivant au fichier Web.config ajoute l’extension de comportement `serviceValidate` au service à reconnaître.</span><span class="sxs-lookup"><span data-stu-id="6d081-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="6d081-111">Une fois l’extension de comportement ajoutée au service, il est possible d’ajouter le comportement `endpointValidate` à la liste de comportements dans le fichier Web.config et donc, au service.</span><span class="sxs-lookup"><span data-stu-id="6d081-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="6d081-112">Les comportements et leurs extensions ajoutés au fichier Web.config appliquent le comportement aux services individuels, tandis qu’en cas d’ajout au fichier Machine.config, ils appliquent le comportement à chaque service actif sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d081-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d081-113">Lors de l'ajout du comportement à tous les services, il est recommandé de sauvegarder le fichier Machine.config avant d'apporter toute modification.</span><span class="sxs-lookup"><span data-stu-id="6d081-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="6d081-114">Exécutez maintenant le client fourni dans le répertoire client\bin de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="6d081-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="6d081-115">Une exception s’est produite avec le message suivant: «Le service demandé « http://localhost/servicemodelsamples/service.svc » n’a pas pu être activé».</span><span class="sxs-lookup"><span data-stu-id="6d081-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="6d081-116">Cette exception est attendue parce qu'un point de terminaison est considéré comme non sécurisé par le comportement de validation de point de terminaison et empêche le démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="6d081-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="6d081-117">Le comportement lève également une exception interne qui décrit quel point de terminaison n'est pas sécurisé et écrit un message à l'observateur d'événements du système sous la source « System.ServiceModel 4.0.0.0 » et la catégorie « WebHost ».</span><span class="sxs-lookup"><span data-stu-id="6d081-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="6d081-118">Il est également possible d'activer le suivi sur le service dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="6d081-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="6d081-119">Cela permet à l'utilisateur de consulter les exceptions levées par le comportement de validation de point de terminaison en ouvrant les suivis du service à l'aide de l'outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="6d081-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="6d081-120">Pour consulter les messages d'exception de validation non réussie d'un point de terminaison dans l'observateur d'événements</span><span class="sxs-lookup"><span data-stu-id="6d081-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="6d081-121">Cliquez sur le menu **Démarrer** et sélectionnez **exécuter...** .</span><span class="sxs-lookup"><span data-stu-id="6d081-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="6d081-122">Tapez `eventvwr` puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6d081-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="6d081-123">Dans la fenêtre observateur d’événements, cliquez sur **application**.</span><span class="sxs-lookup"><span data-stu-id="6d081-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="6d081-124">Double-cliquez sur l’événement «System. ServiceModel 4.0.0.0» ajouté récemment sous la catégorie «WebHost» dans la fenêtre d' **application** pour afficher les messages de point de terminaison non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="6d081-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6d081-125">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6d081-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6d081-126">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d081-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6d081-127">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d081-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6d081-128">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d081-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d081-129">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d081-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6d081-130">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6d081-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d081-131">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="6d081-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d081-132">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6d081-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="6d081-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d081-133">See also</span></span>

- [<span data-ttu-id="6d081-134">Exemples de surveillance AppFabric</span><span class="sxs-lookup"><span data-stu-id="6d081-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
