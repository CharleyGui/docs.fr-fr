---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 9505970c1fd7fcdfe62d3c6ef58f5d653fab4106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941991"
---
# <a name="add"></a><span data-ttu-id="fa8ae-101">\<add></span><span class="sxs-lookup"><span data-stu-id="fa8ae-101">\<add></span></span>
<span data-ttu-id="fa8ae-102">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="fa8ae-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fa8ae-103">\<system.identityModel></span></span>  
<span data-ttu-id="fa8ae-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fa8ae-104">\<identityConfiguration></span></span>  
<span data-ttu-id="fa8ae-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fa8ae-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="fa8ae-106">\<add></span><span class="sxs-lookup"><span data-stu-id="fa8ae-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa8ae-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa8ae-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa8ae-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fa8ae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fa8ae-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa8ae-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="fa8ae-110">Attributes</span></span>  
  
|<span data-ttu-id="fa8ae-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="fa8ae-111">Attribute</span></span>|<span data-ttu-id="fa8ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="fa8ae-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa8ae-113">type</span><span class="sxs-lookup"><span data-stu-id="fa8ae-113">type</span></span>|<span data-ttu-id="fa8ae-114">Nom de type CLR du gestionnaire de jetons à ajouter.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="fa8ae-115">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="fa8ae-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa8ae-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fa8ae-116">Child Elements</span></span>  
  
|<span data-ttu-id="fa8ae-117">Élément</span><span class="sxs-lookup"><span data-stu-id="fa8ae-117">Element</span></span>|<span data-ttu-id="fa8ae-118">Description</span><span class="sxs-lookup"><span data-stu-id="fa8ae-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa8ae-119">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="fa8ae-119">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="fa8ae-120">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="fa8ae-121">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="fa8ae-121">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="fa8ae-122">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="fa8ae-123">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="fa8ae-123">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="fa8ae-124">Fournit la configuration pour <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="fa8ae-125">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="fa8ae-125">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="fa8ae-126">Fournit une configuration facultative pour <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa8ae-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fa8ae-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fa8ae-128">Élément</span><span class="sxs-lookup"><span data-stu-id="fa8ae-128">Element</span></span>|<span data-ttu-id="fa8ae-129">Description</span><span class="sxs-lookup"><span data-stu-id="fa8ae-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa8ae-130">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fa8ae-130">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="fa8ae-131">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa8ae-132">Notes</span><span class="sxs-lookup"><span data-stu-id="fa8ae-132">Remarks</span></span>  
 <span data-ttu-id="fa8ae-133">L' `<add>` élément peut accepter un seul élément enfant qui spécifie la configuration du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="fa8ae-134">Cela dépend du fait que la classe de gestionnaire référencée par `type` l’attribut de `<add>` l’élément assure la prise en charge de cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="fa8ae-135">Les classes de gestionnaire de jetons qui fournissent cette fonctionnalité doivent exposer un constructeur <xref:System.Xml.XmlElement> qui prend un objet.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="fa8ae-136">Plusieurs des classes de gestionnaires de jetons de sécurité intégrées offrent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="fa8ae-137">Ces classes sont <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>et .<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="fa8ae-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fa8ae-138">La collection de gestionnaires de jetons ne peut contenir qu’un seul gestionnaire d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="fa8ae-139">Cela signifie, par exemple, que si vous souhaitez ajouter un gestionnaire dérivé de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à la collection, vous devez d’abord supprimer le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, qui est présent par défaut, à partir de la collection.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="fa8ae-140">Vous pouvez utiliser l' [ \<élément remove >](remove.md) pour supprimer un gestionnaire unique de la collection ou utiliser l' [ \<élément clear >](clear.md) pour supprimer tous les gestionnaires de la collection.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-140">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="fa8ae-141">Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés sur la collection de gestionnaires de jetons sous l' [ \<élément securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) et ceux spécifiés au niveau du service sous le [ \< élément identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="fa8ae-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa8ae-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="fa8ae-142">Example</span></span>  
 <span data-ttu-id="fa8ae-143">Le code XML suivant montre l’utilisation des `<add>` éléments `<remove>` et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="fa8ae-144">Le code XML est extrait de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="fa8ae-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
