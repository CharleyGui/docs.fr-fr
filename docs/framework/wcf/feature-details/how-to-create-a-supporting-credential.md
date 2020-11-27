---
title: 'Procédure : créer des informations d’identification de prise en charge'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1e11da11de68b1d3e24115387ec61ad22ec031b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286303"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="bcc69-102">Procédure : créer des informations d’identification de prise en charge</span><span class="sxs-lookup"><span data-stu-id="bcc69-102">How to: Create a Supporting Credential</span></span>

<span data-ttu-id="bcc69-103">Il est possible d'avoir un modèle de sécurité personnalisé qui requiert plusieurs informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="bcc69-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="bcc69-104">Par exemple, un service peut exiger du client non seulement un nom d'utilisateur et un mot de passe, mais également une information d'identification qui prouve que le client a plus de 18 ans.</span><span class="sxs-lookup"><span data-stu-id="bcc69-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="bcc69-105">La deuxième information d’identification est une *information d’identification de prise en charge*.</span><span class="sxs-lookup"><span data-stu-id="bcc69-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="bcc69-106">Cette rubrique explique comment implémenter ces informations d’identification dans un client Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bcc69-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcc69-107">La spécification pour la prise en charge d'informations d'identification fait partie de la spécification WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="bcc69-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="bcc69-108">Pour plus d’informations, consultez [spécifications de Web Services Security](/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="bcc69-108">For more information, see [Web Services Security Specifications](/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="bcc69-109">Supporting Tokens</span><span class="sxs-lookup"><span data-stu-id="bcc69-109">Supporting Tokens</span></span>  

 <span data-ttu-id="bcc69-110">En résumé, lorsque vous utilisez la sécurité de message, les *informations d’identification principales* sont toujours utilisées pour sécuriser le message (par exemple, un certificat X. 509 ou un ticket Kerberos).</span><span class="sxs-lookup"><span data-stu-id="bcc69-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="bcc69-111">Comme défini par la spécification, une liaison de sécurité utilise des *jetons* pour sécuriser l’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="bcc69-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="bcc69-112">Un *jeton* est une représentation d’informations d’identification de sécurité.</span><span class="sxs-lookup"><span data-stu-id="bcc69-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="bcc69-113">La liaison de sécurité utilise un jeton principal identifié dans la stratégie de liaison de sécurité pour créer une signature.</span><span class="sxs-lookup"><span data-stu-id="bcc69-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="bcc69-114">Cette signature est appelée *signature de message*.</span><span class="sxs-lookup"><span data-stu-id="bcc69-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="bcc69-115">Des jetons supplémentaires peuvent être spécifiés afin d'augmenter les revendications fournies par le jeton associé à la signature de message.</span><span class="sxs-lookup"><span data-stu-id="bcc69-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="bcc69-116">Endossement, signature et chiffrement</span><span class="sxs-lookup"><span data-stu-id="bcc69-116">Endorsing, Signing, and Encrypting</span></span>  

 <span data-ttu-id="bcc69-117">Les informations d’identification de prise en charge entraînent la transmission d’un *jeton de prise en charge* dans le message.</span><span class="sxs-lookup"><span data-stu-id="bcc69-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="bcc69-118">La spécification WS-SecurityPolicy définit quatre façons de joindre un jeton de prise en charge au message, comme décrit dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="bcc69-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="bcc69-119">Objectif</span><span class="sxs-lookup"><span data-stu-id="bcc69-119">Purpose</span></span>|<span data-ttu-id="bcc69-120">Description</span><span class="sxs-lookup"><span data-stu-id="bcc69-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcc69-121">Signé</span><span class="sxs-lookup"><span data-stu-id="bcc69-121">Signed</span></span>|<span data-ttu-id="bcc69-122">Le jeton de prise en charge est inclus dans l'en-tête de sécurité et est signé par la signature de message.</span><span class="sxs-lookup"><span data-stu-id="bcc69-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="bcc69-123">Endossement</span><span class="sxs-lookup"><span data-stu-id="bcc69-123">Endorsing</span></span>|<span data-ttu-id="bcc69-124">Un *jeton d’endossement* signe la signature du message.</span><span class="sxs-lookup"><span data-stu-id="bcc69-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="bcc69-125">Signé et endossement</span><span class="sxs-lookup"><span data-stu-id="bcc69-125">Signed and Endorsing</span></span>|<span data-ttu-id="bcc69-126">Les jetons d'endossement signés signent l'élément `ds:Signature` entier produit à partir de la signature de message et sont eux-mêmes signés par cette signature de message ; autrement dit, les deux jetons (le jeton utilisé pour la signature de message et le jeton d'endossement signé) se signent l'un l'autre.</span><span class="sxs-lookup"><span data-stu-id="bcc69-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="bcc69-127">Signé et chiffrement</span><span class="sxs-lookup"><span data-stu-id="bcc69-127">Signed and Encrypting</span></span>|<span data-ttu-id="bcc69-128">Les jetons de prise en charge chiffrés et signés sont des jetons de prise en charge signés qui sont également chiffrés lorsqu'ils apparaissent dans le `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="bcc69-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="bcc69-129">Programmation d'informations d'identification de prise en charge</span><span class="sxs-lookup"><span data-stu-id="bcc69-129">Programming Supporting Credentials</span></span>  

 <span data-ttu-id="bcc69-130">Pour créer un service qui utilise des jetons de prise en charge, vous devez créer un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="bcc69-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="bcc69-131">(Pour plus d’informations, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="bcc69-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="bcc69-132">La première étape de création d’une liaison personnalisée consiste à créer un élément de liaison de sécurité, qui peut être l’un des trois types suivants :</span><span class="sxs-lookup"><span data-stu-id="bcc69-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="bcc69-133">Toutes les classes héritent de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement>, qui inclut quatre propriétés pertinentes :</span><span class="sxs-lookup"><span data-stu-id="bcc69-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="bcc69-134">Étendues</span><span class="sxs-lookup"><span data-stu-id="bcc69-134">Scopes</span></span>  

 <span data-ttu-id="bcc69-135">Il existe deux étendues pour les informations d'identification de prise en charge :</span><span class="sxs-lookup"><span data-stu-id="bcc69-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="bcc69-136">Les *jetons de prise en charge du point de terminaison* prennent en charge toutes les opérations d’un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bcc69-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="bcc69-137">Autrement dit, l'information d'identification que le jeton de prise en charge représente peut être utilisée chaque fois qu'une opération de point de terminaison est appelée.</span><span class="sxs-lookup"><span data-stu-id="bcc69-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="bcc69-138">Les *jetons de prise en charge* de l’opération prennent uniquement en charge une opération de point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="bcc69-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="bcc69-139">Comme indiqué par les noms de propriétés, les informations d'identification de prise en charge peuvent être obligatoires ou facultatives.</span><span class="sxs-lookup"><span data-stu-id="bcc69-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="bcc69-140">Autrement dit, l'information d'identification de prise en charge est utilisée si elle est présente, bien que cela ne soit pas nécessaire, mais l'authentification n'échouera pas si elle n'est pas présente.</span><span class="sxs-lookup"><span data-stu-id="bcc69-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="bcc69-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="bcc69-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="bcc69-142">Pour créer une liaison personnalisée qui inclut des informations d’identification de prise en charge</span><span class="sxs-lookup"><span data-stu-id="bcc69-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="bcc69-143">Créez un élément de liaison de sécurité.</span><span class="sxs-lookup"><span data-stu-id="bcc69-143">Create a security binding element.</span></span> <span data-ttu-id="bcc69-144">L'exemple suivant crée un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> avec le mode d'authentification `UserNameForCertificate`.</span><span class="sxs-lookup"><span data-stu-id="bcc69-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="bcc69-145">Utiliser la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="bcc69-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="bcc69-146">Ajoutez le paramètre de prise en charge à la collection de types retournée par la propriété appropriée (`Endorsing`, `Signed`, `SignedEncrypted` ou `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="bcc69-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="bcc69-147">Les types dans l'espace de noms <xref:System.ServiceModel.Security.Tokens> incluent des types couramment utilisés, tels que <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="bcc69-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc69-148"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bcc69-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="bcc69-149">Description</span><span class="sxs-lookup"><span data-stu-id="bcc69-149">Description</span></span>  

 <span data-ttu-id="bcc69-150">L’exemple suivant crée une instance du <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et ajoute une instance de la classe <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> à la collection retournée par la propriété Endorsing.</span><span class="sxs-lookup"><span data-stu-id="bcc69-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bcc69-151">Code</span><span class="sxs-lookup"><span data-stu-id="bcc69-151">Code</span></span>  

 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bcc69-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcc69-152">See also</span></span>

- [<span data-ttu-id="bcc69-153">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bcc69-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
