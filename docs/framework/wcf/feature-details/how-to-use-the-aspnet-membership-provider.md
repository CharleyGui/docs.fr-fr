---
title: "Comment : utiliser le fournisseur d'appartenances ASP.NET"
description: Découvrez comment le fournisseur d’appartenances ASP.NET prend en charge les sites Web qui permettent aux utilisateurs de créer un nom d’utilisateur et un mot de passe pour l’accès sans disposer d’un compte de domaine Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246725"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Comment : utiliser le fournisseur d'appartenances ASP.NET

Le fournisseur d’appartenances ASP.NET est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web permettant aux utilisateurs de créer des combinaisons uniques de nom d’utilisateur et de mot de passe. Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d'un accès exclusif à celui-ci et à ses services. Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows. Au lieu de cela, tout utilisateur qui fournit ses informations d’identification (combinaison nom d’utilisateur/mot de passe) peut utiliser le site et ses services.

Pour obtenir un exemple d’application, consultez [appartenance et fournisseur de rôles](../samples/membership-and-role-provider.md). Pour plus d’informations sur l’utilisation de la fonctionnalité de fournisseur de rôles ASP.NET, consultez [Comment : utiliser le fournisseur de rôles ASP.net avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md).

La fonctionnalité d’appartenance requiert l’utilisation d’une base de données SQL Server pour stocker les informations utilisateur. La fonctionnalité inclut également des méthodes qui consistent à poser une question aux utilisateurs qui ont oublié leur mot de passe.

Les développeurs Windows Communication Foundation (WCF) peuvent tirer parti de ces fonctionnalités à des fins de sécurité. Lorsqu’ils sont intégrés à une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application cliente WCF. Pour transférer les données vers le service WCF, utilisez une liaison qui prend en charge les informations d’identification de nom d’utilisateur/mot de passe, telles que <xref:System.ServiceModel.WSHttpBinding> (dans la configuration, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ) et définissez le type d’informations d’identification du client sur `UserName` . Sur le service, la sécurité WCF authentifie l’utilisateur en fonction du nom d’utilisateur et du mot de passe, et attribue également le rôle spécifié par le rôle ASP.NET.

> [!NOTE]
> WCF ne fournit pas de méthodes pour remplir la base de données avec des combinaisons nom d’utilisateur/mot de passe ou autres informations utilisateur.

### <a name="to-configure-the-membership-provider"></a>Pour configurer le fournisseur d'appartenances

1. Dans le fichier Web.config, sous l' `system.web` élément <>, créez un <`membership`> élément.

2. Sous l'élément `<membership>`, créez un élément `<providers>`.

3. En tant qu’enfant de l' `providers` élément <>, ajoutez un `<clear />` élément pour vider la collection de fournisseurs.

4. Sous l' `<clear />` élément, créez un <`add` élément> avec les attributs suivants définis sur les valeurs appropriées : `name` , `type` ,,,, `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` , `requiresQuestionAndAnswer` , `requiresUniqueEmail` et `passwordFormat` . L'attribut `name` est utilisé ultérieurement comme valeur dans le fichier de configuration. L'exemple suivant lui affecte la valeur `SqlMembershipProvider`.

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

1. Dans le fichier de configuration, sous l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajoutez un [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) élément.

2. Ajoutez un [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) à la section Bindings. Pour plus d’informations sur la création d’un élément de liaison WCF, consultez [Comment : spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md).

3. Affectez à l'attribut `mode` de l'élément `<security>` la valeur `Message`.

4. Affectez `clientCredentialType` à l’attribut de l’élément <> la valeur `message` `UserName` . Cela spécifie qu'une paire nom d'utilisateur/mot de passe sera utilisée comme information d'identification du client.

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

1. En tant qu’enfant de l' `<system.serviceModel>` élément, ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément

2. Ajoutez un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' `behaviors` élément <>.

3. Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) et affectez `name` à l’attribut une valeur appropriée.

4. Ajoutez un [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) à l' `behavior` élément <>.

5. Ajoutez un [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) à l' `<serviceCredentials>` élément.

6. Affectez à l'attribut `userNamePasswordValidationMode` la valeur `MembershipProvider`.

    > [!IMPORTANT]
    > Si la `userNamePasswordValidationMode` valeur n’est pas définie, WCF utilise l’authentification Windows au lieu du fournisseur d’appartenances ASP.net.

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

## <a name="example"></a>Exemple

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

- [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Membership and Role Provider](../samples/membership-and-role-provider.md)
