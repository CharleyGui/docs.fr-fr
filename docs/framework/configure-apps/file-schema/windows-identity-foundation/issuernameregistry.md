---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942666"
---
# <a name="issuernameregistry"></a><span data-ttu-id="8a476-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="8a476-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="8a476-102">Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="8a476-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="8a476-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8a476-103">\<system.identityModel></span></span>  
<span data-ttu-id="8a476-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8a476-104">\<identityConfiguration></span></span>  
<span data-ttu-id="8a476-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8a476-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8a476-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8a476-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="8a476-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="8a476-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a476-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a476-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a476-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8a476-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8a476-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8a476-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a476-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="8a476-111">Attributes</span></span>  
  
|<span data-ttu-id="8a476-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="8a476-112">Attribute</span></span>|<span data-ttu-id="8a476-113">Description</span><span class="sxs-lookup"><span data-stu-id="8a476-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a476-114">type</span><span class="sxs-lookup"><span data-stu-id="8a476-114">type</span></span>|<span data-ttu-id="8a476-115">Type qui dérive de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="8a476-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="8a476-116">Pour plus d’informations sur la façon de spécifier `type`un personnalisé, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="8a476-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a476-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8a476-117">Child Elements</span></span>  
  
|<span data-ttu-id="8a476-118">Élément</span><span class="sxs-lookup"><span data-stu-id="8a476-118">Element</span></span>|<span data-ttu-id="8a476-119">Description</span><span class="sxs-lookup"><span data-stu-id="8a476-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a476-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="8a476-120">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="8a476-121">Lorsque l' `type` attribut spécifie le registre des noms d’émetteurs basés sur la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> configuration (la classe), l' [ \<élément trustedIssuers >](trustedissuers.md) doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="8a476-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="8a476-122">L' `<add>` `<clear>` [ \<élément trustedIssuers >](trustedissuers.md) peut prendre des éléments, `<remove>` ou en tant qu’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="8a476-122">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8a476-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8a476-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8a476-124">Élément</span><span class="sxs-lookup"><span data-stu-id="8a476-124">Element</span></span>|<span data-ttu-id="8a476-125">Description</span><span class="sxs-lookup"><span data-stu-id="8a476-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a476-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8a476-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8a476-127">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8a476-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a476-128">Notes</span><span class="sxs-lookup"><span data-stu-id="8a476-128">Remarks</span></span>  
 <span data-ttu-id="8a476-129">Tous les jetons d’émetteur sont validés à l’aide d’un registre de noms d’émetteurs.</span><span class="sxs-lookup"><span data-stu-id="8a476-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="8a476-130">Il s’agit d’un objet qui dérive <xref:System.IdentityModel.Tokens.IssuerNameRegistry> de la classe.</span><span class="sxs-lookup"><span data-stu-id="8a476-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="8a476-131">Le registre des noms d’émetteurs est utilisé pour associer un nom mnémonique aux documents de chiffrement nécessaires à la vérification des signatures des jetons produits par l’émetteur correspondant.</span><span class="sxs-lookup"><span data-stu-id="8a476-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="8a476-132">Le registre des noms d’émetteurs gère une liste des émetteurs qui sont approuvés par l’application de partie de confiance (RP).</span><span class="sxs-lookup"><span data-stu-id="8a476-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="8a476-133">Le type du registre des noms d’émetteurs est spécifié à l' `type` aide de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="8a476-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="8a476-134">L' `<issuerNameRegistry>` élément peut avoir un ou plusieurs éléments enfants qui fournissent la configuration pour le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="8a476-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="8a476-135">Vous fournissez la logique qui traite ces éléments enfants en substituant <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> la méthode.</span><span class="sxs-lookup"><span data-stu-id="8a476-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="8a476-136">WIF fournit un type de registre de nom d’émetteur unique, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="8a476-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="8a476-137">Cette classe utilise un ensemble de certificats d’émetteurs approuvés spécifiés dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="8a476-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="8a476-138">Il nécessite un élément de configuration enfant `<trustedIssuers>`,, sous lequel la collection de certificats d’émetteurs approuvés est configurée.</span><span class="sxs-lookup"><span data-stu-id="8a476-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="8a476-139">Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat et sont ajoutés `<add>`ou `<clear>`supprimés de `<remove>` la collection à l’aide des éléments, ou.</span><span class="sxs-lookup"><span data-stu-id="8a476-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="8a476-140">L' `<issuerNameRegistry>` élément est représenté par la <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.</span><span class="sxs-lookup"><span data-stu-id="8a476-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a476-141">La spécification `<issuerNameRegistry>` de l’élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="8a476-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8a476-142">Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="8a476-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a476-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a476-143">Example</span></span>  
 <span data-ttu-id="8a476-144">Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.</span><span class="sxs-lookup"><span data-stu-id="8a476-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a476-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a476-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
