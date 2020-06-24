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
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="89bd3-103">Comment : utiliser le fournisseur d'appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="89bd3-103">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="89bd3-104">Le fournisseur d’appartenances ASP.NET est une fonctionnalité qui permet aux développeurs ASP.NET de créer des sites Web permettant aux utilisateurs de créer des combinaisons uniques de nom d’utilisateur et de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="89bd3-104">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="89bd3-105">Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d'un accès exclusif à celui-ci et à ses services.</span><span class="sxs-lookup"><span data-stu-id="89bd3-105">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="89bd3-106">Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="89bd3-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="89bd3-107">Au lieu de cela, tout utilisateur qui fournit ses informations d’identification (combinaison nom d’utilisateur/mot de passe) peut utiliser le site et ses services.</span><span class="sxs-lookup"><span data-stu-id="89bd3-107">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="89bd3-108">Pour obtenir un exemple d’application, consultez [appartenance et fournisseur de rôles](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="89bd3-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="89bd3-109">Pour plus d’informations sur l’utilisation de la fonctionnalité de fournisseur de rôles ASP.NET, consultez [Comment : utiliser le fournisseur de rôles ASP.net avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="89bd3-109">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="89bd3-110">La fonctionnalité d’appartenance requiert l’utilisation d’une base de données SQL Server pour stocker les informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89bd3-110">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="89bd3-111">La fonctionnalité inclut également des méthodes qui consistent à poser une question aux utilisateurs qui ont oublié leur mot de passe.</span><span class="sxs-lookup"><span data-stu-id="89bd3-111">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="89bd3-112">Les développeurs Windows Communication Foundation (WCF) peuvent tirer parti de ces fonctionnalités à des fins de sécurité.</span><span class="sxs-lookup"><span data-stu-id="89bd3-112">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="89bd3-113">Lorsqu’ils sont intégrés à une application WCF, les utilisateurs doivent fournir une combinaison nom d’utilisateur/mot de passe à l’application cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="89bd3-113">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="89bd3-114">Pour transférer les données vers le service WCF, utilisez une liaison qui prend en charge les informations d’identification de nom d’utilisateur/mot de passe, telles que <xref:System.ServiceModel.WSHttpBinding> (dans la configuration, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ) et définissez le type d’informations d’identification du client sur `UserName` .</span><span class="sxs-lookup"><span data-stu-id="89bd3-114">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="89bd3-115">Sur le service, la sécurité WCF authentifie l’utilisateur en fonction du nom d’utilisateur et du mot de passe, et attribue également le rôle spécifié par le rôle ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="89bd3-115">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="89bd3-116">WCF ne fournit pas de méthodes pour remplir la base de données avec des combinaisons nom d’utilisateur/mot de passe ou autres informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89bd3-116">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="89bd3-117">Pour configurer le fournisseur d'appartenances</span><span class="sxs-lookup"><span data-stu-id="89bd3-117">To configure the membership provider</span></span>

1. <span data-ttu-id="89bd3-118">Dans le fichier Web.config, sous l' `system.web` élément <>, créez un <`membership`> élément.</span><span class="sxs-lookup"><span data-stu-id="89bd3-118">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="89bd3-119">Sous l'élément `<membership>`, créez un élément `<providers>`.</span><span class="sxs-lookup"><span data-stu-id="89bd3-119">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="89bd3-120">En tant qu’enfant de l' `providers` élément <>, ajoutez un `<clear />` élément pour vider la collection de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="89bd3-120">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="89bd3-121">Sous l' `<clear />` élément, créez un <`add` élément> avec les attributs suivants définis sur les valeurs appropriées : `name` , `type` ,,,, `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` , `requiresQuestionAndAnswer` , `requiresUniqueEmail` et `passwordFormat` .</span><span class="sxs-lookup"><span data-stu-id="89bd3-121">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="89bd3-122">L'attribut `name` est utilisé ultérieurement comme valeur dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="89bd3-122">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="89bd3-123">L'exemple suivant lui affecte la valeur `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="89bd3-123">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="89bd3-124">L'exemple suivant présente la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="89bd3-124">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="89bd3-125">Pour configurer la sécurité de service afin d'accepter la combinaison nom d'utilisateur/mot de passe</span><span class="sxs-lookup"><span data-stu-id="89bd3-125">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="89bd3-126">Dans le fichier de configuration, sous l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajoutez un [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="89bd3-126">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="89bd3-127">Ajoutez un [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) à la section Bindings.</span><span class="sxs-lookup"><span data-stu-id="89bd3-127">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="89bd3-128">Pour plus d’informations sur la création d’un élément de liaison WCF, consultez [Comment : spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="89bd3-128">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="89bd3-129">Affectez à l'attribut `mode` de l'élément `<security>` la valeur `Message`.</span><span class="sxs-lookup"><span data-stu-id="89bd3-129">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="89bd3-130">Affectez `clientCredentialType` à l’attribut de l’élément <> la valeur `message` `UserName` .</span><span class="sxs-lookup"><span data-stu-id="89bd3-130">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="89bd3-131">Cela spécifie qu'une paire nom d'utilisateur/mot de passe sera utilisée comme information d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="89bd3-131">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="89bd3-132">L’exemple suivant présente le code de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="89bd3-132">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="89bd3-133">Pour configurer un service permettant d'utiliser le fournisseur d'appartenances</span><span class="sxs-lookup"><span data-stu-id="89bd3-133">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="89bd3-134">En tant qu’enfant de l' `<system.serviceModel>` élément, ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément</span><span class="sxs-lookup"><span data-stu-id="89bd3-134">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="89bd3-135">Ajoutez un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' `behaviors` élément <>.</span><span class="sxs-lookup"><span data-stu-id="89bd3-135">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="89bd3-136">Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) et affectez `name` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="89bd3-136">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="89bd3-137">Ajoutez un [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) à l' `behavior` élément <>.</span><span class="sxs-lookup"><span data-stu-id="89bd3-137">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="89bd3-138">Ajoutez un [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) à l' `<serviceCredentials>` élément.</span><span class="sxs-lookup"><span data-stu-id="89bd3-138">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="89bd3-139">Affectez à l'attribut `userNamePasswordValidationMode` la valeur `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="89bd3-139">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="89bd3-140">Si la `userNamePasswordValidationMode` valeur n’est pas définie, WCF utilise l’authentification Windows au lieu du fournisseur d’appartenances ASP.net.</span><span class="sxs-lookup"><span data-stu-id="89bd3-140">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="89bd3-141">Affectez à l'attribut `membershipProviderName` le nom du fournisseur (spécifié lors de l'ajout du fournisseur dans la première procédure de cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="89bd3-141">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="89bd3-142">L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.</span><span class="sxs-lookup"><span data-stu-id="89bd3-142">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="89bd3-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="89bd3-143">Example</span></span>

<span data-ttu-id="89bd3-144">Le code suivant montre la configuration d’un service qui utilise la fonctionnalité d’appartenance ASP.</span><span class="sxs-lookup"><span data-stu-id="89bd3-144">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="89bd3-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89bd3-145">See also</span></span>

- [<span data-ttu-id="89bd3-146">Comment : utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="89bd3-146">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="89bd3-147">Membership and Role Provider</span><span class="sxs-lookup"><span data-stu-id="89bd3-147">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
