---
title: Custom Message Interceptor
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 530c626a1f134190bb90fcee3a4e3bbba91d9516
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878306"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="ec622-102">Custom Message Interceptor</span><span class="sxs-lookup"><span data-stu-id="ec622-102">Custom Message Interceptor</span></span>
<span data-ttu-id="ec622-103">Cet exemple montre l'utilisation du modèle d'extensibilité des canaux.</span><span class="sxs-lookup"><span data-stu-id="ec622-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="ec622-104">Indique en particulier comment implémenter un élément de liaison personnalisé qui crée des fabrications de canaux et des écouteurs de canal pour intercepter tous les messages entrants et sortants à un point particulier dans la pile d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ec622-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="ec622-105">L'exemple inclut également un client et serveur qui montrent l'utilisation de ces fabrications personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ec622-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="ec622-106">Dans cet exemple, le client et le service sont tous deux des programmes de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="ec622-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="ec622-107">Le client et le service utilisent une bibliothèque commune (.dll) qui contient l’élément de liaison personnalisé et ses objets d’exécution associés.</span><span class="sxs-lookup"><span data-stu-id="ec622-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec622-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ec622-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ec622-109">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ec622-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ec622-110">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ec622-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ec622-111">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="ec622-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ec622-112">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ec622-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="ec622-113">L’exemple décrit la procédure recommandée pour la création d’un canal superposé personnalisé dans Windows Communication Foundation (WCF), en utilisant l’infrastructure de canal et en suivant les bonnes pratiques WCF.</span><span class="sxs-lookup"><span data-stu-id="ec622-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="ec622-114">Les étapes de la création d'un canal superposé personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec622-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="ec622-115">Déterminez les formes de canal que votre fabrication et écouteur de canal prendra en charge.</span><span class="sxs-lookup"><span data-stu-id="ec622-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="ec622-116">Créez une fabrication et un écouteur de canal qui prennent en charge vos formes de canal.</span><span class="sxs-lookup"><span data-stu-id="ec622-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="ec622-117">Ajoutez un élément de liaison qui ajoute le canal superposé personnalisé à une pile de canaux.</span><span class="sxs-lookup"><span data-stu-id="ec622-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="ec622-118">Ajoutez une section d’extension d’élément de liaison afin d’exposer le nouvel élément de liaison au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="ec622-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="ec622-119">Formes de canal</span><span class="sxs-lookup"><span data-stu-id="ec622-119">Channel Shapes</span></span>  
 <span data-ttu-id="ec622-120">La première étape de l'écriture d'un canal superposé personnalisé consiste à déterminer les formes requises pour le canal.</span><span class="sxs-lookup"><span data-stu-id="ec622-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="ec622-121">Pour notre inspecteur de message, nous prenons en charge les formes qui la couche ci-dessous prend en charge (par exemple, si la couche ci-dessous peux générer <xref:System.ServiceModel.Channels.IOutputChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, nous exposons alors également <xref:System.ServiceModel.Channels.IOutputChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="ec622-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="ec622-122">Fabrication de canal et d'écouteur</span><span class="sxs-lookup"><span data-stu-id="ec622-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="ec622-123">L'étape suivante de l'écriture d'un canal superposé personnalisé consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients et de <xref:System.ServiceModel.Channels.IChannelListener> pour les canaux de service.</span><span class="sxs-lookup"><span data-stu-id="ec622-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="ec622-124">Ces classes prennent une fabrication et un écouteur internes, puis leur délèguent tout les appels à l'exception de `OnCreateChannel` et `OnAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="ec622-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="ec622-125">Ajout d'un élément de liaison</span><span class="sxs-lookup"><span data-stu-id="ec622-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="ec622-126">l’exemple définit un élément de liaison personnalisé : `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="ec622-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="ec622-127">`InterceptingBindingElement` prend un `ChannelMessageInterceptor` en tant qu’entrée et utilise ce `ChannelMessageInterceptor` pour manipuler les messages qui transitent par elle.</span><span class="sxs-lookup"><span data-stu-id="ec622-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="ec622-128">C'est la seule classe qui doit être publique.</span><span class="sxs-lookup"><span data-stu-id="ec622-128">This is the only class that must be public.</span></span> <span data-ttu-id="ec622-129">La fabrication, l'écouteur et les canaux peuvent tous être des implémentations internes des interfaces d'exécution publiques.</span><span class="sxs-lookup"><span data-stu-id="ec622-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="ec622-130">Ajout de la prise en charge de la configuration</span><span class="sxs-lookup"><span data-stu-id="ec622-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="ec622-131">Pour s'intégrer avec la configuration de liaison, la bibliothèque définit un gestionnaire de section de configuration comme section d'extension d'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="ec622-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="ec622-132">Les fichiers de configuration du client et du serveur doivent enregistrer l'extension d'élément de liaison avec le système de configuration.</span><span class="sxs-lookup"><span data-stu-id="ec622-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="ec622-133">Les implémenteurs qui souhaitent exposer leur élément de liaison au système de configuration peuvent dériver de cette classe.</span><span class="sxs-lookup"><span data-stu-id="ec622-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="ec622-134">Ajout d'une stratégie</span><span class="sxs-lookup"><span data-stu-id="ec622-134">Adding Policy</span></span>  
 <span data-ttu-id="ec622-135">Pour s'intégrer avec notre système de stratégie, `InterceptingBindingElement` implémente IPolicyExportExtension pour signaler que nous devons participer à la génération de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ec622-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="ec622-136">Pour prendre en charge l'importation de la stratégie sur un client généré, l'utilisateur peut enregistrer une classe dérivée de `InterceptingBindingElementImporter` et substituer `CreateMessageInterceptor`() pour générer leur classe `ChannelMessageInterceptor` activée par stratégie.</span><span class="sxs-lookup"><span data-stu-id="ec622-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="ec622-137">Exemple : Inspecteur de message</span><span class="sxs-lookup"><span data-stu-id="ec622-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="ec622-138">L'exemple comporte un exemple d'implémentation de `ChannelMessageInspector` qui supprime des messages.</span><span class="sxs-lookup"><span data-stu-id="ec622-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="ec622-139">Vous pouvez y accéder à partir de la configuration comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec622-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ec622-140">Le client et le serveur utilisent cette section de configuration récemment créée afin dans d'insérer les fabrications personnalisées au niveau le plus bas de leurs piles d'exécution de canaux (au-dessus du niveau du transport).</span><span class="sxs-lookup"><span data-stu-id="ec622-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="ec622-141">Le client utilise la bibliothèque `MessageInterceptor` pour ajouter un en-tête personnalisé aux messages portant un numéro pair.</span><span class="sxs-lookup"><span data-stu-id="ec622-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="ec622-142">Le service utilise en revanche la bibliothèque `MessageInterceptor` pour supprimer les messages qui n'ont pas cet en-tête spécifique.</span><span class="sxs-lookup"><span data-stu-id="ec622-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="ec622-143">La sortie du client suivante doit s'afficher après avoir exécuté le service puis le client.</span><span class="sxs-lookup"><span data-stu-id="ec622-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="ec622-144">Le client signale 10 vitesses de vent différentes au service, mais n’en référence que la moitié avec l’en-tête spécifique.</span><span class="sxs-lookup"><span data-stu-id="ec622-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="ec622-145">La sortie suivante doit s'afficher sur le service :</span><span class="sxs-lookup"><span data-stu-id="ec622-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ec622-146">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ec622-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ec622-147">Installer ASP.NET 4.0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="ec622-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ec622-148">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ec622-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ec622-149">Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ec622-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ec622-150">Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ec622-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="ec622-151">Exécutez d'abord Service.exe, puis Client.exe. Examinez ensuite la sortie dans les deux fenêtres de console.</span><span class="sxs-lookup"><span data-stu-id="ec622-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
