---
title: 'Comment : sécuriser des points de terminaison de métadonnées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c5efd921d3826ef814bf45d6895255981101d992
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592955"
---
# <a name="how-to-secure-metadata-endpoints"></a>Comment : sécuriser des points de terminaison de métadonnées

Les métadonnées d'un service peuvent contenir des informations sensibles sur votre application dont un utilisateur malveillant peut tirer parti. Les consommateurs de votre service peuvent également avoir besoin d'un mécanisme sécurisé pour obtenir des métadonnées sur votre service. Par conséquent, il est parfois nécessaire de publier vos métadonnées à l'aide d'un point de terminaison sécurisé.

Les points de terminaison de métadonnées sont généralement sécurisés à l’aide des mécanismes de sécurité standard définis dans Windows Communication Foundation (WCF) pour la sécurisation des points de terminaison d’application. Pour plus d’informations, consultez [Vue d’ensemble de la sécurité](security-overview.md).

Cette rubrique présente en détail les étapes permettant de créer un point de terminaison sécurisé par un certificat SSL (Secure Sockets Layer) ou, en d'autres termes, un point de terminaison HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Pour créer un point de terminaison sécurisé de métadonnées HTTPS GET dans le code

1. Configurez un port avec un certificat X.509 approprié. Le certificat doit provenir d'une autorité approuvée et il doit avoir une utilisation prévue de l'autorisation de service. Vous devez utiliser l'outil HttpCfg.exe pour joindre le certificat au port. Consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > Le sujet du certificat ou son nom DNS (Domain Name System) doit correspondre au nom de l'ordinateur. Ceci est essentiel car l'une des premières étapes effectuées par le mécanisme HTTPS est de vérifier que le certificat est émis vers le même URI (Uniform Resource Identifier) que l'adresse avec laquelle il est appelé.

2. Créez une nouvelle instance de la classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.

3. Affectez la valeur <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de la classe `true`.

4. Affectez une URL appropriée à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>. Notez que si vous spécifiez une adresse absolue, l’URL doit commencer par le schéma `https://` . Si vous spécifiez une adresse relative, vous devez fournir une adresse de base HTTPS pour votre hôte de service. Si cette propriété n'est pas définie, l'adresse par défaut est "" ou directement l'adresse de base HTTPS pour le service.

5. Ajoutez l’instance à la collection de comportements que la propriété <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> de la classe <xref:System.ServiceModel.Description.ServiceDescription> retourne, comme l’illustre le code ci-dessous.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Pour créer un point de terminaison sécurisé de métadonnées HTTPS GET dans la configuration

1. Ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément à l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément du fichier de configuration pour votre service.

2. Ajoutez un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) élément à l' [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément.

3. Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément à l' `<serviceBehaviors>` élément.

4. Affectez une valeur appropriée à l'attribut `name` de l'élément `<behavior>`. L'attribut `name` est obligatoire. L'exemple ci-dessous utilise la valeur `mySvcBehavior`.

5. Ajoutez un [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) à l' `<behavior>` élément.

6. Affectez à l'attribut `httpsGetEnabled` de l'élément `<serviceMetadata>` la valeur `true`.

7. Affectez une valeur appropriée à l'attribut `httpsGetUrl` de l'élément `<serviceMetadata>`. Notez que si vous spécifiez une adresse absolue, l’URL doit commencer par le schéma `https://` . Si vous spécifiez une adresse relative, vous devez fournir une adresse de base HTTPS pour votre hôte de service. Si cette propriété n'est pas définie, l'adresse par défaut est "" ou directement l'adresse de base HTTPS pour le service.

8. Pour utiliser le comportement avec un service, affectez `behaviorConfiguration` à l’attribut de l' [\<service>](../../configure-apps/file-schema/wcf/service.md) élément la valeur de l’attribut Name de l’élément Behavior. Le code de configuration ci-dessous illustre un exemple complet.

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
- [Comment : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Working with Certificates](working-with-certificates.md)
- [Considérations sur la sécurité des métadonnées](security-considerations-with-metadata.md)
- [Securing Services and Clients](securing-services-and-clients.md)
