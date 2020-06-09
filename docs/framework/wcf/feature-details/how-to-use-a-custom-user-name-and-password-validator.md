---
title: "Comment : utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601177"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="96b2d-102">Comment : utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="96b2d-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="96b2d-103">Par défaut, lorsqu’un nom d’utilisateur et un mot de passe sont utilisés pour l’authentification, Windows Communication Foundation (WCF) utilise Windows pour valider le nom d’utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="96b2d-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="96b2d-104">Toutefois, WCF autorise les schémas d’authentification de mot de passe et de nom d’utilisateur personnalisés, également appelés *validateurs*.</span><span class="sxs-lookup"><span data-stu-id="96b2d-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="96b2d-105">Pour incorporer un validateur de nom d'utilisateur et de mot de passe personnalisé, créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, puis configurez-la.</span><span class="sxs-lookup"><span data-stu-id="96b2d-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="96b2d-106">Pour obtenir un exemple d’application, consultez [validateur de mot de passe de nom d’utilisateur](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="96b2d-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="96b2d-107">Pour créer validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="96b2d-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="96b2d-108">Créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="96b2d-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="96b2d-109">Implémentez le schéma d'authentification personnalisé en substituant la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="96b2d-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="96b2d-110">N'utilisez pas le code dans l'exemple suivant qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="96b2d-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="96b2d-111">Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="96b2d-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="96b2d-112">Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="96b2d-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="96b2d-113">Pour configurer un service pour utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="96b2d-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="96b2d-114">Configurez une liaison qui utilise la sécurité de message sur un transport ou la sécurité au niveau du transport sur HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="96b2d-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="96b2d-115">Lorsque vous utilisez la sécurité de message, ajoutez l’une des liaisons fournies par le système, telles qu’un [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , ou un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) qui prend en charge la sécurité de message et le `UserName` type d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="96b2d-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="96b2d-116">Lorsque vous utilisez la sécurité au niveau du transport sur HTTP (S), ajoutez le [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ou [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , un [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) ou un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) qui utilise http (s) et le `Basic` schéma d’authentification.</span><span class="sxs-lookup"><span data-stu-id="96b2d-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="96b2d-117">Lorsque vous utilisez .NET Framework 3,5 ou des versions ultérieures, vous pouvez utiliser un validateur de nom d’utilisateur et de mot de passe personnalisé avec sécurité de transport et de message.</span><span class="sxs-lookup"><span data-stu-id="96b2d-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="96b2d-118">Avec WinFX, un validateur personnalisé de nom d’utilisateur et de mot de passe ne peut être utilisé qu’avec la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="96b2d-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="96b2d-119">Pour plus d’informations sur l’utilisation \<netTcpBinding> de dans ce contexte, consultez [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="96b2d-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="96b2d-120">Dans le fichier de configuration, sous l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajoutez un [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="96b2d-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="96b2d-121">Ajoutez un [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) élément ou à la section des liaisons.</span><span class="sxs-lookup"><span data-stu-id="96b2d-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="96b2d-122">Pour plus d’informations sur la création d’un élément de liaison WCF, consultez [Comment : spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="96b2d-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="96b2d-123">Affectez `mode` à l’attribut de ou la valeur [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` , `Transport` ou `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="96b2d-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="96b2d-124">Définissez l' `clientCredentialType` attribut de [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="96b2d-124">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="96b2d-125">Lorsque vous utilisez la sécurité de message, affectez `clientCredentialType` à l’attribut de la valeur [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) `UserName` .</span><span class="sxs-lookup"><span data-stu-id="96b2d-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="96b2d-126">Lorsque vous utilisez la sécurité au niveau du transport sur HTTP (S), affectez `clientCredentialType` à l’attribut de ou la valeur [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) `Basic` .</span><span class="sxs-lookup"><span data-stu-id="96b2d-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="96b2d-127">Lorsqu’un service WCF est hébergé dans Internet Information Services (IIS) à l’aide de la sécurité au niveau du transport et que la <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> propriété a la valeur <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , le schéma d’authentification personnalisé utilise un sous-ensemble de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="96b2d-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="96b2d-128">En effet, dans ce scénario, IIS effectue l’authentification Windows avant WCF appelant l’authentificateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="96b2d-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="96b2d-129">Pour plus d’informations sur la création d’un élément de liaison WCF, consultez [Comment : spécifier une liaison de service dans la configuration](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="96b2d-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="96b2d-130">L’exemple suivant montre le code de configuration de la liaison :</span><span class="sxs-lookup"><span data-stu-id="96b2d-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="96b2d-131">Configurez un comportement qui spécifie qu'un validateur de nom d'utilisateur et de mot de passe personnalisé est utilisé pour valider des paires nom d'utilisateur/mot de passe pour les jetons de sécurité <xref:System.IdentityModel.Tokens.UserNameSecurityToken> entrants.</span><span class="sxs-lookup"><span data-stu-id="96b2d-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="96b2d-132">En tant qu’enfant de l' [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajoutez un [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="96b2d-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="96b2d-133">Ajoutez un [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) à l' [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="96b2d-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="96b2d-134">Ajoutez un [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément et affectez `name` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="96b2d-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="96b2d-135">Ajoutez un [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) à l' [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="96b2d-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="96b2d-136">Ajoutez un [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) au [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="96b2d-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="96b2d-137">Définissez `userNamePasswordValidationMode` sur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="96b2d-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="96b2d-138">Si la `userNamePasswordValidationMode` valeur n’est pas définie, WCF utilise l’authentification Windows au lieu du validateur de nom d’utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="96b2d-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="96b2d-139">Affectez au `customUserNamePasswordValidatorType` le type qui représente votre validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="96b2d-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="96b2d-140">L’exemple suivant montre le `<serviceCredentials>` fragment à ce point :</span><span class="sxs-lookup"><span data-stu-id="96b2d-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="96b2d-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="96b2d-141">Example</span></span>

<span data-ttu-id="96b2d-142">L'exemple de code suivant montre comment créer un validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="96b2d-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="96b2d-143">N'utilisez pas le code qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="96b2d-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="96b2d-144">Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="96b2d-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="96b2d-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96b2d-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="96b2d-146">Comment : utiliser le fournisseur d'appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="96b2d-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="96b2d-147">Authentification</span><span class="sxs-lookup"><span data-stu-id="96b2d-147">Authentication</span></span>](authentication-in-wcf.md)
