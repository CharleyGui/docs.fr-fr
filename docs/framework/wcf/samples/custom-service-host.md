---
title: Custom Service Host
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 8302c3c829883da954d200526ca641eb4c169f98
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052024"
---
# <a name="custom-service-host"></a>Custom Service Host
Cet exemple montre comment utiliser un dérivé personnalisé de la classe <xref:System.ServiceModel.ServiceHost> pour altérer le comportement d'exécution d'un service. Cette approche propose une alternative réutilisable à la configuration d'un grand nombre de services de manière commune. L'exemple montre également comment utiliser la classe <xref:System.ServiceModel.Activation.ServiceHostFactory> pour utiliser un ServiceHost personnalisé dans l'environnement d'hébergement des services IIS (Internet Information Services) ou WAS (Windows Process Activation Service).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>À propos du scénario
 Pour empêcher la divulgation non intentionnelle de métadonnées de service potentiellement sensibles, la configuration par défaut pour les services Windows Communication Foundation (WCF) désactive la publication de métadonnées. Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser un outil d’importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, sauf si le comportement de publication des métadonnées du service est explicitement activé dans la configuration.  
  
 L'activation de la publication de métadonnées pour un grand nombre de services implique l'ajout des mêmes éléments de configuration à chaque service, ce qui entraîne une grande quantité d'informations de configuration qui sont essentiellement les mêmes. Comme alternative à la configuration distincte de chaque service, vous pouvez écrire le code impératif qui active la publication des métadonnées une fois, puis réutiliser ce code sur plusieurs services différents. Pour ce faire, il faut créer une classe nouvelle qui dérive de <xref:System.ServiceModel.ServiceHost> et remplace la méthode `ApplyConfiguration`() pour ajouter impérativement le comportement de publication de métadonnées.  
  
> [!IMPORTANT]
> Pour plus de clarté, cet exemple montre comment créer un point de terminaison de publication de métadonnées non sécurisé. De tels points de terminaison sont potentiellement disponibles pour les consommateurs anonymes non authentifiés et doivent être pris en compte avant de déployer de tels points de terminaison pour s’assurer que la divulgation publique des métadonnées d’un service est appropriée.  
  
