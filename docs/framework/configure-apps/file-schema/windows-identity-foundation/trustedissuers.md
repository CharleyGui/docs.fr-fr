---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944271"
---
# <a name="trustedissuers"></a><span data-ttu-id="11815-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="11815-101">\<trustedIssuers></span></span>
<span data-ttu-id="11815-102">Configure la liste des certificats d’émetteurs approuvés utilisés par le registre des noms d’émetteurs basés sur la configuration<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>().</span><span class="sxs-lookup"><span data-stu-id="11815-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="11815-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="11815-103">\<system.identityModel></span></span>  
<span data-ttu-id="11815-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="11815-104">\<identityConfiguration></span></span>  
<span data-ttu-id="11815-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="11815-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="11815-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="11815-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="11815-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="11815-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="11815-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="11815-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11815-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11815-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11815-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="11815-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11815-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="11815-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11815-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="11815-112">Attributes</span></span>  
 <span data-ttu-id="11815-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="11815-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11815-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="11815-114">Child Elements</span></span>  
  
|<span data-ttu-id="11815-115">Élément</span><span class="sxs-lookup"><span data-stu-id="11815-115">Element</span></span>|<span data-ttu-id="11815-116">Description</span><span class="sxs-lookup"><span data-stu-id="11815-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="11815-117">Ajoute un certificat à la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="11815-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="11815-118">Le certificat est spécifié avec l' `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="11815-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="11815-119">Cet attribut est obligatoire et doit contenir la forme encodée ASN. 1 de l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="11815-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="11815-120">L' `name` attribut est facultatif et peut être utilisé pour spécifier un nom convivial pour le certificat.</span><span class="sxs-lookup"><span data-stu-id="11815-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="11815-121">Efface tous les certificats de la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="11815-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="11815-122">Supprime un certificat de la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="11815-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="11815-123">Le certificat est spécifié avec l' `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="11815-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="11815-124">Cet attribut est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="11815-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11815-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="11815-125">Parent Elements</span></span>  
  
|<span data-ttu-id="11815-126">Élément</span><span class="sxs-lookup"><span data-stu-id="11815-126">Element</span></span>|<span data-ttu-id="11815-127">Description</span><span class="sxs-lookup"><span data-stu-id="11815-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11815-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="11815-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="11815-129">Configure le registre des noms d’émetteurs.</span><span class="sxs-lookup"><span data-stu-id="11815-129">Configures the issuer name registry.</span></span> <span data-ttu-id="11815-130">**Important :**  L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe `<trustedIssuers>` pour que l’élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="11815-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11815-131">Notes</span><span class="sxs-lookup"><span data-stu-id="11815-131">Remarks</span></span>  
 <span data-ttu-id="11815-132">Windows Identity Foundation (WIF) fournit une implémentation unique de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> la classe prête à l’emploi, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> la classe.</span><span class="sxs-lookup"><span data-stu-id="11815-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="11815-133">Le registre des noms d’émetteurs de configuration gère une liste d’émetteurs approuvés qui est chargée à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="11815-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="11815-134">La liste associe chaque nom d’émetteur au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="11815-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="11815-135">La liste des certificats d’émetteurs approuvés est spécifiée sous l' `<trustedIssuers>` élément.</span><span class="sxs-lookup"><span data-stu-id="11815-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="11815-136">Chaque élément de la liste associe un nom d’émetteur mnémonique au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="11815-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="11815-137">Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat `<add>` et sont ajoutés à la collection à l’aide de l’élément.</span><span class="sxs-lookup"><span data-stu-id="11815-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="11815-138">Vous pouvez effacer ou supprimer les émetteurs (certificats) de la liste à l’aide `<clear>` des `<remove>` éléments et.</span><span class="sxs-lookup"><span data-stu-id="11815-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="11815-139">L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe `<trustedIssuers>` pour que l’élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="11815-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11815-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="11815-140">Example</span></span>  
 <span data-ttu-id="11815-141">Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.</span><span class="sxs-lookup"><span data-stu-id="11815-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11815-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11815-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
