---
title: Configuration et extension de l'exécution à l'aide de comportements
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 67db06649d6059ff6b6e6fb8d84058621fcc7dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185651"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Configuration et extension de l'exécution à l'aide de comportements
Les comportements vous permettent de modifier le comportement par défaut et d’ajouter des extensions personnalisées qui inspectent et valident la configuration du service ou modifient le comportement en temps d’exécution dans les applications client et service de la Windows Communication Foundation (WCF). Cette rubrique décrit les interfaces de comportement, la méthode utilisée pour les implémenter, et comment les ajouter par programme à la description de service (dans une application de service), au point de terminaison (dans une application cliente) ou dans un fichier de configuration. Pour plus d’informations sur l’utilisation de comportements fournis par le système, voir [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md) et [Specifying Client Run-Time Behavior](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Comportements  
 Les types de comportement sont ajoutés aux objets de description de point de terminaison de service ou de service (sur le service ou le client, respectivement) avant que ces objets ne soient utilisés par Windows Communication Foundation (WCF) pour créer un temps d’exécution qui exécute un service WCF ou un client WCF. Lorsque ces comportements sont appelés pendant le processus de construction d’exécution, ils sont ensuite capables d’accéder aux méthodes et propriétés d’exécution qui modifient l’exécution construite par le contrat, les liaisons et les adresses.  
  
### <a name="behavior-methods"></a>Méthodes de comportement  
 Tous les comportements ont une méthode `AddBindingParameters`, une méthode `ApplyDispatchBehavior`, une méthode `Validate` et une méthode `ApplyClientBehavior` avec une exception : <xref:System.ServiceModel.Description.IServiceBehavior> ne pouvant pas s'exécuter dans un client, il n'implémente pas `ApplyClientBehavior`.  
  
- Utilisez la méthode `AddBindingParameters` pour modifier ou ajouter des objets personnalisés à une collection à laquelle les liaisons personnalisées peuvent accéder lorsque l'exécution est construite. Par exemple, la méthode utilisée pour spécifier les exigences de protection affecte la façon dont le canal est construit, mais n’est pas connue par le développeur de canal.  
  
- Utilisez la méthode `Validate` pour examiner l'arborescence de description et l'objet d'exécution correspondant afin de s'assurer qu'elle est conforme à certains critères.  
  
- Utilisez les méthodes `ApplyDispatchBehavior` et `ApplyClientBehavior` pour examiner l’arborescence de description et modifier l’exécution pour une portée spécifique sur le service ou le client. Vous pouvez également insérer des objets d’extension.  
  
    > [!NOTE]
    > Bien qu'une arborescence de description soit fournie dans ces méthodes, elle l'est uniquement à des fins d'examen. Si une arborescence de description est modifiée, le comportement n’est pas défini.  
  
 Les propriétés que vous pouvez modifier et les interfaces de personnalisation que vous pouvez implémenter sont accessibles via les classes d'exécution de service et de client. Les types de services sont les classes <xref:System.ServiceModel.Dispatcher.DispatchRuntime> et <xref:System.ServiceModel.Dispatcher.DispatchOperation>. Les types de client sont les classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> et <xref:System.ServiceModel.Dispatcher.ClientOperation>. Les classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> et <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sont les points d'entrée d'extensibilité pour accéder aux propriétés d'exécution à l'échelle du service et du client et aux collections d'extensions, respectivement. De la même façon, les classes <xref:System.ServiceModel.Dispatcher.ClientOperation> et <xref:System.ServiceModel.Dispatcher.DispatchOperation> exposent les propriétés d’exécution d’opération de service et de client et les collections d’extensions, respectivement. Toutefois, vous pouvez accéder à l'objet d'exécution de portée plus large à partir de l'objet d'exécution d'opération et vice versa, si nécessaire.  
  
> [!NOTE]
> Pour une discussion des propriétés d’exécution et des types d’extension que vous pouvez utiliser pour modifier le comportement d’exécution d’un client, voir [Extending Clients](extending-clients.md). Pour une discussion des propriétés d’exécution et des types d’extension que vous pouvez utiliser pour modifier le comportement d’exécution d’un répartiteur de service, voir [Extending Dispatchers](extending-dispatchers.md).  
  
 La plupart des utilisateurs de WCF n’interagissent pas directement avec le temps d’exécution; au lieu de cela, ils utilisent des constructions de modèle de programmation de base comme les paramètres, les contrats, les liaisons, les adresses et les attributs de comportement sur les classes ou les comportements dans les fichiers de configuration. Ces constructions constituent *l’arbre de description*, qui est la spécification complète pour la construction d’un temps d’exécution pour soutenir un service ou un client décrit par l’arbre de description.  
  
 Il existe quatre types de comportements dans WCF:  
  
- Les comportements de service (types <xref:System.ServiceModel.Description.IServiceBehavior>) activent la personnalisation de l'ensemble de l'exécution du service, dont <xref:System.ServiceModel.ServiceHostBase>.  
  
- Les comportements de point de terminaison (types <xref:System.ServiceModel.Description.IEndpointBehavior>) activent la personnalisation de points de terminaison de service et leurs objets <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> associés.  
  
- Les comportements de contrat (types <xref:System.ServiceModel.Description.IContractBehavior>) activent à la fois la personnalisation des classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> et <xref:System.ServiceModel.Dispatcher.DispatchRuntime> dans les applications clientes et de service, respectivement.  
  
- Les comportements d'opération (types <xref:System.ServiceModel.Description.IOperationBehavior>) activent la personnalisation des classes <xref:System.ServiceModel.Dispatcher.ClientOperation> et <xref:System.ServiceModel.Dispatcher.DispatchOperation> à nouveau sur le client et le service.  
  
 Vous pouvez ajouter ces comportements aux divers objets de description en implémentant des attributs personnalisés, à l'aide de fichiers de configuration d'application, ou en les ajoutant directement à la collection de comportements sur l'objet de description approprié. Cependant, ils doivent être ajoutés à un objet de description de service ou de description de point de terminaison de service avant d'appeler <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur le <xref:System.ServiceModel.ServiceHost> ou un <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Portées de comportement  
 Il existe quatre types de comportement, chacun d'entre eux correspondant à une portée spécifique d'accès d'exécution.  
  
#### <a name="service-behaviors"></a>Comportements de service  
 Les comportements de service, qui implémentent <xref:System.ServiceModel.Description.IServiceBehavior>, constituent le mécanisme principal vous permettant de modifier l'ensemble de l'exécution du service. Il existe trois mécanismes d'ajout de comportements de service à un service.  
  
1. En utilisant un attribut sur la classe de service.  Lorsque <xref:System.ServiceModel.ServiceHost> est construit, l'implémentation <xref:System.ServiceModel.ServiceHost> utilise la réflexion pour découvrir l'ensemble d'attributs sur le type du service. Si ces attributs sont des implémentations de <xref:System.ServiceModel.Description.IServiceBehavior>, ils sont ajoutés à la collection de comportements sur <xref:System.ServiceModel.Description.ServiceDescription>. Cela permet à ces comportements de participer à la construction de l'exécution du service.  
  
2. En ajoutant par programme le comportement à la collection de comportements sur <xref:System.ServiceModel.Description.ServiceDescription>. Pour ce faire, utilisez les lignes de code suivantes :  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. En implémentant un <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personnalisé qui étend la configuration. Cela active l'utilisation du comportement de service à partir des fichiers de configuration d'application.  
  
 Des exemples de comportements de <xref:System.ServiceModel.ServiceBehaviorAttribute> service <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>dans WCF incluent l’attribut, le , et le <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportement.  
  
#### <a name="contract-behaviors"></a>Comportements de contrat  
 Les comportements de contrat, qui implémentent l'interface <xref:System.ServiceModel.Description.IContractBehavior>, permettent d'étendre à la fois l'exécution du client et du service sur un contrat.  
  
 Il existe deux mécanismes d'ajout de comportement de contrat à un contrat.  Le premier consiste à créer un attribut personnalisé à utiliser sur l'interface de contrat. Lorsqu’une interface de contrat <xref:System.ServiceModel.ServiceHost> est <xref:System.ServiceModel.ChannelFactory%601>transmise à a ou à un, WCF examine les attributs de l’interface. Si les attributs sont des implémentations de <xref:System.ServiceModel.Description.IContractBehavior>, ils sont ajoutés à la collection de comportements sur le <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> créé pour cette interface.  
  
 Vous pouvez également implémenter <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> sur l'attribut de comportement de contrat personnalisé. Dans ce cas, le comportement se présente comme suit lorsqu'il est appliqué aux éléments suivants :  
  
 •Interface de contrat. Dans ce cas, le comportement est appliqué à tous les contrats de ce <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> type dans n’importe quel critère d’évaluation et WCF ignore la valeur de la propriété.  
  
 •Classe de service. Dans ce cas, le comportement n'est appliqué qu'aux points de terminaison dont le contrat est la valeur de la propriété <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A>.  
  
 •Classe de rappel. Dans ce cas, le comportement est appliqué au critère de terminaison du <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> client duplex et WCF ignore la valeur de la propriété.  
  
 Le deuxième mécanisme consiste à ajouter le comportement à la collection de comportements sur <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Des exemples de comportements contractuels dans WCF incluent l’attribut. <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> Pour plus d'informations et obtenir un exemple, consultez la rubrique de référence.  
  
#### <a name="endpoint-behaviors"></a>Comportements de point de terminaison  
 Les comportements de point de terminaison, qui implémentent <xref:System.ServiceModel.Description.IEndpointBehavior>, constituent le mécanisme principal vous permettant de modifier l'ensemble de l'exécution du service ou du client pour un point de terminaison spécifique.  
  
 Il existe deux mécanismes d'ajout de comportements de point de terminaison à un service.  
  
1. Ajoutez le comportement à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A>.  
  
2. Implémentez un <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personnalisé qui étend la configuration.  
  
 Pour plus d'informations et obtenir un exemple, consultez la rubrique de référence.  
  
#### <a name="operation-behaviors"></a>Comportements d'opération  
 Les comportements d'opération, qui implémentent l'interface <xref:System.ServiceModel.Description.IOperationBehavior>, permettent d'étendre à la fois l'exécution du client et du service pour chaque opération.  
  
 Il existe deux mécanismes d'ajout de comportements d'opération à une opération. Le premier consiste à créer un attribut personnalisé à utiliser sur la méthode qui modélise l'opération. Lorsqu’une opération est <xref:System.ServiceModel.ServiceHost> ajoutée <xref:System.ServiceModel.ChannelFactory>à un ou <xref:System.ServiceModel.Description.IOperationBehavior> à un, WCF <xref:System.ServiceModel.Description.OperationDescription> ajoute tous les attributs à la collection de comportements sur le créé pour cette opération.  
  
 Le deuxième mécanisme consiste à ajouter directement le comportement à la collection de comportements sur un <xref:System.ServiceModel.Description.OperationDescription> construit.  
  
 Exemples de comportements d’opération <xref:System.ServiceModel.OperationBehaviorAttribute> dans <xref:System.ServiceModel.TransactionFlowAttribute>WCF comprennent le et le .  
  
 Pour plus d'informations et obtenir un exemple, consultez la rubrique de référence.  
  
### <a name="using-configuration-to-create-behaviors"></a>Création de comportements à l'aide de la configuration  
 Les comportements de service, de point de terminaison et de contrat peuvent, de par leur conception, être spécifiés dans le code ou à l'aide d'attributs ; seuls les comportements de service et de point de terminaison peuvent être configurés à l'aide de fichiers d'application ou de configuration Web. L'exposition des comportements à l'aide d'attributs permet aux développeurs de spécifier un comportement au moment de la compilation qui ne peut pas être ajouté, supprimé ou modifié pendant l'exécution. Cela s’avère souvent approprié pour les comportements qui sont systématiquement requis pour l’opération correcte d’un service (par exemple, les paramètres associés à la transaction de l’attribut <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>). L'exposition des comportements à l'aide de la configuration permet aux développeurs de laisser la spécification et la configuration de ces comportements à ceux qui déploient le service. Cela s'avère approprié pour les comportements qui sont des composants facultatifs ou qui représentent une autre configuration spécifique au déploiement, dans le cas par exemple de l'exposition des métadonnées pour le service ou de la configuration d'autorisation spécifique d'un service.  
  
> [!NOTE]
> Vous pouvez également utiliser des comportements qui prennent en charge la configuration afin d'appliquer les stratégies d'application de la société en les insérant dans le fichier de configuration machine.config et en verrouillant ces éléments. Pour une description et un exemple, voir [Comment : Verrouiller les points d’end dans l’entreprise](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Pour exposer un comportement à l’aide de la configuration, un développeur doit créer une classe dérivée de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, puis enregistrer cette extension avec la configuration.  
  
 L'exemple de code suivant indique comment <xref:System.ServiceModel.Description.IEndpointBehavior> implémente <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> :  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 Pour que le système de configuration charge un <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personnalisé, il doit être enregistré en tant qu’extension. L'exemple de code suivant présente le fichier de configuration du comportement de point de terminaison précédent :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Où `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` est le `HostApplication` type d’extension de comportement et est le nom de l’assemblage dans lequel cette classe a été compilée.  
  
### <a name="evaluation-order"></a>Ordre d'évaluation  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> et <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> sont chargés de générer l'exécution à partir de la description et du modèle de programmation. Les comportements, comme décrit précédemment, contribuent à ce processus de génération au niveau du service, du point de terminaison, du contrat et de l'opération.  
  
 <xref:System.ServiceModel.ServiceHost> applique les comportements dans l'ordre suivant :  
  
1. Service  
  
2. Contrat  
  
3. Point de terminaison  
  
4. Opération  
  
 Dans une collection de comportements, aucun ordre n’est garanti.  
  
 <xref:System.ServiceModel.ChannelFactory%601> applique les comportements dans l'ordre suivant :  
  
1. Contrat  
  
2. Point de terminaison  
  
3. Opération  
  
 Dans une collection de comportements, à nouveau aucun ordre n’est garanti.  
  
### <a name="adding-behaviors-programmatically"></a>Ajout de comportements par programme  
 Les propriétés de <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> dans l'application de service ne doivent pas être modifiées à l'issue de la méthode <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Certains membres, tels que la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> et les méthodes `AddServiceEndpoint` sur <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, lèvent une exception s'ils sont modifiés une fois ce stade passé. D'autres membres peuvent être modifiés, mais le résultat n'est pas défini.  
  
 De la même façon, sur le client les valeurs <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> ne doivent pas être modifiées après l'appel à <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. La propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> lève une exception si elle est modifiée une fois ce stade passé, mais les autres valeurs de description du client peuvent être modifiées sans erreur. Toutefois, le résultat n'est pas défini.  
  
 Aussi bien pour le service que le client, il est recommandé de modifier la description avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Règles d'héritage pour les attributs de comportement  
 L'ensemble des quatre types de comportements peuvent être remplis à l'aide d'attributs (comportements de service et comportements de contrat). Ces attributs étant définis sur des membres et objets managés, et les membres et objets managés prenant en charge l'héritage, il est nécessaire de définir la façon dont les attributs de comportement fonctionnent dans le contexte d'héritage.  
  
 À un niveau élevé, la règle veut que pour une portée spécifique (par exemple, service, contrat ou opération), tous les attributs de comportement de la hiérarchie d'héritage pour cette portée soient appliqués. S'il existe deux attributs de comportement du même type, seul le type le plus dérivé est utilisé.  
  
#### <a name="service-behaviors"></a>Comportements de service  
 Pour une classe de service donnée, l'ensemble des attributs de comportement de service sur cette classe, et sur les parents de celle-ci, sont appliqués. Si le même type d'attribut est appliqué à plusieurs emplacements dans la hiérarchie d'héritage, le type le plus dérivé est utilisé.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Par exemple, dans le cas précédent, le service B se termine par <xref:System.ServiceModel.InstanceContextMode> de <xref:System.ServiceModel.InstanceContextMode.Single>, un mode <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> de <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> et <xref:System.ServiceModel.ConcurrencyMode> de <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> a la valeur <xref:System.ServiceModel.ConcurrencyMode.Single>, car l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> sur le service B est « plus dérivé » que celui sur le service A.  
  
#### <a name="contract-behaviors"></a>Comportements de contrat  
 Pour un contrat donné, tous les attributs de comportement de contrat sur cette interface et sur les parents de celle-ci, sont appliqués. Si le même type d'attribut est appliqué à plusieurs emplacements dans la hiérarchie d'héritage, le type le plus dérivé est utilisé.  
  
#### <a name="operation-behaviors"></a>Comportements d'opération  
 Si une opération donnée ne substitue pas une opération virtuelle ou abstraite existante, aucune règle d'héritage ne s'applique.  
  
 Si une opération substitue une opération existante, alors tous les attributs de comportement d'opération sur cette opération, et sur les parents de celle-ci, sont appliqués.  Si le même type d'attribut est appliqué à plusieurs emplacements dans la hiérarchie d'héritage, le type le plus dérivé est utilisé.
