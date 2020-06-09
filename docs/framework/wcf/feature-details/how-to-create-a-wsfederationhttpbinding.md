---
title: 'Comment : créer une liaison WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: ccc28c46e8be0b835cf08d372ef85b8a66e989ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595438"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Comment : créer une liaison WSFederationHttpBinding

Dans Windows Communication Foundation (WCF), la <xref:System.ServiceModel.WSFederationHttpBinding> classe ( [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) dans la configuration) fournit un mécanisme pour exposer un service fédéré. autrement dit, un service qui oblige les clients à s'authentifier à l'aide d'un jeton de sécurité émis par un service de jeton de sécurité. Cette rubrique montre comment installer <xref:System.ServiceModel.WSFederationHttpBinding> dans le code et la configuration. Une fois la liaison créée, vous pouvez installer un point de terminaison pour utiliser cette liaison.

 Les étapes de base sont les suivantes :

1. Sélectionnez un mode de sécurité. <xref:System.ServiceModel.WSFederationHttpBinding> prend en charge `Message`, qui fournit la sécurité de bout en bout au niveau du message, même avec plusieurs sauts, et `TransportWithMessageCredential`, qui fournit les meilleures performances dans les cas où le client et le service peuvent établir une connexion directe sur HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> prend également en charge `None` comme mode de sécurité. Ce mode, non sécurisé, est fourni à des fins de débogage uniquement. Si un point de terminaison de service est déployé avec <xref:System.ServiceModel.WSFederationHttpBinding> avec le mode de sécurité défini sur `None` , la liaison cliente résultante (générée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)) est un <xref:System.ServiceModel.WSHttpBinding> avec le mode de sécurité `None` .

     Contrairement à d'autres liaisons fournies par le système, il n'est pas nécessaire de sélectionner un type d'informations d'identification du client lors de l'utilisation de `WSFederationHttpBinding`. Cela est dû au fait que le type d'informations d'identification du client est toujours un jeton émis. WCF acquiert un jeton à partir d’un émetteur spécifié et présente ce jeton au service pour authentifier le client.

2. Sur les clients fédérés, affectez à la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> l'URL du service de jeton de sécurité. Affectez au <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> la liaison à utiliser pour communiquer avec le service de jeton de sécurité.

3. facultatif. Affectez à la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> l'URI (Uniform Resource Identifier) d'un type de jeton. Sur les services fédérés, spécifiez le type de jeton que le service attend. Sur les clients fédérés, spécifiez le type de jeton que le client demande au service de jeton de sécurité.

     Si aucun type de jeton n'est spécifié, les clients génèrent des jetons RST (Request Security Token) WS-Trust sans l'URI d'un type de jeton, et les services attendent l'authentification du client à l'aide d'un jeton SAML (Security Assertions Markup Language) 1.1 par défaut.

     L’URI d’un jeton SAML 1,1 est `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .

4. facultatif. Sur les services fédérés, affectez à la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> l'URL de métadonnées d'un service de jeton de sécurité. Le point de terminaison de métadonnées permet aux clients du service de sélectionner une paire liaison/point de terminaison appropriée, si le service est configuré pour publier des métadonnées. Pour plus d’informations sur la publication de métadonnées, consultez [publication de métadonnées](publishing-metadata.md).

 Vous pouvez également définir d'autres propriétés, y compris le type de clé utilisé comme clé de vérification dans le jeton émis, la suite algorithmique à utiliser entre le client et le service, l'option de négocier ou de spécifier explicitement les informations d'identification du service, toutes les revendications spécifiques que le service s'attend à trouver dans le jeton émis et tous les éléments XML supplémentaires qui doivent être ajoutés à la demande que le client envoie au service de jeton de sécurité.

> [!NOTE]
> La propriété `NegotiateServiceCredential` n'est pertinente que si `SecurityMode` a la valeur `Message`. Si `SecurityMode` a la valeur `TransportWithMessageCredential`, alors la propriété `NegotiateServiceCredential` est ignorée.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Pour configurer une liaison WSFederationHttpBinding dans le code

1. Créez une instance de <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Affectez à la propriété <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.WSFederationHttpSecurityMode> ou <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> selon le cas. Si une suite d’algorithmes autre que <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> est requise, affectez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> à la propriété une valeur extraite de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .

3. Définissez la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> comme il convient.

4. Affectez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> à la propriété la valeur <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` ou.`AsymmetricKey` Si nécessaire.

