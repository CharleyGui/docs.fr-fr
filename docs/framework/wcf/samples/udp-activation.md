---
title: UDP Activation
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143718"
---
# <a name="udp-activation"></a><span data-ttu-id="552ef-102">UDP Activation</span><span class="sxs-lookup"><span data-stu-id="552ef-102">UDP Activation</span></span>
<span data-ttu-id="552ef-103">Cet échantillon est basé sur l’échantillon [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="552ef-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="552ef-104">Il étend [l’échantillon Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) pour prendre en charge l’activation des processus à l’aide du Service d’activation des processus Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="552ef-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="552ef-105">L'exemple se compose de trois éléments majeurs :</span><span class="sxs-lookup"><span data-stu-id="552ef-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="552ef-106">Un activateur de protocole UDP, un processus autonome qui reçoit des messages UDP de la part des applications qui seront activées ;</span><span class="sxs-lookup"><span data-stu-id="552ef-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="552ef-107">Un client qui utilise le transport personnalisé d'UDP pour envoyer des messages ;</span><span class="sxs-lookup"><span data-stu-id="552ef-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="552ef-108">Un service (hébergé dans un processus de travail activé par WAS) qui reçoit des messages sur le transport UDP personnalisé.</span><span class="sxs-lookup"><span data-stu-id="552ef-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="552ef-109">Activateur de protocole UDP</span><span class="sxs-lookup"><span data-stu-id="552ef-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="552ef-110">L’activateur du protocole UDP est un pont entre le client WCF et le service WCF.</span><span class="sxs-lookup"><span data-stu-id="552ef-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="552ef-111">Il assure la communication des données à travers le protocole UDP au niveau de la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="552ef-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="552ef-112">Il possède deux fonctionnalités majeures :</span><span class="sxs-lookup"><span data-stu-id="552ef-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="552ef-113">L'adaptateur d'écouteur (LA) WAS, qui collabore avec WAS pour activer des processus en réponse à des messages entrants ;</span><span class="sxs-lookup"><span data-stu-id="552ef-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="552ef-114">L'écouteur de protocole UDP, qui accepte les messages UDP de la part des applications qui seront activées.</span><span class="sxs-lookup"><span data-stu-id="552ef-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="552ef-115">L'activateur doit s'exécuter comme un programme autonome sur l'ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="552ef-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="552ef-116">Normalement, les adaptateurs d'écouteur WAS (tels que NetTcpActivator et NetPipeActivator) sont implémentés dans les services Windows à durée d'exécution longue.</span><span class="sxs-lookup"><span data-stu-id="552ef-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="552ef-117">Toutefois, pour des questions de simplicité et de clarté, cet exemple implémente l'activateur de protocole en tant qu'application autonome.</span><span class="sxs-lookup"><span data-stu-id="552ef-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="552ef-118">Adaptateur d'écouteur WAS</span><span class="sxs-lookup"><span data-stu-id="552ef-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="552ef-119">L'adaptateur d'écouteur WAS pour UDP est implémenté dans la classe `UdpListenerAdapter`.</span><span class="sxs-lookup"><span data-stu-id="552ef-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="552ef-120">C'est le module qui interagit avec WAS pour effectuer l'activation d'application pour le protocole UDP.</span><span class="sxs-lookup"><span data-stu-id="552ef-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="552ef-121">Cela s'effectue en appelant les API Webhost suivantes :</span><span class="sxs-lookup"><span data-stu-id="552ef-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="552ef-122">Après avoir appelé `WebhostRegisterProtocol`, l'adaptateur d'écouteur reçoit le rappel `ApplicationCreated` de WAS pour toutes les applications enregistrées dans applicationHost.config (localisé dans %windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="552ef-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="552ef-123">Dans cet exemple, nous gérons uniquement les applications avec le protocole UDP (avec l'identificateur de protocole « net.udp ») activé.</span><span class="sxs-lookup"><span data-stu-id="552ef-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="552ef-124">D'autres implémentations peuvent gérer cela différemment si de telles implémentations répondent aux modifications de configuration dynamiques de l'application (par exemple, le passage d'application de l'état désactivé à l'état activé).</span><span class="sxs-lookup"><span data-stu-id="552ef-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="552ef-125">Lorsque le rappel `ConfigManagerInitializationCompleted` est reçu, il indique que WAS a terminé toutes les notifications pour l'initialisation du protocole.</span><span class="sxs-lookup"><span data-stu-id="552ef-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="552ef-126">À ce stade, l'adaptateur d'écouteur est prêt à traiter les demandes d'activation.</span><span class="sxs-lookup"><span data-stu-id="552ef-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="552ef-127">Lorsqu'une nouvelle demande arrive pour la première fois pour une application, l'adaptateur d'écouteur appelle `WebhostOpenListenerChannelInstance` dans WAS, qui démarre le processus de travail s'il n'est pas déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="552ef-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="552ef-128">Ensuite, les gestionnaires de protocoles sont chargés et la communication entre l'adaptateur d'écouteur et l'application virtuelle peut démarrer.</span><span class="sxs-lookup"><span data-stu-id="552ef-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="552ef-129">L’adaptateur d’écoute est enregistré dans le %SystemRoot%-System32-inetsrv-ApplicationHost.config dans la section `listenerAdapters` <> comme suit :</span><span class="sxs-lookup"><span data-stu-id="552ef-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="552ef-130">Écouteur de protocole</span><span class="sxs-lookup"><span data-stu-id="552ef-130">Protocol Listener</span></span>  
 <span data-ttu-id="552ef-131">L'écouteur de protocole d'UDP est un module interne à l'activateur de protocole qui écoute un point de terminaison UDP au nom de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="552ef-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="552ef-132">Il est implémenté dans la classe `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="552ef-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="552ef-133">Le point de terminaison est représenté comme un `IPEndpoint` pour lequel le numéro de port est extrait de la liaison du protocole pour le site.</span><span class="sxs-lookup"><span data-stu-id="552ef-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="552ef-134">Service de contrôle</span><span class="sxs-lookup"><span data-stu-id="552ef-134">Control Service</span></span>  
 <span data-ttu-id="552ef-135">Dans cet échantillon, nous utilisons WCF pour communiquer entre l’activateur et le processus de travailleur WAS.</span><span class="sxs-lookup"><span data-stu-id="552ef-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="552ef-136">Le service qui réside dans l'activateur est appelé le service de contrôle.</span><span class="sxs-lookup"><span data-stu-id="552ef-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="552ef-137">Gestionnaires de protocoles</span><span class="sxs-lookup"><span data-stu-id="552ef-137">Protocol Handlers</span></span>  
 <span data-ttu-id="552ef-138">Après que l'adaptateur d'écouteur a appelé `WebhostOpenListenerChannelInstance`, le gestionnaire de processus WAS démarre le processus de travail s'il n'est pas démarré.</span><span class="sxs-lookup"><span data-stu-id="552ef-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="552ef-139">Le gestionnaire d'application à l'intérieur du processus de travail charge ensuite le gestionnaire de protocole du processus (PPH) UDP avec la demande pour ce `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="552ef-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="552ef-140">Le PPH à `IAdphManager`tour de rôle appelle .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="552ef-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="552ef-141">pour démarrer l’UDP AppDomain Protocol Handler (ADPH).</span><span class="sxs-lookup"><span data-stu-id="552ef-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="552ef-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="552ef-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="552ef-143">Les informations sont enregistrées dans Web.config comme suit :</span><span class="sxs-lookup"><span data-stu-id="552ef-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="552ef-144">Installation spéciale pour cet exemple</span><span class="sxs-lookup"><span data-stu-id="552ef-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="552ef-145">Cet exemple ne peut être généré et exécuté que sur Windows Vista, Windows Server 2008 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="552ef-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="552ef-146">Pour exécuter l'exemple, vous devez d'abord configurer correctement tous les composants.</span><span class="sxs-lookup"><span data-stu-id="552ef-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="552ef-147">Procédez comme suit pour installer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="552ef-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="552ef-148">Pour installer cet exemple</span><span class="sxs-lookup"><span data-stu-id="552ef-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="552ef-149">Installez ASP.NET 4.0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="552ef-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="552ef-150">Générez le projet sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="552ef-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="552ef-151">Après la compilation, il effectue également les opérations suivantes dans la phase de post-génération :</span><span class="sxs-lookup"><span data-stu-id="552ef-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="552ef-152">Installe la liaison UDP avec le site « Site web par défaut » ;</span><span class="sxs-lookup"><span data-stu-id="552ef-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="552ef-153">Crée l’application virtuelle « ServiceModelSamples » qui doit pointer vers le chemin d’accès physique : « %SystemDrive%\inetpub\wwwroot\servicemodelsamples » ;</span><span class="sxs-lookup"><span data-stu-id="552ef-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="552ef-154">Il active également le protocole « net.udp » pour cette application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="552ef-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="552ef-155">Démarrez l'application d'interface utilisateur « WasNetActivator.exe ».</span><span class="sxs-lookup"><span data-stu-id="552ef-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="552ef-156">Cliquez sur l’onglet **Configuration,** vérifiez les cases à cocher suivantes, puis cliquez sur **Installer** pour les installer :</span><span class="sxs-lookup"><span data-stu-id="552ef-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="552ef-157">Adaptateur d'écouteur UDP</span><span class="sxs-lookup"><span data-stu-id="552ef-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="552ef-158">Gestionnaires de protocoles UDP</span><span class="sxs-lookup"><span data-stu-id="552ef-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="552ef-159">Cliquez sur **l’onglet d’activation** de l’application d’interface utilisateur "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="552ef-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="552ef-160">Cliquez sur le bouton **Démarrer** pour démarrer l’adaptateur de l’auditeur.</span><span class="sxs-lookup"><span data-stu-id="552ef-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="552ef-161">Vous êtes maintenant prêt à exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="552ef-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="552ef-162">Lorsque vous avez terminé avec cet exemple, vous devez exécuter Cleanup.bat pour supprimer la liaison net.udp du « Site Web par défaut ».</span><span class="sxs-lookup"><span data-stu-id="552ef-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="552ef-163">Exemple d’utilisation</span><span class="sxs-lookup"><span data-stu-id="552ef-163">Sample Usage</span></span>  
 <span data-ttu-id="552ef-164">Après la compilation, quatre binaires différents sont générés :</span><span class="sxs-lookup"><span data-stu-id="552ef-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="552ef-165">Client.exe : le code client.</span><span class="sxs-lookup"><span data-stu-id="552ef-165">Client.exe: The client code.</span></span> <span data-ttu-id="552ef-166">App.config est compilé dans le fichier de configuration client Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="552ef-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="552ef-167">UDPActivation.dll : la bibliothèque qui contient toutes les implémentations UDP majeures.</span><span class="sxs-lookup"><span data-stu-id="552ef-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="552ef-168">Service.dll : le code de service.</span><span class="sxs-lookup"><span data-stu-id="552ef-168">Service.dll: The service code.</span></span> <span data-ttu-id="552ef-169">Est copié dans le répertoire \bin de l'application virtuelle ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="552ef-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="552ef-170">Le fichier de service est Service.svc et le fichier de configuration est Web.config. Après compilation, ils sont copiés à l’endroit suivant : %SystemDrive%-Inetpub-wwwroot-ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="552ef-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="552ef-171">WasNetActivator : le programme de l'activateur UDP.</span><span class="sxs-lookup"><span data-stu-id="552ef-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="552ef-172">Assurez-vous que tous les éléments requis sont installés correctement.</span><span class="sxs-lookup"><span data-stu-id="552ef-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="552ef-173">Les étapes suivantes indiquent comment exécuter l'exemple :</span><span class="sxs-lookup"><span data-stu-id="552ef-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="552ef-174">Assurez-vous que les services Windows suivants ont été démarrés :</span><span class="sxs-lookup"><span data-stu-id="552ef-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="552ef-175">service d'activation des processus Windows (WAS) ;</span><span class="sxs-lookup"><span data-stu-id="552ef-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="552ef-176">Services Internet (IIS) : W3SVC.</span><span class="sxs-lookup"><span data-stu-id="552ef-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="552ef-177">Puis démarrez l'activateur, WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="552ef-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="552ef-178">Sous **l’onglet Activation,** le seul protocole, **UDP**, est sélectionné dans la liste des baisses.</span><span class="sxs-lookup"><span data-stu-id="552ef-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="552ef-179">Cliquez sur le bouton **Démarrer** pour démarrer l’activateur.</span><span class="sxs-lookup"><span data-stu-id="552ef-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="552ef-180">Une fois l'activateur démarré, vous pouvez exécuter le code client en exécutant Client.exe à partir d'une fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="552ef-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="552ef-181">La sortie peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="552ef-181">The following is the sample output:</span></span>  
  
    ```console  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="552ef-182">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="552ef-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="552ef-183">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="552ef-183">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="552ef-184">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="552ef-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="552ef-185">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="552ef-185">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
