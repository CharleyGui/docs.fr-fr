---
title: <add>d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 9c56cccd7a6f72a701e4b8652afecc2361e6218a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400686"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="75b78-102">\<Ajouter > de \<l’élément de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="75b78-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="75b78-103">Spécifie les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="75b78-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="75b78-104">Par exemple, les services déclarent les exigences relatives aux informations d’identification entrantes devant posséder un certain jeu de types de revendications.</span><span class="sxs-lookup"><span data-stu-id="75b78-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="75b78-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75b78-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="75b78-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="75b78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="75b78-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="75b78-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="75b78-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="75b78-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="75b78-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="75b78-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="75b78-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="75b78-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="75b78-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75b78-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75b78-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75b78-115">Attributes and Elements</span></span>  
 <span data-ttu-id="75b78-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75b78-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75b78-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="75b78-117">Attributes</span></span>  
  
|<span data-ttu-id="75b78-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="75b78-118">Attribute</span></span>|<span data-ttu-id="75b78-119">Description</span><span class="sxs-lookup"><span data-stu-id="75b78-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75b78-120">claimType</span><span class="sxs-lookup"><span data-stu-id="75b78-120">claimType</span></span>|<span data-ttu-id="75b78-121">URI définissant le type d'une revendication.</span><span class="sxs-lookup"><span data-stu-id="75b78-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="75b78-122">Par exemple, pour acheter un produit d'un site Web, l'utilisateur doit présenter une carte de crédit valide avec limite de crédit suffisante.</span><span class="sxs-lookup"><span data-stu-id="75b78-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="75b78-123">Le type de revendication est l'URI de la carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="75b78-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="75b78-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="75b78-124">isOptional</span></span>|<span data-ttu-id="75b78-125">Valeur booléenne indiquant si l'opération concerne une revendication facultative.</span><span class="sxs-lookup"><span data-stu-id="75b78-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="75b78-126">Affectez à cet attribut la valeur `false` si c'est une revendication requise.</span><span class="sxs-lookup"><span data-stu-id="75b78-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="75b78-127">Vous pouvez utiliser cet attribut lorsque le service demande certaines informations sans pour autant les exiger.</span><span class="sxs-lookup"><span data-stu-id="75b78-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="75b78-128">Par exemple, si vous décidez que l'utilisateur doit indiquer ses prénom, nom et adresse mais pas forcément son numéro de téléphone.</span><span class="sxs-lookup"><span data-stu-id="75b78-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75b78-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75b78-129">Child Elements</span></span>  
 <span data-ttu-id="75b78-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="75b78-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75b78-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75b78-131">Parent Elements</span></span>  
  
|<span data-ttu-id="75b78-132">Élément</span><span class="sxs-lookup"><span data-stu-id="75b78-132">Element</span></span>|<span data-ttu-id="75b78-133">Description</span><span class="sxs-lookup"><span data-stu-id="75b78-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75b78-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="75b78-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="75b78-135">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="75b78-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="75b78-136">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="75b78-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="75b78-137">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="75b78-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="75b78-138">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="75b78-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="75b78-139">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="75b78-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75b78-140">Notes</span><span class="sxs-lookup"><span data-stu-id="75b78-140">Remarks</span></span>  
 <span data-ttu-id="75b78-141">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="75b78-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="75b78-142">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="75b78-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="75b78-143">Cette exigence est explicitée dans une stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="75b78-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="75b78-144">Lorsqu’un client requiert des informations d’identification à partir d’un service fédéré (CardSpace, par exemple), il indique ces exigences dans une demande de jeton (RequestSecurityToken) afin que le service fédéré puisse publier ces informations et répondre aux exigences.</span><span class="sxs-lookup"><span data-stu-id="75b78-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b78-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="75b78-145">Example</span></span>  
 <span data-ttu-id="75b78-146">La configuration suivante ajoute deux exigences de type de revendication à une liaison de sécurité.</span><span class="sxs-lookup"><span data-stu-id="75b78-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75b78-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75b78-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
