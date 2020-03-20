---
title: 'Comment : héberger un service WCF dans WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184916"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Comment : héberger un service WCF dans WAS
Ce sujet décrit les étapes de base requises pour créer un service d’activation des processus Windows (également connu sous le nom de WAS). WAS est le nouveau service d’activation de processus généralisant les fonctionnalités des services IIS (Internet Information Services) qui fonctionnent avec des protocoles de transport non-HTTP. WCF utilise l’interface adaptateur de l’auditeur pour communiquer les demandes d’activation reçues sur les protocoles non-HTTP pris en charge par WCF, tels que TCP, les tuyaux nommés, et la file d’attente message.  
  
 Cette option d'hébergement requiert que les composants d'activation WAS soient installés et configurés correctement, mais ne requiert pas l'écriture du code d'hébergement dans le cadre de l'application. Pour plus d’informations sur l’installation et la configuration A WAS, voir [comment installer et configurer les composants d’activation WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> L’activation de WAS n’est pas prise en charge si le pipeline de traitement de demande du serveur web est en mode classique. Le pipeline de traitement de demande du serveur Web doit être en mode intégré si l'activation de WAS doit être utilisée.  
  
 Lorsqu’un service WCF est hébergé en WAS, les fixations standard sont utilisées de la manière habituelle. Toutefois, lors de l'utilisation de <xref:System.ServiceModel.NetTcpBinding> et de <xref:System.ServiceModel.NetNamedPipeBinding> pour configurer un service hébergé WAS, une contrainte doit être satisfaite. Lorsque des points de terminaison différents utilisent le même transport, les paramètres de liaison doivent correspondre dans les sept propriétés suivantes :  
  
- ConnectionBufferSize  
  
- ChannelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Sinon, le point de terminaison initialisé en premier détermine toujours les valeurs de ces propriétés et les points de terminaison ajoutés ultérieurement lèvent un <xref:System.ServiceModel.ServiceActivationException> s'ils ne correspondent pas à ces paramètres.  
  
 Pour la copie source de cet exemple, voir [L’activation du TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Pour créer un service de base hébergé par WAS  
  
1. Définissez un contrat de service pour le type de service.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implémentez le contrat de service dans une classe de service. Notez que l’adresse ou les informations de liaison ne sont pas spécifiées dans l’implémentation du service. Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Créez un fichier Web.config pour définir la liaison <xref:System.ServiceModel.NetTcpBinding> à utiliser par les points de terminaison `CalculatorService`.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Créez un fichier Service.svc contenant le code suivant.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Placez le fichier Service.svc dans votre rɰertoire virtuel IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Pour créer un client qui utilise le service  
  
1. Utilisez [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) de la ligne de commande pour générer du code à partir de métadonnées de service.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. L'application cliente générée contient également l'implémentation de `ClientCalculator`. Notez que les informations d’adresse et de liaison ne sont pas spécifiées n’importe où dans l’implémentation du service. Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. La configuration du client qui utilise <xref:System.ServiceModel.NetTcpBinding> est également générée par Svcutil.exe. Ce fichier doit être nommé dans le fichier App.config lors de l'utilisation de Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Compilez, puis exécutez le client.  
  
## <a name="see-also"></a>Voir aussi

- [Activation de TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