## <a name="implementing-a-custom-servicehost"></a>Implémentation d'un ServiceHost personnalisé
 La classe <xref:System.ServiceModel.ServiceHost> expose plusieurs méthodes virtuelles utiles que les héritiers peuvent substituer pour modifier le comportement à l'exécution d'un service. Par exemple, la méthode `ApplyConfiguration`() lit des informations de configuration du service du magasin de configurations et modifie en conséquence <xref:System.ServiceModel.Description.ServiceDescription> de l'hôte. L’implémentation par défaut lit la configuration à partir du fichier de configuration de l’application. Les implémentations personnalisées peuvent remplacer `ApplyConfiguration`() pour modifier le <xref:System.ServiceModel.Description.ServiceDescription> à l'aide du code impératif ou remplacer totalement le magasin de configurations par défaut. Par exemple, pour lire la configuration d’un point de terminaison d’un service à partir d’une base de données au lieu du fichier de configuration de l’application.  
  
 Dans cet exemple, nous souhaitons créer un ServiceHost personnalisé qui ajoute ServiceMetadataBehavior (qui active la publication de métadonnées), même si ce comportement n’est pas explicitement ajouté dans le fichier de configuration du service. Pour ce faire, créez une nouvelle classe qui hérite de <xref:System.ServiceModel.ServiceHost> et substitue `ApplyConfiguration` ().  
  
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
  
 Étant donné que nous ne souhaitons pas ignorer les configurations qui ont été fournies dans le fichier de configuration de l’application, la première chose que notre substitution de `ApplyConfiguration` () appelle l’implémentation de base. Une fois cette méthode terminée, nous pouvons ajouter impérativement le <xref:System.ServiceModel.Description.ServiceMetadataBehavior> à la description à l'aide du code impératif suivant.  
  
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
  
 La dernière chose que notre substitution `ApplyConfiguration`() doit faire est ajouter le point de terminaison de métadonnées par défaut. Par Convention, un point de terminaison de métadonnées est créé pour chaque URI dans la collection BaseAddresses de l’hôte de service.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Utilisation d'un ServiceHost personnalisé dans l'auto-hébergement  
 Maintenant que nous avons terminé notre implémentation ServiceHost personnalisée, nous pouvons l'utiliser pour ajouter des métadonnées qui publient le comportement sur tout service en hébergeant ce service dans une instance de notre `SelfDescribingServiceHost`. Le code suivant indique comment l'utiliser dans le scénario d'auto-hébergement.  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Notre hôte personnalisé lit toujours la configuration du point de terminaison du service à partir du fichier de configuration de l’application, comme si nous avions utilisé la classe par défaut <xref:System.ServiceModel.ServiceHost> pour héberger le service. Toutefois, parce que nous avons ajouté la logique pour activer la publication des métadonnées dans notre hôte personnalisé, nous ne devons plus activer explicitement le comportement de publication des métadonnées dans la configuration. Cette approche a un avantage distinct lorsque vous générez une application qui contient plusieurs services et vous souhaitez activer la publication de métadonnées sur chacun d'eux sans écrire les mêmes éléments de configuration plusieurs fois.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Utilisation d'un ServiceHost personnalisé dans IIS ou WAS  
 L'utilisation d'un hôte de service personnalisé dans les scénarios d'auto-hébergement est simple, car c'est votre code d'application qui est finalement chargé de créer et d'ouvrir l'instance hôte du service. Toutefois, dans l’environnement d’hébergement IIS ou WAS, l’infrastructure WCF instancie dynamiquement l’hôte de votre service en réponse à des messages entrants. Les hôtes de service personnalisés peuvent également être utilisés dans cet environnement d'hébergement, mais ils ont besoin de code supplémentaire dans le formulaire d'un ServiceHostFactory. Le code suivant affiche une dérivée de <xref:System.ServiceModel.Activation.ServiceHostFactory> qui retourne des instances de notre `SelfDescribingServiceHost` personnalisé.  
  
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
  
 Comme vous pouvez le voir, l’implémentation d’un ServiceHostFactory personnalisé est simple. Toute la logique personnalisée réside dans l'implémentation ServiceHost ; la fabrique retourne une instance de la classe dérivée.  
  
 Pour utiliser une fabrique personnalisée avec une implémentation de service, nous devons ajouter des métadonnées supplémentaires au fichier. svc du service.  
  
```aspx-csharp
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 Ici, nous avons ajouté un `Factory` attribut supplémentaire à la `@ServiceHost` directive et passé le nom de type CLR de notre fabrique personnalisée comme valeur de l’attribut. Quand IIS ou WAS reçoit un message pour ce service, l’infrastructure d’hébergement WCF crée d’abord une instance de ServiceHostFactory, puis instancie l’hôte de service lui-même en appelant `ServiceHostFactory.CreateServiceHost()` .  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 Bien que cet exemple fournisse une implémentation entièrement fonctionnelle du client et du service, le point de l’exemple est d’illustrer comment modifier le comportement d’exécution d’un service au moyen d’un hôte personnalisé. procédez comme suit :  
  
### <a name="observe-the-effect-of-the-custom-host"></a>Observer l’effet de l’hôte personnalisé
  
1. Ouvrez le fichier de Web.config du service et Notez qu’il n’existe aucune configuration activant explicitement les métadonnées pour le service.  
  
2. Ouvrez le fichier. svc du service et observez que sa @ServiceHost directive contient un attribut Factory qui spécifie le nom d’un ServiceHostFactory personnalisé.  
  
### <a name="set-up-build-and-run-the-sample"></a>Configurer, générer et exécuter l’exemple
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

3. Une fois la solution générée, exécutez Setup.bat pour configurer l’application ServiceModelSamples dans IIS 7,0. Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’application IIS 7,0.

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

5. Pour supprimer l’application IIS 7,0, exécutez *Cleanup.bat*.

## <a name="see-also"></a>Voir aussi

- [Comment : héberger un service WCF dans IIS](../feature-details/how-to-host-a-wcf-service-in-iis.md)
