---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 7c2b6bdc62da63905d7ff33a9984808e7b7d114f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544538"
---
# \<add>
<span data-ttu-id="1b8ca-101">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-101">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="1b8ca-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b8ca-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b8ca-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1b8ca-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1b8ca-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b8ca-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="1b8ca-105">Attributes</span></span>  
  
|<span data-ttu-id="1b8ca-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="1b8ca-106">Attribute</span></span>|<span data-ttu-id="1b8ca-107">Description</span><span class="sxs-lookup"><span data-stu-id="1b8ca-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b8ca-108">type</span><span class="sxs-lookup"><span data-stu-id="1b8ca-108">type</span></span>|<span data-ttu-id="1b8ca-109">Nom de type CLR du gestionnaire de jetons à ajouter.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-109">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="1b8ca-110">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="1b8ca-110">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b8ca-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1b8ca-111">Child Elements</span></span>  
  
|<span data-ttu-id="1b8ca-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1b8ca-112">Element</span></span>|<span data-ttu-id="1b8ca-113">Description</span><span class="sxs-lookup"><span data-stu-id="1b8ca-113">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="1b8ca-114">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-114">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="1b8ca-115">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="1b8ca-116">Fournit la configuration pour la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-116">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="1b8ca-117">Fournit une configuration facultative pour la <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-117">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b8ca-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1b8ca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1b8ca-119">Élément</span><span class="sxs-lookup"><span data-stu-id="1b8ca-119">Element</span></span>|<span data-ttu-id="1b8ca-120">Description</span><span class="sxs-lookup"><span data-stu-id="1b8ca-120">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="1b8ca-121">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-121">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b8ca-122">Notes</span><span class="sxs-lookup"><span data-stu-id="1b8ca-122">Remarks</span></span>  
 <span data-ttu-id="1b8ca-123">L' `<add>` élément peut accepter un seul élément enfant qui spécifie la configuration du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-123">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="1b8ca-124">Cela dépend du fait que la classe de gestionnaire référencée par l' `type` attribut de l' `<add>` élément assure la prise en charge de cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-124">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="1b8ca-125">Les classes de gestionnaire de jetons qui fournissent cette fonctionnalité doivent exposer un constructeur qui prend un <xref:System.Xml.XmlElement> objet.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-125">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="1b8ca-126">Plusieurs des classes de gestionnaires de jetons de sécurité intégrées offrent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-126">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="1b8ca-127">Ces classes sont <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> et <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="1b8ca-127">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1b8ca-128">La collection de gestionnaires de jetons ne peut contenir qu’un seul gestionnaire d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-128">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="1b8ca-129">Cela signifie, par exemple, que si vous souhaitez ajouter un gestionnaire dérivé de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe à la collection, vous devez d’abord supprimer le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , qui est présent par défaut, à partir de la collection.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-129">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="1b8ca-130">Vous pouvez utiliser l' [\<remove>](remove.md) élément pour supprimer un gestionnaire unique de la collection ou utiliser l' [\<clear>](clear.md) élément pour supprimer tous les gestionnaires de la collection.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-130">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="1b8ca-131">Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection de gestionnaires de jetons sous l' [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) élément et ceux spécifiés au niveau du service sous l' [\<identityConfiguration>](identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-131">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b8ca-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1b8ca-132">Example</span></span>  
 <span data-ttu-id="1b8ca-133">Le code XML suivant montre l’utilisation des `<add>` `<remove>` éléments et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-133">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="1b8ca-134">Le code XML est extrait de l' `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="1b8ca-134">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
