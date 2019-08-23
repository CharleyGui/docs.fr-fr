---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942627"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="05dfc-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="05dfc-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="05dfc-102">Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="05dfc-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="05dfc-103">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="05dfc-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="05dfc-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="05dfc-104">\<system.identityModel></span></span>  
<span data-ttu-id="05dfc-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="05dfc-105">\<identityConfiguration></span></span>  
<span data-ttu-id="05dfc-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="05dfc-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="05dfc-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="05dfc-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="05dfc-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="05dfc-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05dfc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05dfc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05dfc-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="05dfc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05dfc-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="05dfc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05dfc-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="05dfc-112">Attributes</span></span>  
  
|<span data-ttu-id="05dfc-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="05dfc-113">Attribute</span></span>|<span data-ttu-id="05dfc-114">Description</span><span class="sxs-lookup"><span data-stu-id="05dfc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05dfc-115">type</span><span class="sxs-lookup"><span data-stu-id="05dfc-115">type</span></span>|<span data-ttu-id="05dfc-116">Spécifie le type de programme de résolution de jetons d’émetteur.</span><span class="sxs-lookup"><span data-stu-id="05dfc-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="05dfc-117">Il doit s’agir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> de la classe ou d’un type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="05dfc-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="05dfc-118">Requis.</span><span class="sxs-lookup"><span data-stu-id="05dfc-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05dfc-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="05dfc-119">Child Elements</span></span>  
 <span data-ttu-id="05dfc-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="05dfc-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05dfc-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="05dfc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="05dfc-122">Élément</span><span class="sxs-lookup"><span data-stu-id="05dfc-122">Element</span></span>|<span data-ttu-id="05dfc-123">Description</span><span class="sxs-lookup"><span data-stu-id="05dfc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05dfc-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="05dfc-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="05dfc-125">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="05dfc-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05dfc-126">Notes</span><span class="sxs-lookup"><span data-stu-id="05dfc-126">Remarks</span></span>  
 <span data-ttu-id="05dfc-127">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="05dfc-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="05dfc-128">Il est utilisé pour récupérer le matériel de chiffrement utilisé pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="05dfc-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="05dfc-129">Vous devez spécifier l' `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="05dfc-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="05dfc-130">Le type spécifié peut être <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="05dfc-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="05dfc-131">Certains gestionnaires de jetons vous permettent de spécifier les paramètres du programme de résolution de jetons d’émetteur dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="05dfc-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="05dfc-132">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="05dfc-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05dfc-133">La spécification `<issuerTokenResolver>` de l’élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="05dfc-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="05dfc-134">Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="05dfc-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05dfc-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="05dfc-135">Example</span></span>  
 <span data-ttu-id="05dfc-136">Le code XML suivant montre la configuration d’un programme de résolution de jetons d’émetteur basé sur une classe personnalisée qui <xref:System.IdentityModel.Tokens.IssuerTokenResolver>dérive de.</span><span class="sxs-lookup"><span data-stu-id="05dfc-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="05dfc-137">Le programme de résolution de jetons gère un dictionnaire de paires de clés d’audience qui est initialisé à partir d'`<AddAudienceKeyPair>`un élément de configuration personnalisé () défini pour la classe.</span><span class="sxs-lookup"><span data-stu-id="05dfc-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="05dfc-138">La classe substitue la <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> méthode pour traiter cet élément.</span><span class="sxs-lookup"><span data-stu-id="05dfc-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="05dfc-139">Le remplacement est illustré dans l’exemple suivant: Toutefois, les méthodes qu’il appelle ne sont pas affichées par souci de concision.</span><span class="sxs-lookup"><span data-stu-id="05dfc-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="05dfc-140">Pour obtenir un exemple complet, consultez `CustomToken` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="05dfc-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="05dfc-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="05dfc-141">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="05dfc-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05dfc-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
