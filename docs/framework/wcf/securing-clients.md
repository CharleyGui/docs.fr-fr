---
title: Sécurisation des clients
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: bfb980e629ffb8f8543937a1850430c9bf6e9199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183131"
---
# <a name="securing-clients"></a>Sécurisation des clients
Dans Windows Communication Foundation (WCF), le service dicte les exigences de sécurité pour les clients. Autrement dit, le service spécifie quel mode de sécurité utiliser, et si le client doit fournir ou non une information d'identification. Le processus de la sécurisation d'un client, par conséquent, est simple : utilisez les métadonnées obtenues depuis le service (s'il est publié) et générez un client. Les métadonnées spécifient comment configurer le client. Si le service exige que le client fournisse une information d'identification, vous devez obtenir une information d'identification qui correspond à la spécification. Cette rubrique décrit en détail le processus. Pour plus d’informations sur la création d’un service sécurisé, voir [Securing Services](securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Le service spécifie la sécurité  
 Par défaut, les liaisons WCF ont des fonctionnalités de sécurité activées. (L’exception <xref:System.ServiceModel.BasicHttpBinding>est le .) Par conséquent, si le service a été créé à l’aide de WCF, il y a plus de chances qu’il implémente la sécurité pour assurer l’authentification, la confidentialité et l’intégrité. Dans ce cas, les métadonnées que le service fournit indiqueront ce qu'il faut pour établir un canal de communication sécurisé. Si les métadonnées du service n’incluent pas d’exigences de sécurité, il n’y a aucun moyen d’imposer une méthode de sécurité, telle que SSL (Secure Sockets Layer) sur HTTP, sur un service. Toutefois, si le service exige que le client fournisse une information d'identification, le développeur, le responsable du déploiement ou l'administrateur client doit fournir l'information d'identification réelle que le client utilisera pour s'identifier auprès du service.  
  
## <a name="obtaining-metadata"></a>Obtention des métadonnées  
 Lors de la création d'un client, la première étape est d'obtenir les métadonnées pour le service avec lequel le client communiquera. Cette opération peut être effectuée de deux façons. Tout d’abord, si le service publie un point de terminaison d’échange de métadonnées (MEX) ou rend ses métadonnées disponibles sur HTTP ou HTTPS, vous pouvez télécharger les métadonnées à l’aide [de l’outil utilitaire De métadonnées ServiceModel (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)qui génère à la fois des fichiers de code pour un client ainsi qu’un fichier de configuration. (Pour plus d’informations sur l’utilisation de l’outil, voir [Accéder aux services à l’aide d’un client WCF](accessing-services-using-a-wcf-client.md).) Si le service ne publie pas de point de terminaison MEX et ne met pas non plus ses métadonnées disponibles sur HTTP ou HTTPS, vous devez contacter le créateur du service pour obtenir de la documentation décrivant les exigences de sécurité et les métadonnées.  
  
> [!IMPORTANT]
> Il est recommandé de vérifier que les métadonnées proviennent d'une source fiable et qu'elles n'ont pas été falsifiées. Les métadonnées récupérées à l'aide du protocole HTTP sont envoyées en texte clair et peuvent être falsifiées. Si le service utilise les propriétés <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> et <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>, utilisez l'URL que le créateur du service vous a fournie pour télécharger les données à l'aide du protocole HTTPS.  
  
## <a name="validating-security"></a>Validation de la sécurité  
 Les sources de métadonnées peuvent être divisées en deux catégories principales : les sources fiables et les sources non fiables. Si vous faites confiance à une source et avez téléchargé le code client et d'autres métadonnées depuis le point de terminaison MEX sécurisé de cette source, vous pouvez générer le client, lui fournir les informations d'identification correctes et l'exécuter sans inquiétude.  
  
 Toutefois, si vous choisissez de télécharger un client et des métadonnées à partir d'une source dont vous savez peu de choses, veillez à valider les mesures de sécurité que le code utilise. Par exemple, vous ne devez pas créer un client qui envoie vos informations personnelles ou financières à un service à moins que le service n'exige confidentialité et intégrité (au strict minimum). Vous devez faire confiance au propriétaire du service dans la mesure où vous êtes prêt à divulguer ces informations, parce que ces informations seront visibles pour eux.  
  
 En règle générale, lorsque vous utilisez du code et des métadonnées provenant d'une source non fiable, vérifiez le code et métadonnées pour vous assurer qu'ils répondent au niveau de sécurité exigé.  
  
## <a name="setting-a-client-credential"></a>Définition de l'information d'identification d'un client  
 La définition de l'information d'identification d'un client s'effectue en deux étapes :  
  
1. Déterminer le *type d’identification du client* dont le service a besoin. Pour cela, vous avez le choix entre deux méthodes. En premier lieu, si vous disposez de la documentation du créateur du service, celle-ci doit spécifier le type d'information d'identification du client (le cas échéant) que le service requiert. En second lieu, si vous disposez uniquement d'un fichier de configuration généré par l'outil Svcutil.exe, vous pouvez examiner les liaisons individuelles pour déterminer quel type d'information d'identification est requis.  
  
2. Spécifiez l'information d'identification effective du client. L’identification réelle du client est appelée une *valeur d’identification du client* pour le distinguer du type. Par exemple, si le type d'information d'identification du client spécifie un certificat, vous devez fournir un certificat X.509 publié par une autorité de certification que le service approuve.  
  
### <a name="determining-the-client-credential-type"></a>Détermination du type d'information d'identification du client  
 Si vous avez le fichier de configuration généré par l’outil Svcutil.exe, examinez les [ \<liaisons>](../configure-apps/file-schema/wcf/bindings.md) section pour déterminer quel type d’identification du client est nécessaire. Dans la section, des éléments de liaison spécifient les conditions de sécurité. Plus précisément, \<examinez la sécurité> élément de chaque liaison. Cet élément inclut l'attribut `mode`, auquel vous pouvez affecter l'une de trois valeurs possibles (`Message`, `Transport` ou `TransportWithMessageCredential`). La valeur de l'attribut détermine le mode, et le mode détermine quel élément enfant est significatif.  
  
 L’élément `<security>` peut `<transport>` contenir `<message>` un élément ou un élément, ou les deux. L'élément significatif est celui qui correspond au mode de sécurité. Par exemple, le code suivant spécifie que le mode de sécurité est `"Message"`, et le type d'information d'identification du client pour l'élément `<message>` est `"Certificate"`. Dans ce cas, l'élément `<transport>` peut être ignoré. Toutefois, l'élément `<message>` spécifie qu'un certificat X.509 doit être fourni.  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 Notez que si l'attribut `clientCredentialType` a la valeur `"Windows"`, comme dans l'exemple suivant, vous n'avez pas besoin de fournir une valeur d'information d'identification effective. Cela est dû au fait que la sécurité intégrée de Windows fournit l'information d'identification effective (un jeton Kerberos) de la personne qui exécute le client.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Définition de la valeur d'information d'identification du client  
 S'il est déterminé que le client doit fournir une information d'identification, utilisez la méthode appropriée pour configurer le client. Par exemple, pour définir un certificat client, utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>.  
  
 Le certificat X.509 est une forme courante d'information d'identification. Vous pouvez fournir l'information d'identification de deux manières :  
  
- En la programmant dans votre code client (à l'aide de la méthode `SetCertificate`).  
  
 En ajoutant [ \<](../configure-apps/file-schema/wcf/behaviors.md) un comportement>section du fichier de configuration `clientCredentials` pour le client et en utilisant l’élément (indiqué ci-dessous).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Définir \<un clientCredentials> valeur dans le code  
 Pour définir un <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> [ \<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) valeur dans le code, vous devez accéder à la propriété de la classe. La propriété retourne un objet <xref:System.ServiceModel.Description.ClientCredentials> qui autorise l'accès à différents types d'informations d'identification, comme le montre le tableau suivant.  
  
|Propriété ClientCredential|Description|Notes|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Retourne un <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.|Représente un certificat X.509 fourni par le client pour s'identifier auprès du service.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Retourne un <xref:System.ServiceModel.Security.HttpDigestClientCredential>.|Représente une information d'identification HTTP Digest. L'information d'identification est un hachage du nom d'utilisateur et du mot de passe.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Retourne un <xref:System.ServiceModel.Security.IssuedTokenClientCredential>.|Représente un jeton de sécurité personnalisé publié par un service de jeton de sécurité, utilisé communément dans les scénarios de fédération.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Retourne un <xref:System.ServiceModel.Security.PeerCredential>.|Représente une information d'identification homologue pour la participation à une maille homologue sur un domaine Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Retourne un <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>.|Représente un certificat X.509 fourni par le service dans une négociation hors bande.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Retourne un <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.|Représente une paire nom d'utilisateur/mot de passe.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Retourne un <xref:System.ServiceModel.Security.WindowsClientCredential>.|Représente une information d'identification du client Windows (une information d'identification Kerberos). Les propriétés de la classe sont en lecture seule.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Définir \<un clientCredentials> valeur dans la configuration  
 Les valeurs d’identification sont spécifiées en utilisant un comportement de point de terminaison en tant qu’éléments d’enfant [ \<du clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) élément. L'élément utilisé dépend du type d'information d'identification du client. Par exemple, l’exemple suivant montre la configuration pour définir un certificat X.509 à l’aide du [ \<client <Certificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 Pour définir l’identifiant du client en configuration, ajoutez un [ \<point finalBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) élément au fichier de configuration. En outre, l’élément de comportement ajouté doit être `behaviorConfiguration` lié au critère de terminaison du service en utilisant l’attribut du point de [ \<terminaison> de \<l’élément>client](../configure-apps/file-schema/wcf/endpoint-of-client.md) tel que indiqué dans l’exemple suivant. La valeur de l'attribut `behaviorConfiguration` doit correspondre à la valeur de l'attribut de comportement `name`.  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> Certaines des valeurs d'information d'identification du client ne peuvent pas être définies à l'aide des fichiers de configuration de l'application, par exemple le nom d'utilisateur et le mot de passe, ou les valeurs d'utilisateur et de mot de passe Windows. Ces valeurs d'information d'identification peuvent être spécifiées dans du code uniquement.  
  
 Pour plus d’informations sur la définition de l’identifiant du client, voir [comment : Spécifier les valeurs d’identification des clients](how-to-specify-client-credential-values.md).  
  
> [!NOTE]
> `ClientCredentialType` est ignoré lorsque `SecurityMode` a la valeur `"TransportWithMessageCredential",` comme le montre l'exemple de configuration suivant.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<liaisons>](../configure-apps/file-schema/wcf/bindings.md)
- [Outil Éditeur de configuration (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Sécurisation de services](securing-services.md)
- [Accès aux services à l’aide d’un client WCF](accessing-services-using-a-wcf-client.md)
- [Guide pratique pour spécifier les valeurs d’informations d’identification du client](how-to-specify-client-credential-values.md)
- [Outil Service Model Metadata Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Comment : spécifier le type d'informations d'identification du client](how-to-specify-the-client-credential-type.md)
