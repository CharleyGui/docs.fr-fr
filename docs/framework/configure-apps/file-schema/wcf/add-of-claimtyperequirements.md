---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153085"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="b1369-102">\<add> de \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b1369-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="b1369-103">Spécifie les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="b1369-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="b1369-104">Par exemple, les services déclarent les exigences relatives aux informations d’identification entrantes devant posséder un certain jeu de types de revendications.</span><span class="sxs-lookup"><span data-stu-id="b1369-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b1369-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1369-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1369-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1369-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b1369-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1369-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1369-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1369-108">Attributes</span></span>  
  
|<span data-ttu-id="b1369-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1369-109">Attribute</span></span>|<span data-ttu-id="b1369-110">Description</span><span class="sxs-lookup"><span data-stu-id="b1369-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1369-111">claimType</span><span class="sxs-lookup"><span data-stu-id="b1369-111">claimType</span></span>|<span data-ttu-id="b1369-112">URI définissant le type d'une revendication.</span><span class="sxs-lookup"><span data-stu-id="b1369-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="b1369-113">Par exemple, pour acheter un produit d'un site Web, l'utilisateur doit présenter une carte de crédit valide avec limite de crédit suffisante.</span><span class="sxs-lookup"><span data-stu-id="b1369-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="b1369-114">Le type de revendication est l'URI de la carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="b1369-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="b1369-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="b1369-115">isOptional</span></span>|<span data-ttu-id="b1369-116">Valeur booléenne indiquant si l'opération concerne une revendication facultative.</span><span class="sxs-lookup"><span data-stu-id="b1369-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="b1369-117">Affectez à cet attribut la valeur `false` si c'est une revendication requise.</span><span class="sxs-lookup"><span data-stu-id="b1369-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="b1369-118">Vous pouvez utiliser cet attribut lorsque le service demande certaines informations sans pour autant les exiger.</span><span class="sxs-lookup"><span data-stu-id="b1369-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="b1369-119">Par exemple, si vous avez besoin que l’utilisateur entre son prénom, son nom et son adresse, il est préférable de choisir ce numéro de téléphone.</span><span class="sxs-lookup"><span data-stu-id="b1369-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1369-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1369-120">Child Elements</span></span>  
 <span data-ttu-id="b1369-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b1369-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1369-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1369-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b1369-123">Élément</span><span class="sxs-lookup"><span data-stu-id="b1369-123">Element</span></span>|<span data-ttu-id="b1369-124">Description</span><span class="sxs-lookup"><span data-stu-id="b1369-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="b1369-125">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="b1369-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="b1369-126">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="b1369-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b1369-127">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="b1369-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b1369-128">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="b1369-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1369-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="b1369-129">Remarks</span></span>  
 <span data-ttu-id="b1369-130">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="b1369-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b1369-131">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="b1369-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b1369-132">Cette exigence est explicitée dans une stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b1369-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="b1369-133">Lorsqu’un client requiert des informations d’identification à partir d’un service fédéré (CardSpace, par exemple), il indique ces exigences dans une demande de jeton (RequestSecurityToken) afin que le service fédéré puisse publier ces informations et répondre aux exigences.</span><span class="sxs-lookup"><span data-stu-id="b1369-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1369-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1369-134">Example</span></span>  
 <span data-ttu-id="b1369-135">La configuration suivante ajoute deux exigences de type de revendication à une liaison de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b1369-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1369-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1369-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="b1369-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b1369-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b1369-138">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="b1369-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b1369-139">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="b1369-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="b1369-140">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b1369-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b1369-141">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="b1369-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
