---
title: 'Comment : sécuriser des points de terminaison de métadonnées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: ee64e53f49e15059c91982f2e64879b9f4c76d78
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834678"
---
# <a name="how-to-secure-metadata-endpoints"></a>Comment : sécuriser des points de terminaison de métadonnées

Les métadonnées d'un service peuvent contenir des informations sensibles sur votre application dont un utilisateur malveillant peut tirer parti. Les consommateurs de votre service peuvent également avoir besoin d'un mécanisme sécurisé pour obtenir des métadonnées sur votre service. Par conséquent, il est parfois nécessaire de publier vos métadonnées à l'aide d'un point de terminaison sécurisé.

Les points de terminaison de métadonnées sont généralement sécurisés à l’aide des mécanismes de sécurité standard définis dans Windows Communication Foundation (WCF) pour la sécurisation des points de terminaison d’application. Pour plus d’informations, consultez [vue d’ensemble](security-overview.md)de la sécurité.

Cette rubrique présente en détail les étapes permettant de créer un point de terminaison sécurisé par un certificat SSL (Secure Sockets Layer) ou, en d'autres termes, un point de terminaison HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Pour créer un point de terminaison sécurisé de métadonnées HTTPS GET dans le code

1. Configurez un port avec un certificat X.509 approprié. Le certificat doit provenir d'une autorité approuvée et il doit avoir une utilisation prévue de l'autorisation de service. Vous devez utiliser l'outil HttpCfg.exe pour joindre le certificat au port. Consultez [procédure : configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > Le sujet du certificat ou son nom DNS (Domain Name System) doit correspondre au nom de l'ordinateur. Ceci est essentiel car l'une des premières étapes effectuées par le mécanisme HTTPS est de vérifier que le certificat est émis vers le même URI (Uniform Resource Identifier) que l'adresse avec laquelle il est appelé.

2. Créez une nouvelle instance de la classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.

3. Affectez la valeur <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de la classe `true`.

4. Affectez une URL appropriée à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>. Notez que si vous spécifiez une adresse absolue, l'URL doit commencer par le préfixe https://. Si vous spécifiez une adresse relative, vous devez fournir une adresse de base HTTPS pour votre hôte de service. Si cette propriété n'est pas définie, l'adresse par défaut est "" ou directement l'adresse de base HTTPS pour le service.

5. Ajoutez l’instance à la collection de comportements que la propriété <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> de la classe <xref:System.ServiceModel.Description.ServiceDescription> retourne, comme l’illustre le code ci-dessous.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Pour créer un point de terminaison sécurisé de métadonnées HTTPS GET dans la configuration

1. Ajoutez un élément [\<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) à l’élément [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) du fichier de configuration de votre service.

2. Ajoutez un élément [\<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l’élément comportements de l' [\<>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .

3. Ajoutez un élément de [> de comportement\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) à l’élément `<serviceBehaviors>`.

4. Affectez une valeur appropriée à l'attribut `name` de l'élément `<behavior>`. L'attribut `name` est obligatoire. L'exemple ci-dessous utilise la valeur `mySvcBehavior`.

5. Ajoutez un [>\<serviceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à l’élément `<behavior>`.

6. Affectez à l'attribut `httpsGetEnabled` de l'élément `<serviceMetadata>` la valeur `true`.

7. Affectez une valeur appropriée à l'attribut `httpsGetUrl` de l'élément `<serviceMetadata>`. Notez que si vous spécifiez une adresse absolue, l'URL doit commencer par le préfixe https://. Si vous spécifiez une adresse relative, vous devez fournir une adresse de base HTTPS pour votre hôte de service. Si cette propriété n'est pas définie, l'adresse par défaut est "" ou directement l'adresse de base HTTPS pour le service.

8. Pour utiliser le comportement avec un service, affectez à l’attribut `behaviorConfiguration` de l’élément [>\<service](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) la valeur de l’attribut Name de l’élément Behavior. Le code de configuration ci-dessous illustre un exemple complet.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a>Exemple

L'exemple ci-dessous crée une instance d'une classe <xref:System.ServiceModel.ServiceHost> et ajoute un point de terminaison. Le code crée ensuite une instance de la classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> et définit les propriétés pour créer un point d'échange de métadonnées sécurisé.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Compilation du code

L'exemple de code utilise les espaces de noms suivants :

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Guide pratique pour configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Considérations sur la sécurité des métadonnées](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
