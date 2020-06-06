---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152669"
---
# \<issuerTokenResolver>
<span data-ttu-id="4dd55-101">Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="4dd55-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4dd55-102">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="4dd55-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="4dd55-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dd55-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dd55-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4dd55-104">Attributes and Elements</span></span>  
 <span data-ttu-id="4dd55-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4dd55-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dd55-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="4dd55-106">Attributes</span></span>  
  
|<span data-ttu-id="4dd55-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="4dd55-107">Attribute</span></span>|<span data-ttu-id="4dd55-108">Description</span><span class="sxs-lookup"><span data-stu-id="4dd55-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dd55-109">type</span><span class="sxs-lookup"><span data-stu-id="4dd55-109">type</span></span>|<span data-ttu-id="4dd55-110">Spécifie le type de programme de résolution de jetons d’émetteur.</span><span class="sxs-lookup"><span data-stu-id="4dd55-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="4dd55-111">Il doit s’agir de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou d’un type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="4dd55-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="4dd55-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4dd55-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dd55-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4dd55-113">Child Elements</span></span>  
 <span data-ttu-id="4dd55-114">Aucune</span><span class="sxs-lookup"><span data-stu-id="4dd55-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dd55-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4dd55-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4dd55-116">Élément</span><span class="sxs-lookup"><span data-stu-id="4dd55-116">Element</span></span>|<span data-ttu-id="4dd55-117">Description</span><span class="sxs-lookup"><span data-stu-id="4dd55-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="4dd55-118">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4dd55-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dd55-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="4dd55-119">Remarks</span></span>  
 <span data-ttu-id="4dd55-120">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="4dd55-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="4dd55-121">Il est utilisé pour récupérer le matériel de chiffrement utilisé pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="4dd55-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="4dd55-122">Vous devez spécifier l' `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="4dd55-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="4dd55-123">Le type spécifié peut être <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="4dd55-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="4dd55-124">Certains gestionnaires de jetons vous permettent de spécifier les paramètres du programme de résolution de jetons d’émetteur dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="4dd55-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="4dd55-125">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4dd55-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dd55-126">La spécification de l' `<issuerTokenResolver>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="4dd55-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="4dd55-127">Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="4dd55-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd55-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="4dd55-128">Example</span></span>  
 <span data-ttu-id="4dd55-129">Le code XML suivant montre la configuration d’un programme de résolution de jetons d’émetteur basé sur une classe personnalisée qui dérive de <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="4dd55-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="4dd55-130">Le programme de résolution de jetons gère un dictionnaire de paires de clés d’audience qui est initialisé à partir d’un élément de configuration personnalisé ( `<AddAudienceKeyPair>` ) défini pour la classe.</span><span class="sxs-lookup"><span data-stu-id="4dd55-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="4dd55-131">La classe substitue la <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> méthode pour traiter cet élément.</span><span class="sxs-lookup"><span data-stu-id="4dd55-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="4dd55-132">Le remplacement est illustré dans l’exemple suivant : Toutefois, les méthodes qu’il appelle ne sont pas affichées par souci de concision.</span><span class="sxs-lookup"><span data-stu-id="4dd55-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="4dd55-133">Pour obtenir un exemple complet, consultez l’exemple `CustomToken` .</span><span class="sxs-lookup"><span data-stu-id="4dd55-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="4dd55-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="4dd55-134">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="4dd55-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dd55-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
