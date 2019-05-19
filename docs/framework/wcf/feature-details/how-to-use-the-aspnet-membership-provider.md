---
title: 'Procédure : utiliser le fournisseur d’appartenances ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 61324bbc5ea07dd19e23589bfc90f9ea44a6b331
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880186"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="7ef36-102">Procédure : utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7ef36-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="7ef36-103">Le fournisseur d’appartenances ASP.NET est une fonctionnalité qui permet aux développeurs ASP.NET créer des sites Web qui permettent aux utilisateurs de créer des combinaisons nom et mot de passe utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="7ef36-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="7ef36-104">Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d'un accès exclusif à celui-ci et à ses services.</span><span class="sxs-lookup"><span data-stu-id="7ef36-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="7ef36-105">Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="7ef36-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="7ef36-106">Au lieu de cela, l'utilisateur qui fournit ses informations d'identification (combinaison nom d'utilisateur/mot de passe) peut utiliser le site et ses services.</span><span class="sxs-lookup"><span data-stu-id="7ef36-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="7ef36-107">Pour un exemple d’application, consultez [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="7ef36-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="7ef36-108">Pour plus d’informations sur l’utilisation de la fonctionnalité de fournisseur de rôle ASP.NET, consultez [Comment : Utiliser le fournisseur de rôle ASP.NET avec un Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="7ef36-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="7ef36-109">La fonctionnalité d’appartenance requiert l’utilisation d’une base de données SQL Server pour stocker les informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7ef36-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="7ef36-110">La fonctionnalité inclut également des méthodes qui consistent à poser une question aux utilisateurs qui ont oublié leur mot de passe.</span><span class="sxs-lookup"><span data-stu-id="7ef36-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="7ef36-111">Les développeurs de Windows Communication Foundation (WCF) peuvent tirer parti de ces fonctionnalités pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7ef36-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="7ef36-112">Lorsqu’ils sont intégrés dans une application WCF, les utilisateurs doivent fournir une combinaison nom/mot de passe d’utilisateur à l’application de client WCF.</span><span class="sxs-lookup"><span data-stu-id="7ef36-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="7ef36-113">Pour transférer les données au service WCF, utilisez une liaison qui prend en charge les informations d’identification de nom/mot de passe utilisateur, telles que la <xref:System.ServiceModel.WSHttpBinding> (dans la configuration, le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) et définir le type d’informations d’identification à client`UserName`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="7ef36-114">Sur le service, sécurité WCF s’authentifie l’utilisateur en fonction du nom d’utilisateur et le mot de passe et affecte également le rôle spécifié par le rôle ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7ef36-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ef36-115">WCF ne fournit pas de méthodes pour remplir la base de données avec des combinaisons nom/mot de passe d’utilisateur ou d’autres informations de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7ef36-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="7ef36-116">Pour configurer le fournisseur d'appartenances</span><span class="sxs-lookup"><span data-stu-id="7ef36-116">To configure the membership provider</span></span>  
  
1. <span data-ttu-id="7ef36-117">Dans le fichier Web.config, sous le <`system.web`> élément, créer un <`membership`> élément.</span><span class="sxs-lookup"><span data-stu-id="7ef36-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2. <span data-ttu-id="7ef36-118">Sous l'élément `<membership>`, créez un élément `<providers>`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3. <span data-ttu-id="7ef36-119">En tant qu’enfant à la <`providers`> élément, ajoutez un `<clear />` élément pour vider la collection de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="7ef36-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4. <span data-ttu-id="7ef36-120">Sous le `<clear />` élément, créer un <`add`> élément avec les attributs suivants définis aux valeurs appropriées : `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, et `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="7ef36-121">L'attribut `name` est utilisé ultérieurement comme valeur dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7ef36-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="7ef36-122">L'exemple suivant lui affecte la valeur `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="7ef36-123">L'exemple suivant présente la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="7ef36-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="7ef36-124">Pour configurer la sécurité de service afin d'accepter la combinaison nom d'utilisateur/mot de passe</span><span class="sxs-lookup"><span data-stu-id="7ef36-124">To configure service security to accept the user name/password combination</span></span>  
  
1. <span data-ttu-id="7ef36-125">Dans le fichier de configuration, sous le [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajoutez un [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="7ef36-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2. <span data-ttu-id="7ef36-126">Ajouter un [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à la section des liaisons.</span><span class="sxs-lookup"><span data-stu-id="7ef36-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="7ef36-127">Pour plus d’informations sur la création d’un élément de liaison WCF, consultez [Comment : Spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7ef36-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3. <span data-ttu-id="7ef36-128">Affectez à l'attribut `mode` de l'élément `<security>` la valeur `Message`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4. <span data-ttu-id="7ef36-129">Définir le `clientCredentialType` attribut de la <`message`> élément à `UserName`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="7ef36-130">Cela spécifie qu'une paire nom d'utilisateur/mot de passe sera utilisée comme information d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="7ef36-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="7ef36-131">L’exemple suivant présente le code de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="7ef36-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="7ef36-132">Pour configurer un service permettant d'utiliser le fournisseur d'appartenances</span><span class="sxs-lookup"><span data-stu-id="7ef36-132">To configure a service to use the membership provider</span></span>  
  
1. <span data-ttu-id="7ef36-133">En tant qu’enfant à la `<system.serviceModel>` élément, ajoutez un [ \<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément</span><span class="sxs-lookup"><span data-stu-id="7ef36-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2. <span data-ttu-id="7ef36-134">Ajouter un [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à la <`behaviors`> élément.</span><span class="sxs-lookup"><span data-stu-id="7ef36-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3. <span data-ttu-id="7ef36-135">Ajouter un [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) et définir le `name` attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="7ef36-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="7ef36-136">Ajouter un [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à la <`behavior`> élément.</span><span class="sxs-lookup"><span data-stu-id="7ef36-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5. <span data-ttu-id="7ef36-137">Ajouter un [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à la `<serviceCredentials>` élément.</span><span class="sxs-lookup"><span data-stu-id="7ef36-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6. <span data-ttu-id="7ef36-138">Affectez à l'attribut `userNamePasswordValidationMode` la valeur `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="7ef36-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7ef36-139">Si le `userNamePasswordValidationMode` valeur n’est pas définie, WCF utilise l’authentification Windows plutôt que le fournisseur d’appartenances ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7ef36-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>  
  
7. <span data-ttu-id="7ef36-140">Affectez à l'attribut `membershipProviderName` le nom du fournisseur (spécifié lors de l'ajout du fournisseur dans la première procédure de cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="7ef36-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="7ef36-141">L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.</span><span class="sxs-lookup"><span data-stu-id="7ef36-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7ef36-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ef36-142">Example</span></span>  
 <span data-ttu-id="7ef36-143">Le code suivant montre la configuration d’un service qui utilise la fonctionnalité d’appartenance ASP.</span><span class="sxs-lookup"><span data-stu-id="7ef36-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ef36-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ef36-144">See also</span></span>

- [<span data-ttu-id="7ef36-145">Guide pratique pour Utiliser le fournisseur de rôle ASP.NET avec un Service</span><span class="sxs-lookup"><span data-stu-id="7ef36-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="7ef36-146">Fournisseur d’appartenances et de rôles</span><span class="sxs-lookup"><span data-stu-id="7ef36-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
