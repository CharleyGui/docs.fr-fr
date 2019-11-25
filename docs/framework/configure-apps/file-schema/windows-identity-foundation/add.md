---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973800"
---
# <a name="add"></a><span data-ttu-id="e9b41-101">\<add></span><span class="sxs-lookup"><span data-stu-id="e9b41-101">\<add></span></span>
<span data-ttu-id="e9b41-102">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="e9b41-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="e9b41-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9b41-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9b41-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e9b41-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e9b41-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration**](identityconfiguration.md) ></span><span class="sxs-lookup"><span data-stu-id="e9b41-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e9b41-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**securityTokenHandlers**](securitytokenhandlers.md) ></span><span class="sxs-lookup"><span data-stu-id="e9b41-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="e9b41-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Ajouter des >**</span><span class="sxs-lookup"><span data-stu-id="e9b41-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b41-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9b41-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9b41-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e9b41-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9b41-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e9b41-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9b41-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e9b41-111">Attributes</span></span>  
  
|<span data-ttu-id="e9b41-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="e9b41-112">Attribute</span></span>|<span data-ttu-id="e9b41-113">Description</span><span class="sxs-lookup"><span data-stu-id="e9b41-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9b41-114">type</span><span class="sxs-lookup"><span data-stu-id="e9b41-114">type</span></span>|<span data-ttu-id="e9b41-115">Nom de type CLR du gestionnaire de jetons à ajouter.</span><span class="sxs-lookup"><span data-stu-id="e9b41-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="e9b41-116">Pour plus d’informations sur la spécification de l’attribut `type`, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="e9b41-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9b41-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e9b41-117">Child Elements</span></span>  
  
|<span data-ttu-id="e9b41-118">Élément</span><span class="sxs-lookup"><span data-stu-id="e9b41-118">Element</span></span>|<span data-ttu-id="e9b41-119">Description</span><span class="sxs-lookup"><span data-stu-id="e9b41-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9b41-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="e9b41-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="e9b41-121">Fournit la configuration pour la classe <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, la classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="e9b41-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="e9b41-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="e9b41-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="e9b41-123">Fournit la configuration pour la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="e9b41-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="e9b41-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="e9b41-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="e9b41-125">Fournit la configuration pour la classe <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="e9b41-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="e9b41-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="e9b41-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="e9b41-127">Fournit la configuration facultative pour la classe <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="e9b41-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9b41-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e9b41-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e9b41-129">Élément</span><span class="sxs-lookup"><span data-stu-id="e9b41-129">Element</span></span>|<span data-ttu-id="e9b41-130">Description</span><span class="sxs-lookup"><span data-stu-id="e9b41-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9b41-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e9b41-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="e9b41-132">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e9b41-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9b41-133">Notes</span><span class="sxs-lookup"><span data-stu-id="e9b41-133">Remarks</span></span>  
 <span data-ttu-id="e9b41-134">L’élément `<add>` peut accepter un élément enfant unique qui spécifie la configuration du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="e9b41-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="e9b41-135">Cela dépend du fait que la classe de gestionnaire référencée via l’attribut `type` de l’élément `<add>` fournit la prise en charge de cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e9b41-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="e9b41-136">Les classes de gestionnaire de jetons qui fournissent cette fonctionnalité doivent exposer un constructeur qui prend un objet <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="e9b41-137">Plusieurs des classes de gestionnaires de jetons de sécurité intégrées offrent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e9b41-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="e9b41-138">Ces classes sont <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>et <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="e9b41-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e9b41-139">La collection de gestionnaires de jetons ne peut contenir qu’un seul gestionnaire d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="e9b41-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="e9b41-140">Cela signifie, par exemple, que si vous souhaitez ajouter un gestionnaire dérivé de la classe <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> à la collection, vous devez d’abord supprimer l' <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, qui est présent par défaut, de la collection.</span><span class="sxs-lookup"><span data-stu-id="e9b41-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="e9b41-141">Vous pouvez utiliser l’élément [\<remove >](remove.md) pour supprimer un gestionnaire unique de la collection ou utiliser l’élément [\<Clear >](clear.md) pour supprimer tous les gestionnaires de la collection.</span><span class="sxs-lookup"><span data-stu-id="e9b41-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="e9b41-142">Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection de gestionnaires de jetons sous l’élément [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) et ceux spécifiés au niveau du service sous l’élément [\<identityConfiguration](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="e9b41-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9b41-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="e9b41-143">Example</span></span>  
 <span data-ttu-id="e9b41-144">Le code XML suivant montre l’utilisation des éléments `<add>` et `<remove>` pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e9b41-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="e9b41-145">Le code XML provient de l’exemple `ClaimsAwareWebFarm`.</span><span class="sxs-lookup"><span data-stu-id="e9b41-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
