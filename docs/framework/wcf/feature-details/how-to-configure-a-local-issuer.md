---
title: 'Procédure : configurer un émetteur local'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 98d4c01bf2b84a6379eca5d0e1d5dbee68dc7cdd
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487135"
---
# <a name="how-to-configure-a-local-issuer"></a>Procédure : configurer un émetteur local
Cette rubrique décrit comment configurer un client afin d'utiliser un émetteur local pour les jetons émis.  
  
 Lorsqu'un client communique avec un service fédéré, il arrive souvent que le service spécifie l'adresse du service d'émission de jeton de sécurité qui est attendue pour émettre le jeton que le client utilisera pour s'authentifier auprès du service fédéré. Dans certaines situations, le client peut être configuré pour utiliser un *émetteur local*.  
  
 Windows Communication Foundation (WCF) utilise un émetteur local dans les cas où l’adresse de l’émetteur d’une liaison fédérée est `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`. Dans ce cas, vous devez configurer <xref:System.ServiceModel.Description.ClientCredentials> avec l’adresse de l’émetteur local et la liaison à utiliser pour communiquer avec celui-ci.  
  
> [!NOTE]
>  Si le <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> propriété de la `ClientCredentials` classe est définie sur `true`, une adresse d’émetteur local n’est pas spécifiée, et l’adresse d’émetteur spécifiée par le [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou autres liaison fédérée est `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, ou est `null`, l’émetteur de Windows CardSpace est utilisé.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Pour configurer l'émetteur local dans le code  
  
1. Créez une variable de type <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2. Affectez à la variable la valeur de l'instance retournée par la propriété <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> de la classe `ClientCredentials`. Cette instance est retournée par la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> du client (héritée de <xref:System.ServiceModel.ClientBase%601>) ou la propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A> de <xref:System.ServiceModel.ChannelFactory> :  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3. Affectez une nouvelle instance de <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> à la propriété <xref:System.ServiceModel.EndpointAddress>, avec l'adresse de l'émetteur local comme argument au constructeur.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Ou bien, créez une instance <xref:System.Uri> comme argument au constructeur.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     Le `addressHeaders` paramètre est un tableau de <xref:System.ServiceModel.Channels.AddressHeader> instances, comme indiqué.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4. Définissez la liaison de l’émetteur local à l’aide de la <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> propriété.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5. Facultatif. Ajoutez des comportements de point de terminaison configurés pour l’émetteur local en ajoutant ces comportements à la collection retournée par la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Pour configurer l'émetteur local dans la configuration  
  
1. Créer un [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) élément en tant qu’enfant de le [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) élément lui-même est un enfant de la [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) élément dans un comportement de point de terminaison.  
  
2. Affectez à l'attribut `address` l'adresse de l'émetteur local qui acceptera des demandes de jeton.  
  
3. Affectez aux attributs `binding` et `bindingConfiguration` des valeurs référençant la liaison appropriée à utiliser lors de la communication avec le point de terminaison de l'émetteur local.  
  
4. Facultatif. Définir le [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) élément en tant qu’enfant de la <`localIssuer`> élément et spécifiez les informations d’identité de l’émetteur local.  
  
5. Facultatif. Définir le [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) élément en tant qu’enfant de la <`localIssuer`> élément et spécifiez les en-têtes supplémentaires qui sont requis pour adresser correctement l’émetteur local.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Notez que si une liaison et une adresse d’émetteur sont spécifiées pour une liaison donnée, l’émetteur local n’est pas utilisé pour les points de terminaison qui utilisent cette liaison. Les clients qui prévoient d'utiliser systématiquement l'émetteur local doivent s'assurer de ne pas utiliser de liaison de ce type ou de modifier la liaison afin que l'adresse de l'émetteur soit `null`.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Configurer les informations d’identification sur un Service de fédération](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Guide pratique pour Créer un Client fédéré](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Guide pratique pour Créer une liaison WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
