---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 451750a1facd9a886b53427a8d54580d1a939fa5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968510"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="915df-101">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="915df-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="915df-102">Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="915df-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="915df-103">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="915df-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="915df-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="915df-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="915df-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="915df-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="915df-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration**](identityconfiguration.md) ></span><span class="sxs-lookup"><span data-stu-id="915df-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="915df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**securityTokenHandlers**](securitytokenhandlers.md) ></span><span class="sxs-lookup"><span data-stu-id="915df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="915df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration**](securitytokenhandlerconfiguration.md) ></span><span class="sxs-lookup"><span data-stu-id="915df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="915df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**issuerTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="915df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915df-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="915df-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="915df-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="915df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="915df-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="915df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="915df-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="915df-113">Attributes</span></span>  
  
|<span data-ttu-id="915df-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="915df-114">Attribute</span></span>|<span data-ttu-id="915df-115">Description</span><span class="sxs-lookup"><span data-stu-id="915df-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="915df-116">type</span><span class="sxs-lookup"><span data-stu-id="915df-116">type</span></span>|<span data-ttu-id="915df-117">Spécifie le type de programme de résolution de jetons d’émetteur.</span><span class="sxs-lookup"><span data-stu-id="915df-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="915df-118">Il doit s’agir de la classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou d’un type qui dérive de la classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="915df-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="915df-119">Requis.</span><span class="sxs-lookup"><span data-stu-id="915df-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="915df-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="915df-120">Child Elements</span></span>  
 <span data-ttu-id="915df-121">aucune.</span><span class="sxs-lookup"><span data-stu-id="915df-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="915df-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="915df-122">Parent Elements</span></span>  
  
|<span data-ttu-id="915df-123">Élément</span><span class="sxs-lookup"><span data-stu-id="915df-123">Element</span></span>|<span data-ttu-id="915df-124">Description</span><span class="sxs-lookup"><span data-stu-id="915df-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="915df-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="915df-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="915df-126">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="915df-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915df-127">Notes</span><span class="sxs-lookup"><span data-stu-id="915df-127">Remarks</span></span>  
 <span data-ttu-id="915df-128">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="915df-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="915df-129">Il est utilisé pour récupérer le matériel de chiffrement utilisé pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="915df-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="915df-130">Vous devez spécifier l’attribut `type`.</span><span class="sxs-lookup"><span data-stu-id="915df-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="915df-131">Le type spécifié peut être <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou un type personnalisé qui dérive de la classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="915df-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="915df-132">Certains gestionnaires de jetons vous permettent de spécifier les paramètres du programme de résolution de jetons d’émetteur dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="915df-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="915df-133">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="915df-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="915df-134">La spécification de l’élément `<issuerTokenResolver>` en tant qu’élément enfant de l’élément [\<identityConfiguration >](identityconfiguration.md) est dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="915df-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="915df-135">Les paramètres de l’élément `<securityTokenHandlerConfiguration>` substituent ceux qui se trouvent sur l’élément `<identityConfiguration>`.</span><span class="sxs-lookup"><span data-stu-id="915df-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="915df-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="915df-136">Example</span></span>  
 <span data-ttu-id="915df-137">Le code XML suivant montre la configuration d’un programme de résolution de jetons d’émetteur basé sur une classe personnalisée qui dérive de <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="915df-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="915df-138">Le programme de résolution de jetons gère un dictionnaire de paires de clés d’audience qui est initialisé à partir d’un élément de configuration personnalisé (`<AddAudienceKeyPair>`) défini pour la classe.</span><span class="sxs-lookup"><span data-stu-id="915df-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="915df-139">La classe substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> pour traiter cet élément.</span><span class="sxs-lookup"><span data-stu-id="915df-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="915df-140">Le remplacement est illustré dans l’exemple suivant : Toutefois, les méthodes qu’il appelle ne sont pas affichées par souci de concision.</span><span class="sxs-lookup"><span data-stu-id="915df-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="915df-141">Pour obtenir un exemple complet, consultez l’exemple `CustomToken`.</span><span class="sxs-lookup"><span data-stu-id="915df-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="915df-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="915df-142">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="915df-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="915df-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
