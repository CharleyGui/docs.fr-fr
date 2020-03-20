---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153085"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="b6d2b-102">\<ajouter> de \<réclamationTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b6d2b-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="b6d2b-103">Spécifie les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="b6d2b-104">Par exemple, les services déclarent les exigences relatives aux informations d’identification entrantes devant posséder un certain jeu de types de revendications.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="b6d2b-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6d2b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b6d2b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<liaisons>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b6d2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b6d2b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>contraignantes**</span><span class="sxs-lookup"><span data-stu-id="b6d2b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b6d2b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de sécurité**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="b6d2b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<publiéTokenParameters>**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="b6d2b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequiments>**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="b6d2b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**</span><span class="sxs-lookup"><span data-stu-id="b6d2b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d2b-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6d2b-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6d2b-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6d2b-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b6d2b-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6d2b-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6d2b-117">Attributes</span></span>  
  
|<span data-ttu-id="b6d2b-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="b6d2b-118">Attribute</span></span>|<span data-ttu-id="b6d2b-119">Description</span><span class="sxs-lookup"><span data-stu-id="b6d2b-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6d2b-120">claimType</span><span class="sxs-lookup"><span data-stu-id="b6d2b-120">claimType</span></span>|<span data-ttu-id="b6d2b-121">URI définissant le type d'une revendication.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="b6d2b-122">Par exemple, pour acheter un produit d'un site Web, l'utilisateur doit présenter une carte de crédit valide avec limite de crédit suffisante.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="b6d2b-123">Le type de revendication est l'URI de la carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="b6d2b-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="b6d2b-124">isOptional</span></span>|<span data-ttu-id="b6d2b-125">Valeur booléenne indiquant si l'opération concerne une revendication facultative.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="b6d2b-126">Affectez à cet attribut la valeur `false` si c'est une revendication requise.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="b6d2b-127">Vous pouvez utiliser cet attribut lorsque le service demande certaines informations sans pour autant les exiger.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="b6d2b-128">Par exemple, si vous exigez que l’utilisateur saisit son prénom, son nom de famille et son adresse, mais décide que le numéro de téléphone est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6d2b-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6d2b-129">Child Elements</span></span>  
 <span data-ttu-id="b6d2b-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6d2b-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6d2b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="b6d2b-132">Élément</span><span class="sxs-lookup"><span data-stu-id="b6d2b-132">Element</span></span>|<span data-ttu-id="b6d2b-133">Description</span><span class="sxs-lookup"><span data-stu-id="b6d2b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6d2b-134">\<claimTypeRequiments></span><span class="sxs-lookup"><span data-stu-id="b6d2b-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="b6d2b-135">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="b6d2b-136">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b6d2b-137">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b6d2b-138">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6d2b-139">Notes </span><span class="sxs-lookup"><span data-stu-id="b6d2b-139">Remarks</span></span>  
 <span data-ttu-id="b6d2b-140">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b6d2b-141">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b6d2b-142">Cette exigence est explicitée dans une stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="b6d2b-143">Lorsqu’un client requiert des informations d’identification à partir d’un service fédéré (CardSpace, par exemple), il indique ces exigences dans une demande de jeton (RequestSecurityToken) afin que le service fédéré puisse publier ces informations et répondre aux exigences.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6d2b-144"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b6d2b-144">Example</span></span>  
 <span data-ttu-id="b6d2b-145">La configuration suivante ajoute deux exigences de type de revendication à une liaison de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b6d2b-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="b6d2b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6d2b-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b6d2b-147">\<claimTypeRequiments></span><span class="sxs-lookup"><span data-stu-id="b6d2b-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="b6d2b-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b6d2b-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6d2b-149">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="b6d2b-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b6d2b-150">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="b6d2b-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b6d2b-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b6d2b-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b6d2b-152">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b6d2b-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b6d2b-153">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="b6d2b-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
