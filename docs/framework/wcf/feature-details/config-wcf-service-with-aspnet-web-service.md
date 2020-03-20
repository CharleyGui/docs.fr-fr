---
title: 'Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 6a06e1983a54581cfb89f008e9f063a671e992c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185351"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET
Pour configurer un critère de service de la Windows Communication Foundation (WCF) <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> pour être interopérable avec ASP.NET clients du service Web, utilisez le type comme type de liaison pour votre point de terminaison de service.  
  
 Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l'authentification du client au niveau du transport sur la liaison. ASP.NET clients du service Web ne prennent pas en <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> charge l’encodage de <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>messages MTOM, de sorte que la propriété doit être laissée comme valeur par défaut, qui est . Les clients du service Web ASP.NET ne prennent pas en charge la spécification WS-Security, donc <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> doit avoir la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Pour mettre les métadonnées d’un service WCF à la disposition de ASP.NET outils de génération de proxy de service Web [(c’est-à-dire l’outil linguistique de description des services Web (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)) [l’outil de découverte des services Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))et la fonction Add Web Reference dans Visual Studio), vous devez exposer un point de terminaison de métadonnées HTTP/GET.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Pour ajouter un point de terminaison WCF compatible avec les clients du service Web ASP.NET dans du code  
  
1. Créez une nouvelle instance <xref:System.ServiceModel.BasicHttpBinding>.  
  
2. Vous pouvez éventuellement activer la sécurité de transport pour cette liaison de point de terminaison de service en affectant au mode de sécurité de la liaison la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Pour plus de détails, veuillez consulter [transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Ajoutez un nouveau point de terminaison d'application à votre hôte de service à l'aide de l'instance de liaison que vous venez de créer. Pour plus de détails sur la façon d’ajouter un point de terminaison de service dans le code, voir comment [: Créer un point d’évaluation du service dans le code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus de détails, voir [comment : Publier des métadonnées pour un service utilisant le code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Pour ajouter un point de terminaison WCF compatible avec les clients du service Web ASP.NET dans un fichier de configuration  
  
1. Créez une configuration de liaison <xref:System.ServiceModel.BasicHttpBinding>. Pour plus de détails, voir comment [: Spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Vous pouvez éventuellement activer la sécurité de transport pour la configuration de cette liaison de point de terminaison de service en affectant au mode de sécurité de la liaison la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Pour plus de détails, voir [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Configurez un nouveau point de terminaison d’application pour votre service à l’aide de la configuration de liaison que vous venez de créer. Pour plus de détails sur la façon d’ajouter un point de terminaison de service dans un fichier de configuration, voir comment [: Créer un point d’évaluation de service dans configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Activez un point de terminaison de métadonnées HTTP/GET pour votre service. Pour plus de détails, consultez le [comment : Publier des métadonnées pour un service à l’aide d’un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant, le code montre comment ajouter un point de terminaison WCF compatible avec ASP.NET clients du service Web dans le code et alternativement dans les fichiers de configuration.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer un point de terminaison de service dans le code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Comment : publier les métadonnées d'un service à l'aide de code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Guide pratique pour spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Comment : créer un point de terminaison de service dans la configuration.](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Sécurité des transports](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Utilisation des métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)
