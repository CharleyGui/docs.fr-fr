---
title: Custom Service Host
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 271233015739024428a7a29815f66278c9d7aa04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789927"
---
# <a name="custom-service-host"></a><span data-ttu-id="490ce-102">Custom Service Host</span><span class="sxs-lookup"><span data-stu-id="490ce-102">Custom Service Host</span></span>
<span data-ttu-id="490ce-103">Cet exemple montre comment utiliser un dérivé personnalisé de la classe <xref:System.ServiceModel.ServiceHost> pour altérer le comportement d'exécution d'un service.</span><span class="sxs-lookup"><span data-stu-id="490ce-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="490ce-104">Cette approche propose une alternative réutilisable à la configuration d'un grand nombre de services de manière commune.</span><span class="sxs-lookup"><span data-stu-id="490ce-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="490ce-105">L'exemple montre également comment utiliser la classe <xref:System.ServiceModel.Activation.ServiceHostFactory> pour utiliser un ServiceHost personnalisé dans l'environnement d'hébergement des services IIS (Internet Information Services) ou WAS (Windows Process Activation Service).</span><span class="sxs-lookup"><span data-stu-id="490ce-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="490ce-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="490ce-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="490ce-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="490ce-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="490ce-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="490ce-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="490ce-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="490ce-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="490ce-110">À propos du scénario</span><span class="sxs-lookup"><span data-stu-id="490ce-110">About the scenario</span></span>
 <span data-ttu-id="490ce-111">Pour empêcher la divulgation non intentionnelle de métadonnées de service potentiellement sensibles, la configuration par défaut pour les services Windows Communication Foundation (WCF) désactive la publication de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="490ce-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="490ce-112">Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="490ce-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="490ce-113">L'activation de la publication de métadonnées pour un grand nombre de services implique l'ajout des mêmes éléments de configuration à chaque service, ce qui entraîne une grande quantité d'informations de configuration qui sont essentiellement les mêmes.</span><span class="sxs-lookup"><span data-stu-id="490ce-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="490ce-114">Comme alternative à la configuration distincte de chaque service, vous pouvez écrire le code impératif qui active la publication des métadonnées une fois, puis réutiliser ce code sur plusieurs services différents.</span><span class="sxs-lookup"><span data-stu-id="490ce-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="490ce-115">Pour ce faire, il faut créer une classe nouvelle qui dérive de <xref:System.ServiceModel.ServiceHost> et remplace la méthode `ApplyConfiguration`() pour ajouter impérativement le comportement de publication de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="490ce-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="490ce-116">Pour plus de clarté, cet exemple montre comment créer un point de terminaison de publication de métadonnées non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="490ce-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="490ce-117">De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="490ce-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="490ce-118">Implémentation d'un ServiceHost personnalisé</span><span class="sxs-lookup"><span data-stu-id="490ce-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="490ce-119">La classe <xref:System.ServiceModel.ServiceHost> expose plusieurs méthodes virtuelles utiles que les héritiers peuvent substituer pour modifier le comportement à l'exécution d'un service.</span><span class="sxs-lookup"><span data-stu-id="490ce-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="490ce-120">Par exemple, la méthode `ApplyConfiguration`() lit des informations de configuration du service du magasin de configurations et modifie en conséquence <xref:System.ServiceModel.Description.ServiceDescription> de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="490ce-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="490ce-121">L'implémentation par défaut lit la configuration à partir du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="490ce-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="490ce-122">Les implémentations personnalisées peuvent remplacer `ApplyConfiguration`() pour modifier le <xref:System.ServiceModel.Description.ServiceDescription> à l'aide du code impératif ou remplacer totalement le magasin de configurations par défaut.</span><span class="sxs-lookup"><span data-stu-id="490ce-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="490ce-123">Par exemple, pour lire la configuration du point de terminaison d'un service à partir d'une base de données au lieu du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="490ce-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="490ce-124">Dans cet exemple, nous souhaitons générer un ServiceHost personnalisé qui ajoute ServiceMetadataBehavior, (lequel active l'édition de métadonnées) même si ce comportement n'est pas ajouté explicitement dans le fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="490ce-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="490ce-125">Pour ce faire, nous créons une classe héritée de <xref:System.ServiceModel.ServiceHost> et qui remplace `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="490ce-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="490ce-126">Parce que nous ne souhaitons pas ignorer de configuration ayant été fournie dans le fichier de configuration de l'application, la première chose que notre substitution de `ApplyConfiguration`() fait est d'appeler l'implémentation de base.</span><span class="sxs-lookup"><span data-stu-id="490ce-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="490ce-127">Une fois cette méthode terminée, nous pouvons ajouter impérativement le <xref:System.ServiceModel.Description.ServiceMetadataBehavior> à la description à l'aide du code impératif suivant.</span><span class="sxs-lookup"><span data-stu-id="490ce-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="490ce-128">La dernière chose que notre substitution `ApplyConfiguration`() doit faire est ajouter le point de terminaison de métadonnées par défaut.</span><span class="sxs-lookup"><span data-stu-id="490ce-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="490ce-129">Par convention, un point de terminaison de métadonnées est créé pour chaque URI dans la collection BaseAddresses de l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="490ce-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="490ce-130">Utilisation d'un ServiceHost personnalisé dans l'auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="490ce-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="490ce-131">Maintenant que nous avons terminé notre implémentation ServiceHost personnalisée, nous pouvons l'utiliser pour ajouter des métadonnées qui publient le comportement sur tout service en hébergeant ce service dans une instance de notre `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="490ce-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="490ce-132">Le code suivant indique comment l'utiliser dans le scénario d'auto-hébergement.</span><span class="sxs-lookup"><span data-stu-id="490ce-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="490ce-133">Notre hôte personnalisé lit encore la configuration du point de terminaison du service à partir du fichier de configuration de l'application, comme si nous avions utilisé la classe <xref:System.ServiceModel.ServiceHost> par défaut pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="490ce-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="490ce-134">Toutefois, parce que nous avons ajouté la logique pour activer la publication des métadonnées dans notre hôte personnalisé, nous ne devons plus activer explicitement le comportement de publication des métadonnées dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="490ce-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="490ce-135">Cette approche a un avantage distinct lorsque vous générez une application qui contient plusieurs services et vous souhaitez activer la publication de métadonnées sur chacun d'eux sans écrire les mêmes éléments de configuration plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="490ce-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="490ce-136">Utilisation d'un ServiceHost personnalisé dans IIS ou WAS</span><span class="sxs-lookup"><span data-stu-id="490ce-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="490ce-137">L'utilisation d'un hôte de service personnalisé dans les scénarios d'auto-hébergement est simple, car c'est votre code d'application qui est finalement chargé de créer et d'ouvrir l'instance hôte du service.</span><span class="sxs-lookup"><span data-stu-id="490ce-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="490ce-138">Toutefois, dans l’environnement d’hébergement IIS ou WAS, l’infrastructure WCF instancie dynamiquement l’hôte de votre service en réponse à des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="490ce-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="490ce-139">Les hôtes de service personnalisés peuvent également être utilisés dans cet environnement d'hébergement, mais ils ont besoin de code supplémentaire dans le formulaire d'un ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="490ce-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="490ce-140">Le code suivant affiche une dérivée de <xref:System.ServiceModel.Activation.ServiceHostFactory> qui retourne des instances de notre `SelfDescribingServiceHost` personnalisé.</span><span class="sxs-lookup"><span data-stu-id="490ce-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="490ce-141">Comme vous pouvez voir, l'implémentation d'un ServiceHostFactory personnalisé est très simple.</span><span class="sxs-lookup"><span data-stu-id="490ce-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="490ce-142">Toute la logique personnalisée réside dans l'implémentation ServiceHost ; la fabrique retourne une instance de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="490ce-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="490ce-143">Pour utiliser une fabrique personnalisée avec une implémentation de service, nous devons ajouter des métadonnées supplémentaires au fichier .svc du service.</span><span class="sxs-lookup"><span data-stu-id="490ce-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="490ce-144">Ici, nous avons ajouté un attribut `Factory` supplémentaire à la directive `@ServiceHost` et avons transmis le nom de type CLR de notre fabrique personnalisée comme valeur de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="490ce-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="490ce-145">Quand IIS ou WAS reçoit un message pour ce service, l’infrastructure d’hébergement WCF crée d’abord une instance de ServiceHostFactory, puis instancie l’hôte de service lui-même en appelant `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="490ce-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="490ce-146">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="490ce-146">Running the sample</span></span>  
 <span data-ttu-id="490ce-147">Bien que cet exemple fournisse une implémentation entièrement fonctionnelle d'un client et d'un service, l'intérêt de cet exemple est qu'il montre comment modifier le comportement à l'exécution d'un service au moyen d'un hôte personnalisé. Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="490ce-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="490ce-148">Observer l’effet de l’hôte personnalisé</span><span class="sxs-lookup"><span data-stu-id="490ce-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="490ce-149">Ouvrez le fichier Web. config du service et Notez qu’il n’existe aucune configuration activant explicitement les métadonnées pour le service.</span><span class="sxs-lookup"><span data-stu-id="490ce-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="490ce-150">Ouvrez le fichier. svc du service et observez que sa directive @ServiceHost contient un attribut Factory qui spécifie le nom d’un ServiceHostFactory personnalisé.</span><span class="sxs-lookup"><span data-stu-id="490ce-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="490ce-151">Configurer, générer et exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="490ce-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="490ce-152">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="490ce-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="490ce-153">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="490ce-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="490ce-154">Une fois la solution générée, exécutez Setup. bat pour configurer l’application ServiceModelSamples dans IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="490ce-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="490ce-155">Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’application IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="490ce-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="490ce-156">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="490ce-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="490ce-157">Pour supprimer l’application IIS 7,0, exécutez *Cleanup. bat*.</span><span class="sxs-lookup"><span data-stu-id="490ce-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="490ce-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="490ce-158">See also</span></span>

- [<span data-ttu-id="490ce-159">How to: Host a WCF Service in IIS (Comment : héberger un service WCF dans IIS)</span><span class="sxs-lookup"><span data-stu-id="490ce-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
