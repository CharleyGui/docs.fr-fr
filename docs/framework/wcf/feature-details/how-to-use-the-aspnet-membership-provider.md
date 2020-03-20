---
title: "Comment : utiliser le fournisseur d'appartenances ASP.NET"
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184793"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Comment : utiliser le fournisseur d'appartenances ASP.NET

Le fournisseur d’adhésion ASP.NET est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web qui permettent aux utilisateurs de créer des combinaisons uniques de noms d’utilisateur et de mots de passe. Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d'un accès exclusif à celui-ci et à ses services. Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows. Au lieu de cela, tout utilisateur qui fournit ses informations d’identification (le nom d’utilisateur / combinaison mot de passe) peut utiliser le site et ses services.

Pour une demande d’exemple, voir [Adhésion et Fournisseur de rôle](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Pour plus d’informations sur l’utilisation de la fonction ASP.NET fournisseur de rôles, voir [comment : Utilisez le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).

La fonctionnalité d’appartenance requiert l’utilisation d’une base de données SQL Server pour stocker les informations utilisateur. La fonctionnalité inclut également des méthodes qui consistent à poser une question aux utilisateurs qui ont oublié leur mot de passe.

Les développeurs de la Windows Communication Foundation (WCF) peuvent profiter de ces fonctionnalités à des fins de sécurité. Lorsqu’ils sont intégrés dans une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application client WCF. Pour transférer les données au service WCF, utilisez une liaison qui prend <xref:System.ServiceModel.WSHttpBinding> en charge les informations d’identification du nom d’utilisateur/mot de `UserName`passe, telles que la (en configuration, le [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) et définissez le type d’identification du client à . Sur le service, la sécurité WCF authentifie l’utilisateur en fonction du nom d’utilisateur et du mot de passe, et attribue également le rôle spécifié par le rôle ASP.NET.

> [!NOTE]
> WCF ne fournit pas de méthodes pour remplir la base de données avec des combinaisons nom d’utilisateur/mot de passe ou d’autres informations utilisateur.

### <a name="to-configure-the-membership-provider"></a>Pour configurer le fournisseur d'appartenances

1. Dans le fichier Web.config, sous `system.web` l’élément> <, créez `membership` un élément <>.

2. Sous l'élément `<membership>`, créez un élément `<providers>`.

3. Comme un enfant à `providers` la <> élément, `<clear />` ajouter un élément pour rincer la collecte des fournisseurs.

4. Sous `<clear />` l’élément, créer un `add` <> élément avec les attributs suivants `name` `type`définis à des valeurs `passwordFormat`appropriées: , , , `connectionStringName` `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset` `requiresQuestionAndAnswer`, , `requiresUniqueEmail`, et . L'attribut `name` est utilisé ultérieurement comme valeur dans le fichier de configuration. L'exemple suivant lui affecte la valeur `SqlMembershipProvider`.

    L'exemple suivant présente la section de configuration.

    ```xml
    <!-- Configure the Sql Membership Provider -->
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">
      <providers>
        <clear />
          <add
            name="SqlMembershipProvider"
            type="System.Web.Security.SqlMembershipProvider"
            connectionStringName="SqlConn"
            applicationName="MembershipAndRoleProviderSample"
            enablePasswordRetrieval="false"
            enablePasswordReset="false"
            requiresQuestionAndAnswer="false"
            requiresUniqueEmail="true"
            passwordFormat="Hashed" />
      </providers>
    </membership>
    ```

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Pour configurer la sécurité de service afin d'accepter la combinaison nom d'utilisateur/mot de passe

1. Dans le fichier de configuration, sous l’élément [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) ajoutez une [ \<fixation>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.

2. Ajoutez un [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à la section des fixations. Pour plus d’informations sur la création d’un élément de liaison WCF, voir [Comment : Spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

3. Affectez à l'attribut `mode` de l'élément `<security>` la valeur `Message`.

4. Définissez `clientCredentialType` l’attribut de `message` l’élément <`UserName`> à . Cela spécifie qu'une paire nom d'utilisateur/mot de passe sera utilisée comme information d'identification du client.

    L’exemple suivant présente le code de configuration de la liaison.

    ```xml
    <system.serviceModel>
    <bindings>
      <wsHttpBinding>
      <!-- Set up a binding that uses UserName as the client credential type -->
        <binding name="MembershipBinding">
          <security mode ="Message">
            <message clientCredentialType ="UserName"/>
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    </system.serviceModel>
    ```

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Pour configurer un service permettant d'utiliser le fournisseur d'appartenances

1. Comme un enfant `<system.serviceModel>` à l’élément, ajouter un [ \<comportement>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément

2. Ajouter un [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l’élément `behaviors` <>.

3. Ajoutez [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) un comportement>et `name` définissez l’attribut à une valeur appropriée.

4. Ajoutez un [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à l’élément `behavior`> <.

5. Ajoutez un [ \<utilisateurNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à `<serviceCredentials>` l’élément.

6. Affectez à l'attribut `userNamePasswordValidationMode` la valeur `MembershipProvider`.

    > [!IMPORTANT]
    > Si `userNamePasswordValidationMode` la valeur n’est pas définie, WCF utilise l’authentification Windows au lieu du fournisseur d’adhésion ASP.NET.

7. Affectez à l'attribut `membershipProviderName` le nom du fournisseur (spécifié lors de l'ajout du fournisseur dans la première procédure de cette rubrique). L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.

    ```xml
    <behaviors>
       <serviceBehaviors>
          <behavior name="MyServiceBehavior">
             <serviceCredentials>
                <userNameAuthentication
                userNamePasswordValidationMode="MembershipProvider"
                membershipProviderName="SqlMembershipProvider" />
             </serviceCredentials>
          </behavior>
       </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a> Exemple

Le code suivant montre la configuration d’un service qui utilise la fonctionnalité d’appartenance ASP.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">
        <endpoint address="http://microsoft.com/WCFservices/Calculator"
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="MyServiceBehavior">
          <serviceCredentials>
            <userNameAuthentication
              userNamePasswordValidationMode="MembershipProvider"
              membershipProviderName="SqlMembershipProvider" />
          </serviceCredentials>
        </behavior>
          </serviceBehaviors>
    </behaviors>
    <bindings>
      <wsHttpBinding>
        <binding name="MembershipBinding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Fournisseur d’appartenances et de rôles](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
