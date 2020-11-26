---
title: 'Procédure : créer un service qui utilise un validateur de certificat personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 31918ca2d96b63911130d22476a6e5a6d48999ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249239"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Procédure : créer un service qui utilise un validateur de certificat personnalisé

Cette rubrique décrit comment implémenter un validateur de certificat personnalisé et comment configurer les informations d’identification du service ou du client pour remplacer la logique de validation de certificat par défaut par le validateur de certificat personnalisé.  
  
 Si le certificat X. 509 est utilisé pour authentifier un client ou un service, Windows Communication Foundation (WCF) utilise par défaut le magasin de certificats Windows et l’API de chiffrement pour valider le certificat et s’assurer qu’il est approuvé. Les fonctionnalités intégrées de validation du certificat sont parfois insuffisantes et doivent être changées. WCF offre un moyen simple de modifier la logique de validation en permettant aux utilisateurs d’ajouter un validateur de certificat personnalisé. Si un validateur de certificat personnalisé est spécifié, WCF n’utilise pas la logique intégrée de validation de certificat, mais s’appuie sur le validateur personnalisé à la place.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Pour créer un validateur de certificat personnalisé  
  
1. Définissez une nouvelle classe dérivée de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2. Implémentez la méthode abstraite <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>. Le certificat qui doit être validé est passé sous la forme d’un argument à la méthode. Si le certificat passé n’est pas valide selon la logique de validation, cette méthode lève une <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Si le certificat est valide, la méthode est retournée à l'appelant.  
  
    > [!NOTE]
    > Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Pour spécifier un validateur de certificat personnalisé dans la configuration du service  
  
1. Ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément et un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément.  
  
2. Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) et affectez `name` à l’attribut une valeur appropriée.  
  
3. Ajoutez un [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) à l' `<behavior>` élément.  
  
4. Ajoutez un élément `<clientCertificate>` à l'élément `<serviceCredentials>`.  
  
5. Ajoutez un [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) à l' `<clientCertificate>` élément.  
  
6. Affectez à l'attribut `customCertificateValidatorType` le type de validateur. L'exemple suivant affecte à l'attribut l'espace de noms et le nom du type.  
  
7. Affectez à l'attribut `certificateValidationMode` la valeur `Custom`.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Pour spécifier un validateur de certificat personnalisé à l'aide de la configuration sur le client  
  
1. Ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément et un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément.  
  
2. Ajoutez un [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) élément.  
  
3. Ajoutez un élément `<behavior>`, puis affectez à l'attribut `name` une valeur appropriée.  
  
4. Ajoutez un [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) élément.  
  
5. Ajoutez un [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
6. Ajoutez un [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) comme indiqué dans l’exemple suivant.  
  
7. Affectez à l'attribut `customCertificateValidatorType` le type de validateur.  
  
8. Affectez à l'attribut `certificateValidationMode` la valeur `Custom`. L'exemple suivant affecte à l'attribut l'espace de noms et le nom du type.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Pour spécifier un validateur de certificat personnalisé à l'aide du code sur le service  
  
1. Spécifiez le validateur de certificat personnalisé sur la propriété <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>. Vous pouvez accéder aux informations d'identification de service à l'aide de la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.  
  
2. Affectez à la propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Pour spécifier un validateur de certificat personnalisé à l'aide du code sur le client  
  
1. Spécifiez le validateur de certificat personnalisé à l'aide de la propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A>. Vous pouvez accéder aux informations d'identification du client à l'aide de la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>. (La classe de client générée par l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) dérive toujours de la <xref:System.ServiceModel.ClientBase%601> classe.)  
  
2. Affectez à la propriété <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a> Exemple  
  
### <a name="description"></a>Description  

 L'exemple suivant montre une implémentation d'un validateur de certificat personnalisé et son utilisation sur le service.  
  
### <a name="code"></a>Code  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
