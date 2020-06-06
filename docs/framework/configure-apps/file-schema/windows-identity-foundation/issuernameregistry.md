---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251968"
---
# \<issuerNameRegistry>
<span data-ttu-id="cdf3f-101">Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="cdf3f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdf3f-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdf3f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cdf3f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cdf3f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdf3f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="cdf3f-105">Attributes</span></span>  
  
|<span data-ttu-id="cdf3f-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="cdf3f-106">Attribute</span></span>|<span data-ttu-id="cdf3f-107">Description</span><span class="sxs-lookup"><span data-stu-id="cdf3f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdf3f-108">type</span><span class="sxs-lookup"><span data-stu-id="cdf3f-108">type</span></span>|<span data-ttu-id="cdf3f-109">Type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="cdf3f-110">Pour plus d’informations sur la façon de spécifier un personnalisé `type` , consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="cdf3f-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdf3f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cdf3f-111">Child Elements</span></span>  
  
|<span data-ttu-id="cdf3f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="cdf3f-112">Element</span></span>|<span data-ttu-id="cdf3f-113">Description</span><span class="sxs-lookup"><span data-stu-id="cdf3f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="cdf3f-114">Lorsque l' `type` attribut spécifie le registre des noms d’émetteurs basés sur la configuration (la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe), l' [\<trustedIssuers>](trustedissuers.md) élément doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="cdf3f-115">L' [\<trustedIssuers>](trustedissuers.md) élément peut prendre `<add>` des `<clear>` éléments, ou `<remove>` en tant qu’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdf3f-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cdf3f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cdf3f-117">Élément</span><span class="sxs-lookup"><span data-stu-id="cdf3f-117">Element</span></span>|<span data-ttu-id="cdf3f-118">Description</span><span class="sxs-lookup"><span data-stu-id="cdf3f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="cdf3f-119">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf3f-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="cdf3f-120">Remarks</span></span>  
 <span data-ttu-id="cdf3f-121">Tous les jetons d’émetteur sont validés à l’aide d’un registre de noms d’émetteurs.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="cdf3f-122">Il s’agit d’un objet qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="cdf3f-123">Le registre des noms d’émetteurs est utilisé pour associer un nom mnémonique aux documents de chiffrement nécessaires à la vérification des signatures des jetons produits par l’émetteur correspondant.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="cdf3f-124">Le registre des noms d’émetteurs gère une liste des émetteurs qui sont approuvés par l’application de partie de confiance (RP).</span><span class="sxs-lookup"><span data-stu-id="cdf3f-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="cdf3f-125">Le type du registre des noms d’émetteurs est spécifié à l’aide de l' `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="cdf3f-126">L' `<issuerNameRegistry>` élément peut avoir un ou plusieurs éléments enfants qui fournissent la configuration pour le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="cdf3f-127">Vous fournissez la logique qui traite ces éléments enfants en substituant la <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="cdf3f-128">WIF fournit un type de registre de nom d’émetteur unique, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="cdf3f-129">Cette classe utilise un ensemble de certificats d’émetteurs approuvés spécifiés dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="cdf3f-130">Il nécessite un élément de configuration enfant, `<trustedIssuers>` , sous lequel la collection de certificats d’émetteurs approuvés est configurée.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="cdf3f-131">Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat et sont ajoutés ou supprimés de la collection à l’aide des `<add>` `<clear>` éléments, ou `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="cdf3f-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="cdf3f-132">L' `<issuerNameRegistry>` élément est représenté par la <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdf3f-133">La spécification de l' `<issuerNameRegistry>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="cdf3f-134">Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdf3f-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="cdf3f-135">Example</span></span>  
 <span data-ttu-id="cdf3f-136">Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.</span><span class="sxs-lookup"><span data-stu-id="cdf3f-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdf3f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdf3f-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
