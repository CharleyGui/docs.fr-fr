---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152669"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="2d409-101">\<émetteurTokenResolver></span><span class="sxs-lookup"><span data-stu-id="2d409-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="2d409-102">Enregistre le résa résolveur de jetons de l’émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="2d409-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="2d409-103">Le résolveur de jetons de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons entrants et les messages.</span><span class="sxs-lookup"><span data-stu-id="2d409-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="2d409-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d409-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d409-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2d409-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2d409-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2d409-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2d409-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2d409-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2d409-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2d409-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="2d409-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<émetteurTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="2d409-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d409-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d409-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d409-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2d409-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2d409-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2d409-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d409-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="2d409-113">Attributes</span></span>  
  
|<span data-ttu-id="2d409-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="2d409-114">Attribute</span></span>|<span data-ttu-id="2d409-115">Description</span><span class="sxs-lookup"><span data-stu-id="2d409-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d409-116">type</span><span class="sxs-lookup"><span data-stu-id="2d409-116">type</span></span>|<span data-ttu-id="2d409-117">Spécifie le type de résouteur de jetons de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="2d409-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="2d409-118">Doit être <xref:System.IdentityModel.Tokens.IssuerTokenResolver> soit la classe ou un <xref:System.IdentityModel.Tokens.IssuerTokenResolver> type qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="2d409-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="2d409-119">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2d409-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d409-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d409-120">Child Elements</span></span>  
 <span data-ttu-id="2d409-121">None</span><span class="sxs-lookup"><span data-stu-id="2d409-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d409-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2d409-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2d409-123">Élément</span><span class="sxs-lookup"><span data-stu-id="2d409-123">Element</span></span>|<span data-ttu-id="2d409-124">Description</span><span class="sxs-lookup"><span data-stu-id="2d409-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d409-125">\<sécuritéTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="2d409-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="2d409-126">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2d409-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d409-127">Notes </span><span class="sxs-lookup"><span data-stu-id="2d409-127">Remarks</span></span>  
 <span data-ttu-id="2d409-128">Le résolveur de jetons de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons entrants et les messages.</span><span class="sxs-lookup"><span data-stu-id="2d409-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="2d409-129">Il est utilisé pour récupérer le matériel cryptographique qui est utilisé pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="2d409-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="2d409-130">Vous devez `type` spécifier l’attribut.</span><span class="sxs-lookup"><span data-stu-id="2d409-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="2d409-131">Le type spécifié <xref:System.IdentityModel.Tokens.IssuerTokenResolver> peut être soit ou un <xref:System.IdentityModel.Tokens.IssuerTokenResolver> type personnalisé qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="2d409-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="2d409-132">Certains gestionnaires de jetons vous permettent de spécifier les paramètres de résolution de jetons de l’émetteur dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="2d409-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="2d409-133">Les paramètres des manutentionnaires individuels remplacent ceux spécifiés sur la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2d409-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d409-134">Spécifier l’élément `<issuerTokenResolver>` comme élément enfant de [ \<l’identitéConfiguration>](identityconfiguration.md) élément a été déprécié, mais est toujours pris en charge pour la compatibilité vers l’arrière.</span><span class="sxs-lookup"><span data-stu-id="2d409-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="2d409-135">Les paramètres `<securityTokenHandlerConfiguration>` de l’élément `<identityConfiguration>` l’emportent sur ceux de l’élément.</span><span class="sxs-lookup"><span data-stu-id="2d409-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d409-136"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2d409-136">Example</span></span>  
 <span data-ttu-id="2d409-137">Le XML suivant affiche la configuration d’un résolveur de jetons <xref:System.IdentityModel.Tokens.IssuerTokenResolver>d’émetteur qui est basé sur une classe personnalisée qui dérive de .</span><span class="sxs-lookup"><span data-stu-id="2d409-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="2d409-138">Le résolveur de jetons maintient un dictionnaire de paires d’audience-clé qui est parascé à partir d’un élément de configuration personnalisé (`<AddAudienceKeyPair>`) défini pour la classe.</span><span class="sxs-lookup"><span data-stu-id="2d409-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="2d409-139">La classe l’emporte sur la <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> méthode pour traiter cet élément.</span><span class="sxs-lookup"><span data-stu-id="2d409-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="2d409-140">La dérogation est illustrée dans l’exemple suivant; cependant, les méthodes qu’il appelle ne sont pas indiquées pour la brièveté.</span><span class="sxs-lookup"><span data-stu-id="2d409-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="2d409-141">Pour l’exemple complet, voir l’échantillon. `CustomToken`</span><span class="sxs-lookup"><span data-stu-id="2d409-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="2d409-142"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2d409-142">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="2d409-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d409-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
