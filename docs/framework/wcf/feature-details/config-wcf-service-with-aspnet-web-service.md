---
title: 'Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 52f7857a2dc7108eb308fde942bf153d85d8e8ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593605"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET

Pour configurer un point de terminaison de service Windows Communication Foundation (WCF) pour qu’il soit compatible avec les clients de service Web ASP.NET, utilisez le <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type comme type de liaison pour votre point de terminaison de service.  
  
 Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l'authentification du client au niveau du transport sur la liaison. Les clients de service Web ASP.NET ne prenant pas en charge l’encodage de message MTOM, la <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriété doit être conservée comme valeur par défaut, c’est-à-dire <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> . Les clients du service Web ASP.NET ne prennent pas en charge WS-Security, donc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> doit avoir la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> .  
  
 Pour rendre les métadonnées d’un service WCF disponibles pour les outils de génération de proxy de service Web ASP.NET (autrement dit, [Web Services Description Language Tool (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)), [Web Services Discovery Tool (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))et la fonctionnalité **Ajouter une référence Web** dans Visual Studio), vous devez exposer un point de terminaison de métadonnées http/obtenir.  
  
## <a name="add-an-endpoint-in-code"></a>Ajouter un point de terminaison dans le code  
  
1. Créez une nouvelle instance <xref:System.ServiceModel.BasicHttpBinding>.  
  
2. Vous pouvez éventuellement activer la sécurité de transport pour cette liaison de point de terminaison de service en affectant au mode de sécurité de la liaison la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Pour plus d’informations, consultez [sécurité du transport](transport-security.md).  
  
3. Ajoutez un nouveau point de terminaison d'application à votre hôte de service à l'aide de l'instance de liaison que vous venez de créer. Pour plus d’informations sur l’ajout d’un point de terminaison de service dans le code, consultez [Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md).  
  
4. Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus d’informations, consultez [Comment : publier des métadonnées pour un service à l’aide de code](how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>Ajouter un point de terminaison dans un fichier de configuration  
  
1. Créez une configuration de liaison <xref:System.ServiceModel.BasicHttpBinding>. Pour plus d’informations, consultez [Comment : spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md).  
  
2. Vous pouvez éventuellement activer la sécurité de transport pour la configuration de cette liaison de point de terminaison de service en affectant au mode de sécurité de la liaison la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Pour plus d’informations, consultez [sécurité du transport](transport-security.md).  
  
3. Configurez un nouveau point de terminaison d’application pour votre service à l’aide de la configuration de liaison que vous venez de créer. Pour plus d’informations sur l’ajout d’un point de terminaison de service dans un fichier de configuration, consultez [Comment : créer un point de terminaison de service dans la configuration](how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus d’informations, consultez [Comment : publier les métadonnées d’un service à l’aide d’un fichier de configuration](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter un point de terminaison WCF qui est compatible avec les clients de service Web ASP.NET dans le code et également dans les fichiers de configuration.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer un point de terminaison de service dans le code](how-to-create-a-service-endpoint-in-code.md)
- [Comment : publier les métadonnées d'un service à l'aide de code](how-to-publish-metadata-for-a-service-using-code.md)
- [Guide pratique pour spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md)
- [Comment : créer un point de terminaison de service dans la configuration.](how-to-create-a-service-endpoint-in-configuration.md)
- [Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Sécurité de transport](transport-security.md)
- [Utilisation des métadonnées](using-metadata.md)
