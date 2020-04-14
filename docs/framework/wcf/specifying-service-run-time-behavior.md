---
title: Spécification du comportement du service au moment de l'exécution
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 246f16cee85633499a6a1c200e608ee7bccf133c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243100"
---
# <a name="specifying-service-run-time-behavior"></a>Spécification du comportement du service au moment de l'exécution
Une fois que vous avez conçu un contrat de service ([Designing Service Contracts](designing-service-contracts.md)) et implémenté votre contrat de service ([Implementing Service Contracts](implementing-service-contracts.md)), vous pouvez configurer le comportement d’opération de l’exécution du service. Cette rubrique traite des comportements de service fournis par le système et des comportements d'opération et précise où rechercher plus d'informations pour créer de nouveaux comportements. Si certains comportements sont appliqués sous la forme d'attributs, un grand nombre s'appliquent à l'aide d'un fichier de configuration de l'application ou par programme. Pour plus d’informations sur la configuration de votre application de service, voir [Configuring Services](configuring-services.md).  
  
## <a name="overview"></a>Vue d’ensemble  
 Le contrat définit les entrées, sorties, types de données et fonctions d'un service de ce type. L'implémentation d'un contrat de service crée une classe qui, lorsqu'elle est configurée avec une liaison à une adresse, répond au contrat qu'elle implémente. Les informations contractuelles, de liaisons et d'adresse sont tout connues du client ; sans elles, le client ne peut pas utiliser le service.  
  
 Toutefois, les caractéristiques d'opération, telles que les problèmes de thread ou la gestion d'instance, sont opaques aux clients. Une fois que vous avez implémenté votre contrat de service, vous pouvez configurer un grand nombre de caractéristiques d'opération à l'aide des *comportements*. Les comportements sont des objets qui modifient l’exécution de la Windows Communication Foundation (WCF) en définissant une propriété en temps d’exécution ou en insérant un type de personnalisation dans le temps d’exécution. Pour plus d’informations sur la modification de l’exécution en créant des comportements définis par l’utilisateur, voir [Extending ServiceHost et la couche de modèle de service](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Les attributs <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> et <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> sont les comportements le plus largement utiles et qui exposent les fonctionnalités d'opération les plus couramment demandées. Comme ce sont des attributs, vous les appliquez à l'implémentation de service ou d'opération. Les autres comportements, tels que <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, sont appliqués en général à l'aide d'un fichier de configuration de l'application, bien que vous puissiez les utiliser par programme.  
  
 Ce sujet fournit un <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> aperçu des différents et attributs, décrit les différentes portées auxquelles les comportements peuvent fonctionner, et fournit une description rapide de nombreux comportements fournis par le système aux différentes portées qui peuvent être d’intérêt pour les développeurs WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute et OperationBehaviorAttribute  
 Les comportements les plus importants sont les attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute> que vous pouvez utiliser pour contrôler :  
  
- Durées de vie d'instance  
  
- Prise en charge multi-utilisateur et de synchronisation  
  
- Comportement de configuration  
  
- Comportement de transaction  
  
- Comportements de sérialisation  
  
- Transformation de métadonnées  
  
- Durée de vie de session  
  
- Filtrage d'adresse et traitement d'en-tête  
  
- Emprunt d'identité  
  
- Pour utiliser ces attributs, marquez l'implémentation de service ou d'opération avec l'attribut approprié à cette étendue et définissez les propriétés. Par exemple, l'exemple de code suivant affiche une implémentation d'opération qui utilise la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> pour exiger que les appelants de cette opération prennent en charge l'emprunt d'identité.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Un grand nombre des propriétés exigent la prise en charge supplémentaire à partir de la liaison. Par exemple, une opération qui requiert une transaction à partir du client doit être configurée pour utiliser une liaison qui prend en charge les transactions transmises.  
  
### <a name="well-known-singleton-services"></a>Services singleton connus  
 Vous pouvez utiliser les attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute> pour contrôler certaines durées de vie, les deux <xref:System.ServiceModel.InstanceContext> et des objets de service qui implémentent les opérations.  
  
 Par exemple, la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> contrôle la fréquence à laquelle <xref:System.ServiceModel.InstanceContext> est diffusé, et les propriétés <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> contrôlent le moment auquel l'objet de service est diffusé.  
  
 Toutefois, vous pouvez également créer un objet de service vous-même et créer l'hôte de service utilisant cet objet. Pour ce faire, vous devez également affecter <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> à la propriété <xref:System.ServiceModel.InstanceContextMode.Single> , sans quoi une exception est levée lorsque l'hôte de service est ouvert.  
  
 Utilisez le constructeur <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> pour créer un service de ce type. Il fournit une alternative à l'implémentation d'un <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> personnalisé lorsque vous souhaitez fournir une instance d'objet spécifique qui sera utilisée par un service singleton. Vous pouvez utiliser cette surcharge lorsque votre type de mise en œuvre de service est difficile à construire (par exemple, s’il ne met pas en œuvre un constructeur public sans paramètres).
  
 Notez que lorsqu’un objet est fourni à ce constructeur, certaines fonctionnalités liées à la Windows Communication Foundation (WCF) instancing comportement fonctionnent différemment. Par exemple, l'appel de <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> n'a aucun effet lorsqu'une instance d'objet connue est fournie. De même, tout autre mécanisme de libération d'instance est ignoré. La classe <xref:System.ServiceModel.ServiceHost> se comporte toujours comme si la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> avait la valeur <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pour toutes les opérations.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Autres comportements de service, de point de terminaison, de contrat et d'opération  
 Les comportements de service, tels que l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> , fonctionnent sur l'ensemble d'un service. Par exemple, si vous affectez à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> la valeur <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> , vous devez gérer vous-même les problèmes de synchronisation de thread à l'intérieur de chaque opération dans ce service. Les comportements de point de terminaison fonctionnent sur un point de terminaison ; un grand nombre des comportements de point de terminaison fournis par le système sont destinés aux fonctionnalités clientes. Les comportements de contrat fonctionnent au niveau du contrat, et les comportements d'opération modifient la remise d'opération.  
  
 Un grand nombre de ces comportements sont implémentés sur les attributs, et sont utilisés comme les attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute> , en les appliquant à l'implémentation d'opération ou de classe de service appropriée. Les autres comportements, tels que les objets <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior> , sont appliqués en général à l'aide d'un fichier de configuration de l'application, bien que vous puissiez les utiliser par programme.  
  
 Par exemple, la publication de métadonnées est configurée en utilisant l'objet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> . Le fichier de configuration de l'application suivant illustre l'utilisation la plus courante.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Les sections suivantes décrivent un grand nombre des comportements les plus utiles fournis par le système que vous pouvez utiliser pour modifier la remise d'exécution de votre service ou client. Consultez la rubrique de référence pour déterminer comment utiliser chacun d'entre eux.  
  
### <a name="service-behaviors"></a>Comportements de service  
 Les comportements suivants fonctionnent sur les services.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Appliqué à un service WCF pour indiquer si ce service peut être exécuté en mode ASP.NET Compatibilité.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Contrôle comment le service autorise les revendications clientes.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Configure les informations d'identification d'un service. Utilisez cette classe pour spécifier les informations d'identification du service, tel qu'un certificat X.509.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Permet le débogage et l’aide des fonctionnalités d’information pour un service WCF.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Détermine la publication de métadonnées de service et des informations associées.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Spécifie le comportement d'audit d'événements de sécurité.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Configure les paramètres de débit d'exécution qui permettent de régler les performances du service.  
  
### <a name="endpoint-behaviors"></a>Comportements de point de terminaison  
 Les comportements suivants fonctionnent sur des points de terminaison. Un grand nombre de ces comportements sont utilisés dans les applications clientes.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Configure une implémentation de service de rappel dans une application cliente duplex.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Permet le débogage de service pour un objet de rappel WCF.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Permet à l'utilisateur de configurer les informations d'identification de service et de client ainsi que paramètres d'authentification des informations d'identification de service à utiliser sur le client.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. Utilisé par les clients pour spécifier l'URI (Uniform Resource Identifier) pour lequel le canal de transport doit être créé.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Demande à WCF de `MustUnderstand` désactiver le traitement.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Indique à l'exécution d'utiliser un processus de réception synchrone pour les canaux.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optimise les opérations de réception pour les transports qui prennent en charge les réceptions transactionnelles.  
  
### <a name="contract-behaviors"></a>Comportements de contrat  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Spécifie les fonctionnalités que les liaisons doivent fournir à l'implémentation de service ou de client.  
  
### <a name="operation-behaviors"></a>Comportements d'opération  
 Les comportements d'opération suivants spécifient les contrôles de sérialisation et de transaction pour les opérations.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Représente le comportement à l'exécution de <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Détermine le comportement à l'exécution du `XmlSerializer` et l'associe à une opération.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Spécifie le niveau dans lequel une opération de service accepte un en-tête de transaction.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des services](configuring-services.md)
- [Guide pratique pour contrôler l’instanciation de service](./feature-details/how-to-control-service-instancing.md)
