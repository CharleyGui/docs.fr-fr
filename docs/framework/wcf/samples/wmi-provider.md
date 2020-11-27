---
title: Fournisseur WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 9d654527c6897e071f914d4015ba9a225974b0f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263767"
---
# <a name="wmi-provider"></a><span data-ttu-id="3c944-102">Fournisseur WMI</span><span class="sxs-lookup"><span data-stu-id="3c944-102">WMI Provider</span></span>

<span data-ttu-id="3c944-103">Cet exemple montre comment collecter des données à partir de services Windows Communication Foundation (WCF) au moment de l’exécution à l’aide du fournisseur Windows Management Instrumentation (WMI) intégré à WCF.</span><span class="sxs-lookup"><span data-stu-id="3c944-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="3c944-104">Cet exemple montre également comment ajouter un objet WMI défini par l'utilisateur à un service.</span><span class="sxs-lookup"><span data-stu-id="3c944-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="3c944-105">L’exemple active le fournisseur WMI pour la [prise en main](getting-started-sample.md) et montre comment collecter des données à partir du `ICalculator` service au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3c944-105">The sample activates the WMI provider for the [Getting Started](getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="3c944-106">WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management).</span><span class="sxs-lookup"><span data-stu-id="3c944-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="3c944-107">Pour plus d’informations sur le kit de développement logiciel (SDK) WMI, consultez [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="3c944-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="3c944-108">WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.</span><span class="sxs-lookup"><span data-stu-id="3c944-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="3c944-109">WCF implémente un fournisseur WMI, un composant qui expose l’instrumentation au moment de l’exécution par le biais d’une interface compatible WBEM.</span><span class="sxs-lookup"><span data-stu-id="3c944-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="3c944-110">Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface.</span><span class="sxs-lookup"><span data-stu-id="3c944-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="3c944-111">WCF expose des attributs de services tels que les adresses, les liaisons, les comportements et les écouteurs.</span><span class="sxs-lookup"><span data-stu-id="3c944-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="3c944-112">Le fournisseur WMI intégré est activé dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="3c944-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="3c944-113">Cette opération s’effectue par le biais `wmiProviderEnabled` de l’attribut de [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) dans la [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) section, comme illustré dans l’exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="3c944-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3c944-114">Cette entrée de configuration expose une interface WMI.</span><span class="sxs-lookup"><span data-stu-id="3c944-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="3c944-115">Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.</span><span class="sxs-lookup"><span data-stu-id="3c944-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="3c944-116">Objet  WMI personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3c944-116">Custom WMI Object</span></span>  

 <span data-ttu-id="3c944-117">L'ajout d'objets WMI à un service permet de révéler des informations définies par l'utilisateur en même temps que les informations du fournisseur WMI intégré.</span><span class="sxs-lookup"><span data-stu-id="3c944-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="3c944-118">Cela s'effectue en publiant le schéma du service dans WMI en utilisant l'application Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="3c944-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="3c944-119">Des instructions plus détaillées sont disponibles dans les instructions d'installation à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="3c944-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="3c944-120">Accès aux informations WMI</span><span class="sxs-lookup"><span data-stu-id="3c944-120">Accessing WMI Information</span></span>  

<span data-ttu-id="3c944-121">Les données WMI sont accessibles de plusieurs façons différentes.</span><span class="sxs-lookup"><span data-stu-id="3c944-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="3c944-122">Microsoft fournit des API WMI pour les scripts, les applications Visual Basic, les applications C++ et les .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c944-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="3c944-123">Pour plus d’informations, consultez [utilisation de WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="3c944-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="3c944-124">Cet exemple utilise deux scripts Java : un pour énumérer des services qui s'exécutent sur l'ordinateur avec certaines de leurs propriétés et le second pour consulter les données WMI définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3c944-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="3c944-125">Le script ouvre une connexion au fournisseur WMI, analyse les données et affiche les données rassemblées.</span><span class="sxs-lookup"><span data-stu-id="3c944-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="3c944-126">Démarrez l’exemple pour créer une instance en cours d’exécution d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="3c944-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="3c944-127">Pendant que le service s'exécute, exécutez chaque script Java en utilisant la commande suivante dans l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="3c944-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="3c944-128">Le script accède à l'instrumentation contenue dans le service et produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c944-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="3c944-129">Ensuite, exécutez le deuxième script Java pour afficher les données WMI définies par l'utilisateur :</span><span class="sxs-lookup"><span data-stu-id="3c944-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="3c944-130">Le script accède à l'instrumentation définie par l'utilisateur contenue dans les services et produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c944-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="3c944-131">La sortie montre qu'un service unique s'exécute sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3c944-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="3c944-132">Le service expose un point de terminaison qui implémente le contrat `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="3c944-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="3c944-133">Les paramètres du comportement et de la liaison qui sont implémentés par le point de terminaison sont répertoriés comme la somme des éléments individuels de la pile de messagerie.</span><span class="sxs-lookup"><span data-stu-id="3c944-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="3c944-134">WMI n’est pas limité à l’exposition de l’instrumentation de gestion de l’infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="3c944-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="3c944-135">L'application peut exposer ses propres éléments de données spécifiques au domaine à travers le même mécanisme.</span><span class="sxs-lookup"><span data-stu-id="3c944-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="3c944-136">WMI est un mécanisme unifié pour l'inspection et le contrôle d'un service Web.</span><span class="sxs-lookup"><span data-stu-id="3c944-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3c944-137">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3c944-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3c944-138">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c944-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3c944-139">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c944-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3c944-140">Publiez le schéma de services dans WMI en exécutant InstallUtil.exe (l'emplacement par défaut pour Installutil.exe est « %WINDIR%\Microsoft.NET\Framework\v4.0.30319 ») sur le fichier service.dll dans le répertoire d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="3c944-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="3c944-141">Cette étape doit seulement être exécutée lorsque des modifications ont été apportées au fichier service.dll.</span><span class="sxs-lookup"><span data-stu-id="3c944-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="3c944-142">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c944-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3c944-143">Si vous avez installé WCF après l’installation de ASP.NET, vous devrez peut-être exécuter «% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows communication Foundation\servicemodelreg.exe "-r-x pour accorder au compte ASPNET l’autorisation de publier des objets WMI.</span><span class="sxs-lookup"><span data-stu-id="3c944-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="3c944-144">Consultez les données de l'exemple révélées par WMI en utilisant la commande `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="3c944-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3c944-145">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3c944-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3c944-146">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3c944-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3c944-147">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3c944-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c944-148">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3c944-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="3c944-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c944-149">See also</span></span>

- <span data-ttu-id="3c944-150">[Exemples d'analyse AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3c944-150">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
