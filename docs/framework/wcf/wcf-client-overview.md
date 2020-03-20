---
title: Vue d'ensemble d'un client WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 7905d540e0f06dd2863cf80381210307e3021918
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183070"
---
# <a name="wcf-client-overview"></a>Vue d'ensemble d'un client WCF
Cette section décrit ce que font les applications client, comment configurer, créer et utiliser un client de la Fondation Windows Communication (WCF) et comment sécuriser les applications client.  
  
## <a name="using-wcf-client-objects"></a>Utilisation des objets clients WCF  
 Une application client est une application gérée qui utilise un client WCF pour communiquer avec une autre application. Pour créer une application client pour un service WCF, il faut les étapes suivantes :  
  
1. Obtenez le contrat de service, les informations de liaison et d'adresse pour un point de terminaison de service.  
  
2. Créez un client WCF en utilisant ces informations.  
  
3. Appelez les opérations.  
  
4. Fermez l’objet client WCF.  
  
 Les sections suivantes traitent de ces étapes et fournissent de brèves introductions aux problèmes suivants :  
  
- Gestion des erreurs.  
  
- Configuration et sécurisation des clients.  
  
- Création d'objets de rappel pour les services duplex.  
  
- Appels des services de façon asynchrone.  
  
- Appels des services à l'aide de canaux clients.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Obtenir le contrat de service, les liaisons et les adresses  
 Dans WCF, les services et les clients modélisent des contrats à l’aide d’attributs, d’interfaces et de méthodes gérés. Pour se connecter à un service dans une application cliente, vous devez obtenir les informations de type pour le contrat de service. En règle générale, vous le faites en utilisant [l’outil utilitaire De métadonnées De ServiceModel (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)qui télécharge les métadonnées à partir du service, la convertit en un fichier de code source géré dans la langue de votre choix, et crée un fichier de configuration d’application client que vous pouvez utiliser pour configurer votre objet client WCF. Par exemple, si vous allez créer un objet `MyCalculatorService`client WCF pour invoquer un , `http://computerName/MyCalculatorService/Service.svc?wsdl`et vous savez que les métadonnées de ce service `ClientCode.vb` est publié à , puis l’exemple de code suivant montre comment utiliser Svcutil.exe pour obtenir un fichier qui contient le contrat de service dans le code géré.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Vous pouvez soit compiler ce code de contrat dans l’application client ou dans un autre assemblage que l’application client peut ensuite utiliser pour créer un objet client WCF. Vous pouvez utiliser le fichier de configuration pour configurer l'objet client pour se connecter correctement au service.  
  
 Pour un exemple de ce processus, voir [Comment : Créer un client](how-to-create-a-wcf-client.md). Pour plus d’informations complètes sur les contrats, voir [Contrats](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Créer un objet client WCF  
 Un client WCF est un objet local qui représente un service WCF sous une forme que le client peut utiliser pour communiquer avec le service distant. Les types de clients WCF implémentent le contrat de service cible, donc lorsque vous en créez un et le configurez, vous pouvez ensuite utiliser l’objet client directement pour invoquer les opérations de service. Le temps d’exécution WCF convertit les appels de méthode en messages, les envoie au service, écoute la `out` `ref` réponse, et retourne ces valeurs à l’objet client WCF comme valeurs de retour ou paramètres.  
  
 Vous pouvez également utiliser des objets de canal client WCF pour vous connecter et utiliser les services. Pour plus de détails, voir [WCF Client Architecture](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Création d'un nouvel objet WCF  
 Pour illustrer l'utilisation d'une classe <xref:System.ServiceModel.ClientBase%601>, supposons que le contrat de service simple suivant a été généré depuis une application de service.  
  
> [!NOTE]
> Si vous utilisez Visual Studio pour créer votre client WCF, les objets sont chargés automatiquement dans le navigateur d’objets lorsque vous ajoutez une référence de service à votre projet.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Si vous n’utilisez pas Visual Studio, examinez le <xref:System.ServiceModel.ClientBase%601> code contractuel `ISampleService`généré pour trouver le type qui s’étend et l’interface du contrat de service . Dans ce cas, ce type ressemble au code suivant :  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Cette classe peut être créée comme un objet local à l'aide de l'un des constructeurs, elle peut être configurée, puis utilisée pour se connecter à un service du type `ISampleService`.  
  
 Il est recommandé de créer votre objet client WCF d’abord, puis l’utiliser et le fermer à l’intérieur d’un seul essai / bloc de capture. Vous ne devez `using` pas`Using` utiliser l’instruction (dans Visual Basic) car elle peut masquer les exceptions dans certains modes d’échec. Pour plus d’informations, voir les sections suivantes ainsi que [Use Close and Abort pour libérer les ressources des clients WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Contrats, liaisons et adresses  
 Avant de pouvoir créer un objet client WCF, vous devez configurer l’objet client. Plus précisément, il doit avoir un *critère de service* à utiliser. Un point de terminaison est la combinaison d’un contrat de service, d’une liaison et d’une adresse. (Pour plus d’informations sur les points de terminaison, voir [points de terminaison : Adresses, liaisons et contrats](./feature-details/endpoints-addresses-bindings-and-contracts.md).) En règle générale, ces [ \<](../configure-apps/file-schema/wcf/endpoint-of-client.md) informations sont situées dans le critère>élément d’un fichier de configuration d’application client, comme celui que l’outil Svcutil.exe génère, et est chargée automatiquement lorsque vous créez votre objet client. Les deux types de clients WCF ont également des surcharges qui vous permettent de spécifier programmatiquement ces informations.  
  
 Par exemple, un fichier de configuration généré pour un `ISampleService` utilisé dans les exemples précédents contient les informations suivantes sur le point de terminaison.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Ce fichier de configuration spécifie un point de terminaison cible dans l'élément `<client>`. Pour plus d’informations sur l’utilisation <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> de <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> plusieurs paramètres cibles, voir ou les constructeurs.  
  
## <a name="calling-operations"></a>Opérations appelantes  
 Une fois qu’un objet client a été créé et configuré, créez un bloc d’essai/capture, appelez les opérations de la même manière que vous le feriez si l’objet était local et fermez l’objet client WCF. Lorsque l’application client appelle la première opération, WCF ouvre automatiquement le canal sous-jacent, et le canal sous-jacent est fermé lorsque l’objet est recyclé. (Vous pouvez également ouvrir et fermer explicitement le canal avant ou après l'appel des autres opérations.)  
  
 Par exemple, si vous avez le contrat de service suivant :  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _
   Public Interface ICalculator  
        <OperationContract> _
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 Vous pouvez appeler les opérations en créant un objet client WCF et en appelant ses méthodes, comme le montre l’exemple de code suivant. Notez que l’ouverture, l’appel et la fermeture de l’objet client WCF se produit dans un seul bloc d’essai/capture. Pour plus d’informations, voir [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md) and [Use Close and Abort pour libérer les ressources des clients de WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Gestion des erreurs  
 Des exceptions peuvent se produire dans une application cliente lors de l'ouverture du canal client sous-jacent (en appelant explicitement ou automatiquement une opération), lors de l'utilisation de l'objet client ou de canal pour appeler des opérations, ou lors de la fermeture du canal client sous-jacent. Il est recommandé que les applications gèrent au minimum les exceptions <xref:System.TimeoutException?displayProperty=nameWithType> et <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> possibles en plus de tous les objets <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> levés suite aux erreurs SOAP retournées par les opérations. Les erreurs SOAP spécifiées dans le contrat d’opération sont levées aux applications clientes sous la forme d’une <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> où le paramètre de type représente le type de détail de l’erreur SOAP. Pour plus d’informations sur le traitement des conditions d’erreur dans une application client, voir [Envoyer et recevoir des défauts](sending-and-receiving-faults.md). Pour un échantillon complet, le montre comment gérer les erreurs chez un client, voir [exceptions attendues](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Configuration et sécurisation des clients  
 La configuration d'un client démarre par le chargement nécessaire des informations de point de terminaison cibles pour l'objet client ou de canal, généralement depuis un fichier de configuration, même s'il est possible aussi de charger ces informations par programme à l'aide des constructeurs et des propriétés du client. Toutefois, des étapes de configuration supplémentaires sont nécessaires pour activer certain comportement client et pour de nombreux scénarios de sécurité.  
  
 Par exemple, les conditions de sécurité pour les contrats de service sont déclarées dans l’interface de contrat de service, et si Svcutil.exe a créé un fichier de configuration, ce fichier contient généralement une liaison qui peut prendre en charge les spécifications de sécurité du service. Dans certains cas, toutefois, davantage de configuration de sécurité peut être requis, tel que configurer des informations d'identification du client. Pour plus d’informations sur la configuration de la sécurité pour les clients WCF, voir [Securing Clients](securing-clients.md).  
  
 De plus, certaines modifications personnalisées peuvent être activées dans des applications clientes, telles que les comportements d'exécution personnalisés. Pour plus d’informations sur la façon de configurer un comportement client personnalisé, voir [Configuring Client Behaviors](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Création d'objets de rappel pour les services duplex  
 Les services duplex spécifient un contrat de rappel que l'application cliente doit implémenter afin de fournir un objet de rappel pour le service à appeler selon les spécifications du contrat. Bien que les objets de rappel ne soient pas des services complets (par exemple, vous ne pouvez pas initialiser de canal avec un objet de rappel), pour les besoins de l'implémentation et de la configuration ils peuvent être considérés comme un type de service.  
  
 Les clients de services duplex doivent :  
  
- Implémenter une classe de contrat de rappel.  
  
- Créez une instance de la classe de mise <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> en œuvre du contrat de rappel et utilisez-la pour créer l’objet que vous transmettez au constructeur client WCF.  
  
- Appeler des opérations et traiter des rappels d'opération.  
  
 Les objets clients Duplex WCF fonctionnent comme leurs homologues non-duplex, à l’exception qu’ils exposent les fonctionnalités nécessaires pour prendre en charge les rappels, y compris la configuration du service de rappel.  
  
 Par exemple, vous pouvez contrôler différents aspects de comportement à l'exécution de l'objet de rappel en utilisant des propriétés de l'attribut <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> sur la classe de rappel. Un autre exemple est l'utilisation de la classe <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> pour permettre le retour d'informations sur les exceptions aux services qui appellent l'objet de rappel. Pour plus d’informations, voir [Duplex Services](./feature-details/duplex-services.md). Pour un échantillon complet, voir [Duplex](./samples/duplex.md).  
  
 Sur les ordinateurs Windows XP qui exécutent les services IIS (Internet Information Services) 5.1, les clients duplex doivent spécifier une adresse de base cliente à l'aide de la classe <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> ou une exception est levée. L'exemple de code suivant montre comment procéder.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Le code suivant montre comment effectuer cette opération dans un fichier de configuration  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Appels des services de façon asynchrone.  
 Le mode d'appel des opérations dépend entièrement du développeur du client. En effet, les messages qui composent une opération peuvent être mappés aux méthodes synchrones ou asynchrones lorsqu’ils sont exprimés dans le code managé. Par conséquent, si vous souhaitez générer un client qui appelle des opérations de façon asynchrone, vous pouvez utiliser Svcutil.exe pour générer le code client asynchrone à l'aide de l'option `/async`. Pour plus d’informations, voir [Comment : Opérations de service d’appel Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Appels des services à l'aide des canaux clients WCF  
 Les types de <xref:System.ServiceModel.ClientBase%601>clients WCF <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> s’étendent , qui lui-même dérive de l’interface pour exposer le système de canal sous-jacent. Vous pouvez appeler des services à l'aide du contrat de service cible avec la classe <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Pour plus de détails, voir [WCF Client Architecture](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
