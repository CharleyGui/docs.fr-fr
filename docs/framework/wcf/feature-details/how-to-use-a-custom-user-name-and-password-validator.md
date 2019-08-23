---
title: 'Procédure : utiliser un validateur de nom d’utilisateur et mot de passe personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 57bd650caef831f3ee886c0422e13cc4149d3416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968806"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Procédure : utiliser un validateur de nom d’utilisateur et mot de passe personnalisé
Par défaut, lorsqu’un nom d’utilisateur et un mot de passe sont utilisés pour l’authentification, Windows Communication Foundation (WCF) utilise Windows pour valider le nom d’utilisateur et le mot de passe. Toutefois, WCF autorise les schémas d’authentification de mot de passe et de nom d'utilisateur personnalisés, également appelés validateurs. Pour incorporer un validateur de nom d'utilisateur et de mot de passe personnalisé, créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, puis configurez-la.  
  
 Pour obtenir un exemple d’application, consultez [validateur de mot de passe de nom d’utilisateur](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Pour créer validateur de nom d'utilisateur et de mot de passe personnalisé  
  
1. Créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. Implémentez le schéma d'authentification personnalisé en substituant la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
     N'utilisez pas le code dans l'exemple suivant qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production. Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.  
  
     Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Pour configurer un service pour utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé  
  
1. Configurez une liaison qui utilise la sécurité de message sur un transport ou la sécurité au niveau du transport sur HTTP(S)  
  
     Lorsque vous utilisez la sécurité de message, ajoutez l’une des liaisons fournies par le système, telles qu’un [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou un [ \<> CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) qui prend en `UserName` charge la sécurité de message et le type d’informations d’identification.  
  
     Lorsque vous utilisez la sécurité au niveau du transport sur http (S), ajoutez la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), un [ \<> NetTcpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou un [ \<> CustomBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)qui utilise http (S) et le `Basic` schéma d’authentification.  
  
    > [!NOTE]
    > Lors de l'utilisation du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou une version ultérieure, vous pouvez utiliser un validateur personnalisé de mot de passe et de nom d'utilisateur avec la sécurité de transport et de message. Avec WinFX, un validateur personnalisé de nom d’utilisateur et de mot de passe ne peut être utilisé qu’avec la sécurité de message.  
  
    > [!TIP]
    >  Pour plus d’informations sur \<l’utilisation de > NetTcpBinding dans ce contexte, consultez [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1. Dans le fichier de configuration, sous l' [ \<élément System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , ajoutez une [ \<liaison >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.  
  
    2. Ajoutez un [ \<élément WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) à la section Bindings. Pour plus d’informations sur la création d’un élément de [liaison WCF, consultez Procédure: Spécifiez une liaison de service](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)dans la configuration.  
  
    3. Affectez `mode` à [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Transport` `TransportWithMessageCredential` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) l’attribut de la > de sécurité ou > de sécurité la valeur, ou. `Message`  
  
    4. Définissez l' `clientCredentialType` attribut [ \<du > de message](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<du > de transport](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Lorsque vous utilisez la sécurité `clientCredentialType` `UserName` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) de message, affectez à l’attribut du message > la valeur.  
  
         Lorsque vous utilisez la sécurité au niveau du transport sur http (S) `clientCredentialType` , définissez l’attribut [ \<du > de transport](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou `Basic` [ \<du > de transport](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) sur.  
  
        > [!NOTE]
        >  Lorsqu’un service WCF est hébergé dans Internet Information Services (IIS) à l’aide de la sécurité au <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> niveau du transport et <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>que la propriété a la valeur, le schéma d’authentification personnalisé utilise un sous-ensemble de l’authentification Windows. En effet, dans ce scénario, IIS effectue l’authentification Windows avant WCF appelant l’authentificateur personnalisé.  
  
     Pour plus d’informations sur la création d’un élément de [liaison WCF, consultez Procédure: Spécifiez une liaison de service](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)dans la configuration.  
  
     L’exemple suivant présente le code de configuration de la liaison.  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2. Configurez un comportement qui spécifie qu'un validateur de nom d'utilisateur et de mot de passe personnalisé est utilisé pour valider des paires nom d'utilisateur/mot de passe pour les jetons de sécurité <xref:System.IdentityModel.Tokens.UserNameSecurityToken> entrants.  
  
    1. En tant qu’enfant de l' [ \<élément System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , ajoutez un [ \<élément comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .  
  
    2. Ajoutez un [ \<> serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l' [ \<élément comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .  
  
    3. Ajoutez un [ \<élément de comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) et affectez à l' `name` attribut une valeur appropriée.  
  
    4. Ajoutez un [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à l' [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément de > de comportement.  
  
    5. Ajoutez un [ \<> UserNameAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à la [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6. Affectez `userNamePasswordValidationMode` à `Custom`.  
  
        > [!IMPORTANT]
        >  Si la `userNamePasswordValidationMode` valeur n’est pas définie, WCF utilise l’authentification Windows au lieu du validateur de nom d’utilisateur et de mot de passe personnalisé.  
  
    7. Affectez au `customUserNamePasswordValidatorType` le type qui représente votre validateur de nom d'utilisateur et de mot de passe personnalisé.  
  
     L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Exemples  
 L'exemple de code suivant montre comment créer un validateur de nom d'utilisateur et de mot de passe personnalisé. N'utilisez pas le code qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production. Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Guide pratique : Utiliser le fournisseur d’appartenances ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Authentification](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
