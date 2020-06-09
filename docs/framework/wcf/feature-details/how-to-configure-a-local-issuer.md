---
title: 'Comment : configurer un émetteur local'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601242"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="0cb6b-102">Comment : configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="0cb6b-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="0cb6b-103">Cette rubrique décrit comment configurer un client afin d'utiliser un émetteur local pour les jetons émis.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="0cb6b-104">Lorsqu'un client communique avec un service fédéré, il arrive souvent que le service spécifie l'adresse du service d'émission de jeton de sécurité qui est attendue pour émettre le jeton que le client utilisera pour s'authentifier auprès du service fédéré.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="0cb6b-105">Dans certains cas, le client peut être configuré pour utiliser un *émetteur local*.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="0cb6b-106">Windows Communication Foundation (WCF) utilise un émetteur local dans les cas où l’adresse de l’émetteur d’une liaison fédérée est `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null` .</span><span class="sxs-lookup"><span data-stu-id="0cb6b-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="0cb6b-107">Dans ce cas, vous devez configurer <xref:System.ServiceModel.Description.ClientCredentials> avec l’adresse de l’émetteur local et la liaison à utiliser pour communiquer avec celui-ci.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="0cb6b-108">Si la <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> propriété de la `ClientCredentials` classe a la valeur `true` , qu’une adresse d’émetteur local n’est pas spécifiée et que l’adresse de l’émetteur spécifiée par le [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou une autre liaison fédérée est, `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou est `null` , l’émetteur Windows CardSpace est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="0cb6b-109">Pour configurer l'émetteur local dans le code</span><span class="sxs-lookup"><span data-stu-id="0cb6b-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="0cb6b-110">Créez une variable de type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="0cb6b-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="0cb6b-111">Affectez à la variable la valeur de l'instance retournée par la propriété <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> de la classe `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="0cb6b-112">Cette instance est retournée par la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> du client (héritée de <xref:System.ServiceModel.ClientBase%601>) ou la propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A> de <xref:System.ServiceModel.ChannelFactory> :</span><span class="sxs-lookup"><span data-stu-id="0cb6b-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="0cb6b-113">Affectez une nouvelle instance de <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> à la propriété <xref:System.ServiceModel.EndpointAddress>, avec l'adresse de l'émetteur local comme argument au constructeur.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="0cb6b-114">Ou bien, créez une instance <xref:System.Uri> comme argument au constructeur.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="0cb6b-115">Le `addressHeaders` paramètre est un tableau d' <xref:System.ServiceModel.Channels.AddressHeader> instances, comme indiqué.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="0cb6b-116">Définissez la liaison de l’émetteur local à l’aide de la <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="0cb6b-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-117">Optional.</span></span> <span data-ttu-id="0cb6b-118">Ajoutez des comportements de point de terminaison configurés pour l’émetteur local en ajoutant ces comportements à la collection retournée par la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="0cb6b-119">Pour configurer l'émetteur local dans la configuration</span><span class="sxs-lookup"><span data-stu-id="0cb6b-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="0cb6b-120">Créez un [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) élément en tant qu’enfant de l' [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) élément qui est lui-même un enfant de l' [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) élément dans un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-120">Create a [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="0cb6b-121">Affectez à l'attribut `address` l'adresse de l'émetteur local qui acceptera des demandes de jeton.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="0cb6b-122">Affectez aux attributs `binding` et `bindingConfiguration` des valeurs référençant la liaison appropriée à utiliser lors de la communication avec le point de terminaison de l'émetteur local.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="0cb6b-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-123">Optional.</span></span> <span data-ttu-id="0cb6b-124">Définissez l' [\<identity>](../../configure-apps/file-schema/wcf/identity.md) élément en tant qu’enfant de l' `localIssuer` élément <> et spécifiez les informations d’identité de l’émetteur local.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-124">Set the [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="0cb6b-125">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-125">Optional.</span></span> <span data-ttu-id="0cb6b-126">Définissez l' [\<headers>](../../configure-apps/file-schema/wcf/headers.md) élément en tant qu’enfant de l' `localIssuer` élément <> et spécifiez les en-têtes supplémentaires requis pour adresser correctement l’émetteur local.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-126">Set the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="0cb6b-127">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0cb6b-127">.NET Framework Security</span></span>

<span data-ttu-id="0cb6b-128">Notez que si une liaison et une adresse d’émetteur sont spécifiées pour une liaison donnée, l’émetteur local n’est pas utilisé pour les points de terminaison qui utilisent cette liaison.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="0cb6b-129">Les clients qui prévoient d'utiliser systématiquement l'émetteur local doivent s'assurer de ne pas utiliser de liaison de ce type ou de modifier la liaison afin que l'adresse de l'émetteur soit `null`.</span><span class="sxs-lookup"><span data-stu-id="0cb6b-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cb6b-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cb6b-130">See also</span></span>

- [<span data-ttu-id="0cb6b-131">Comment : configurer des informations d'identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="0cb6b-131">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="0cb6b-132">Comment : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="0cb6b-132">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="0cb6b-133">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0cb6b-133">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)