5. Affectez la valeur appropriée à la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A>. Si aucune valeur n’est définie, WCF prend par défaut `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` la valeur, qui indique les jetons SAML 1,1.

6. Requis sur le client si aucun émetteur local n'est spécifié ; facultatif sur le service. Créez un <xref:System.ServiceModel.EndpointAddress> qui contient les informations d'adresse et d'identité du service de jeton de sécurité et assignez l'instance <xref:System.ServiceModel.EndpointAddress> à la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A>.

7. Requis sur le client si aucun émetteur local n'est spécifié ; non utilisé sur le service. Créez un <xref:System.ServiceModel.Channels.Binding> pour le `SecurityTokenService` et assignez l' <xref:System.ServiceModel.Channels.Binding> instance à la <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> propriété.

8. Non utilisé sur le client ; facultatif sur le service. Créez une instance <xref:System.ServiceModel.EndpointAddress> pour les métadonnées du service de jeton de sécurité et assignez-la à la propriété `IssuerMetadataAddress`.

9. Facultatif sur le client et le service. Créez et ajoutez une ou plusieurs instances <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> à la collection retournée par la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>.

10. Facultatif sur le client et le service. Créez et ajoutez une ou plusieurs instances <xref:System.Xml.XmlElement> à la collection retournée par la propriété <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Pour créer un point de terminaison fédéré dans la configuration

1. Créez un [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) en tant qu’enfant de l' [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) élément dans le fichier de configuration de l’application.

2. Créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément en tant qu’enfant de [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) et affectez `name` à l’attribut une valeur appropriée.

3. Créez un `<security>` élément en tant qu’enfant de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément.

4. Affectez à l'attribut `mode` sur l'élément `<security>` une valeur de `Message` ou de `TransportWithMessageCredential`, selon le cas.

5. Créez un élément `<message>` en tant qu'enfant de l'élément `<security>`.

6. facultatif. Affectez une valeur appropriée à l'attribut `algorithmSuite` sur l'élément `<message>`. Par défaut, il s’agit de `Basic256`.

7. facultatif. Si une clé de vérification asymétrique est requise, affectez à l'attribut `issuedKeyType` de l'élément `<message>` la valeur `AsymmetricKey`. Par défaut, il s’agit de `SymmetricKey`.

8. facultatif. Définissez l'attribut `issuedTokenType` sur l'élément `<message>`.

9. Requis sur le client si aucun émetteur local n'est spécifié ; facultatif sur le service. Créez un élément `<issuer>` en tant qu'enfant de l'élément `<message>`.

10. Affectez l'attribut `address` à l'élément `<issuer>` et spécifiez l'adresse à laquelle le service de jeton de sécurité accepte des demandes de jeton.

11. facultatif. Ajoutez un élément enfant `<identity>` et spécifiez l'identité du service de jeton de sécurité.

12. Pour plus d’informations, consultez [identité du service et authentification](service-identity-and-authentication.md).

13. Requis sur le client si aucun émetteur local n'est spécifié ; non utilisé sur le service. Créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dans la section liaisons qui peut être utilisée pour communiquer avec le service d’accès aux jetons de sécurité. Pour plus d’informations sur la création d’une liaison, consultez [Comment : spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md).

14. Spécifiez la liaison créée à l’étape précédente en définissant les attributs `binding` et `bindingConfiguration` de l’élément `<issuer>`.

15. Non utilisé sur le client ; facultatif sur le service. Créez un `<issuerMetadata>` élément en tant qu’enfant de l' `message` élément <>. Puis, dans un attribut `address` sur l'élément `<issuerMetadata>`, spécifiez l'adresse à laquelle le service de jeton de sécurité doit publier ses métadonnées. Éventuellement, ajoutez un élément enfant `<identity>` et spécifiez l'identité du service de jeton de sécurité.

16. Facultatif sur le client et le service. Ajoutez un élément `<claimTypeRequirements>` en tant qu'enfant de l'élément `<message>`. Spécifiez les revendications obligatoires et facultatives sur lesquelles repose le service en ajoutant des [\<add>](../../configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) éléments à l' `<claimTypeRequirements>` élément et en spécifiant le type de revendication avec l' `claimType` attribut. Spécifiez si une revendication donnée est requise ou facultative en définissant l'attribut `isOptional`.

## <a name="example"></a>Exemple

L'exemple de code suivant montre comment installer `WSFederationHttpBinding` de façon impérative.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Fédération](federation.md)
- [Federation, exemple](../samples/federation-sample.md)
- [Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
