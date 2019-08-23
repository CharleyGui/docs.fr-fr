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
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="40342-102">Procédure : utiliser un validateur de nom d’utilisateur et mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="40342-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="40342-103">Par défaut, lorsqu’un nom d’utilisateur et un mot de passe sont utilisés pour l’authentification, Windows Communication Foundation (WCF) utilise Windows pour valider le nom d’utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="40342-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="40342-104">Toutefois, WCF autorise les schémas d’authentification de mot de passe et de nom d'utilisateur personnalisés, également appelés validateurs.</span><span class="sxs-lookup"><span data-stu-id="40342-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="40342-105">Pour incorporer un validateur de nom d'utilisateur et de mot de passe personnalisé, créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, puis configurez-la.</span><span class="sxs-lookup"><span data-stu-id="40342-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="40342-106">Pour obtenir un exemple d’application, consultez [validateur de mot de passe de nom d’utilisateur](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="40342-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="40342-107">Pour créer validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="40342-107">To create a custom user name and password validator</span></span>  
  
1. <span data-ttu-id="40342-108">Créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="40342-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. <span data-ttu-id="40342-109">Implémentez le schéma d'authentification personnalisé en substituant la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="40342-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="40342-110">N'utilisez pas le code dans l'exemple suivant qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="40342-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="40342-111">Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="40342-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="40342-112">Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="40342-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="40342-113">Pour configurer un service pour utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="40342-113">To configure a service to use a custom user name and password validator</span></span>  
  
1. <span data-ttu-id="40342-114">Configurez une liaison qui utilise la sécurité de message sur un transport ou la sécurité au niveau du transport sur HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="40342-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="40342-115">Lorsque vous utilisez la sécurité de message, ajoutez l’une des liaisons fournies par le système, telles qu’un [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou un [ \<> CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) qui prend en `UserName` charge la sécurité de message et le type d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="40342-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="40342-116">Lorsque vous utilisez la sécurité au niveau du transport sur http (S), ajoutez la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), un [ \<> NetTcpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou un [ \<> CustomBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)qui utilise http (S) et le `Basic` schéma d’authentification.</span><span class="sxs-lookup"><span data-stu-id="40342-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="40342-117">Lors de l'utilisation du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou une version ultérieure, vous pouvez utiliser un validateur personnalisé de mot de passe et de nom d'utilisateur avec la sécurité de transport et de message.</span><span class="sxs-lookup"><span data-stu-id="40342-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="40342-118">Avec WinFX, un validateur personnalisé de nom d’utilisateur et de mot de passe ne peut être utilisé qu’avec la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="40342-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="40342-119">Pour plus d’informations sur \<l’utilisation de > NetTcpBinding dans ce contexte, consultez [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="40342-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1. <span data-ttu-id="40342-120">Dans le fichier de configuration, sous l' [ \<élément System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , ajoutez une [ \<liaison >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="40342-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2. <span data-ttu-id="40342-121">Ajoutez un [ \<élément WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) à la section Bindings.</span><span class="sxs-lookup"><span data-stu-id="40342-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="40342-122">Pour plus d’informations sur la création d’un élément de [liaison WCF, consultez Procédure: Spécifiez une liaison de service](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="40342-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3. <span data-ttu-id="40342-123">Affectez `mode` à [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Transport` `TransportWithMessageCredential` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) l’attribut de la > de sécurité ou > de sécurité la valeur, ou. `Message`</span><span class="sxs-lookup"><span data-stu-id="40342-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
    4. <span data-ttu-id="40342-124">Définissez l' `clientCredentialType` attribut [ \<du > de message](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<du > de transport](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="40342-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="40342-125">Lorsque vous utilisez la sécurité `clientCredentialType` `UserName` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) de message, affectez à l’attribut du message > la valeur.</span><span class="sxs-lookup"><span data-stu-id="40342-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="40342-126">Lorsque vous utilisez la sécurité au niveau du transport sur http (S) `clientCredentialType` , définissez l’attribut [ \<du > de transport](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou `Basic` [ \<du > de transport](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) sur.</span><span class="sxs-lookup"><span data-stu-id="40342-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="40342-127">Lorsqu’un service WCF est hébergé dans Internet Information Services (IIS) à l’aide de la sécurité au <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> niveau du transport et <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>que la propriété a la valeur, le schéma d’authentification personnalisé utilise un sous-ensemble de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="40342-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="40342-128">En effet, dans ce scénario, IIS effectue l’authentification Windows avant WCF appelant l’authentificateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="40342-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>  
  
     <span data-ttu-id="40342-129">Pour plus d’informations sur la création d’un élément de [liaison WCF, consultez Procédure: Spécifiez une liaison de service](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="40342-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="40342-130">L’exemple suivant présente le code de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="40342-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2. <span data-ttu-id="40342-131">Configurez un comportement qui spécifie qu'un validateur de nom d'utilisateur et de mot de passe personnalisé est utilisé pour valider des paires nom d'utilisateur/mot de passe pour les jetons de sécurité <xref:System.IdentityModel.Tokens.UserNameSecurityToken> entrants.</span><span class="sxs-lookup"><span data-stu-id="40342-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1. <span data-ttu-id="40342-132">En tant qu’enfant de l' [ \<élément System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , ajoutez un [ \<élément comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="40342-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2. <span data-ttu-id="40342-133">Ajoutez un [ \<> serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l' [ \<élément comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="40342-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3. <span data-ttu-id="40342-134">Ajoutez un [ \<élément de comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) et affectez à l' `name` attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="40342-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4. <span data-ttu-id="40342-135">Ajoutez un [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à l' [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément de > de comportement.</span><span class="sxs-lookup"><span data-stu-id="40342-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5. <span data-ttu-id="40342-136">Ajoutez un [ \<> UserNameAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à la [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="40342-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6. <span data-ttu-id="40342-137">Affectez `userNamePasswordValidationMode` à `Custom`.</span><span class="sxs-lookup"><span data-stu-id="40342-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="40342-138">Si la `userNamePasswordValidationMode` valeur n’est pas définie, WCF utilise l’authentification Windows au lieu du validateur de nom d’utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="40342-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7. <span data-ttu-id="40342-139">Affectez au `customUserNamePasswordValidatorType` le type qui représente votre validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="40342-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="40342-140">L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.</span><span class="sxs-lookup"><span data-stu-id="40342-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="40342-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="40342-141">Example</span></span>  
 <span data-ttu-id="40342-142">L'exemple de code suivant montre comment créer un validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="40342-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="40342-143">N'utilisez pas le code qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="40342-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="40342-144">Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="40342-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="40342-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40342-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="40342-146">Guide pratique : Utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="40342-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="40342-147">Authentification</span><span class="sxs-lookup"><span data-stu-id="40342-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
