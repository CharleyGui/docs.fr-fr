---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251758"
---
# <a name="trustedissuers"></a><span data-ttu-id="22a3a-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="22a3a-101">\<trustedIssuers></span></span>
<span data-ttu-id="22a3a-102">Configure la liste des certificats d’émetteurs approuvés utilisés par le registre des noms d’émetteurs basés sur la configuration<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>().</span><span class="sxs-lookup"><span data-stu-id="22a3a-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
<span data-ttu-id="22a3a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22a3a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22a3a-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="22a3a-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="22a3a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="22a3a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="22a3a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="22a3a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="22a3a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="22a3a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="22a3a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerNameRegistry >** ](issuernameregistry.md)</span><span class="sxs-lookup"><span data-stu-id="22a3a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)</span></span>\
<span data-ttu-id="22a3a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trustedIssuers >**</span><span class="sxs-lookup"><span data-stu-id="22a3a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a3a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22a3a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22a3a-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="22a3a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="22a3a-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="22a3a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22a3a-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="22a3a-113">Attributes</span></span>  
 <span data-ttu-id="22a3a-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="22a3a-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="22a3a-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="22a3a-115">Child Elements</span></span>  
  
|<span data-ttu-id="22a3a-116">Élément</span><span class="sxs-lookup"><span data-stu-id="22a3a-116">Element</span></span>|<span data-ttu-id="22a3a-117">Description</span><span class="sxs-lookup"><span data-stu-id="22a3a-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="22a3a-118">Ajoute un certificat à la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="22a3a-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="22a3a-119">Le certificat est spécifié avec l' `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="22a3a-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="22a3a-120">Cet attribut est obligatoire et doit contenir la forme encodée ASN. 1 de l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="22a3a-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="22a3a-121">L' `name` attribut est facultatif et peut être utilisé pour spécifier un nom convivial pour le certificat.</span><span class="sxs-lookup"><span data-stu-id="22a3a-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="22a3a-122">Efface tous les certificats de la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="22a3a-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="22a3a-123">Supprime un certificat de la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="22a3a-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="22a3a-124">Le certificat est spécifié avec l' `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="22a3a-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="22a3a-125">Cet attribut est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="22a3a-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22a3a-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="22a3a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="22a3a-127">Élément</span><span class="sxs-lookup"><span data-stu-id="22a3a-127">Element</span></span>|<span data-ttu-id="22a3a-128">Description</span><span class="sxs-lookup"><span data-stu-id="22a3a-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22a3a-129">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="22a3a-129">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="22a3a-130">Configure le registre des noms d’émetteurs.</span><span class="sxs-lookup"><span data-stu-id="22a3a-130">Configures the issuer name registry.</span></span> <span data-ttu-id="22a3a-131">**Important :**  L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe `<trustedIssuers>` pour que l’élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="22a3a-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22a3a-132">Notes</span><span class="sxs-lookup"><span data-stu-id="22a3a-132">Remarks</span></span>  
 <span data-ttu-id="22a3a-133">Windows Identity Foundation (WIF) fournit une implémentation unique de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> la classe prête à l’emploi, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> la classe.</span><span class="sxs-lookup"><span data-stu-id="22a3a-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="22a3a-134">Le registre des noms d’émetteurs de configuration gère une liste d’émetteurs approuvés qui est chargée à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="22a3a-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="22a3a-135">La liste associe chaque nom d’émetteur au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="22a3a-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="22a3a-136">La liste des certificats d’émetteurs approuvés est spécifiée sous l' `<trustedIssuers>` élément.</span><span class="sxs-lookup"><span data-stu-id="22a3a-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="22a3a-137">Chaque élément de la liste associe un nom d’émetteur mnémonique au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="22a3a-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="22a3a-138">Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat `<add>` et sont ajoutés à la collection à l’aide de l’élément.</span><span class="sxs-lookup"><span data-stu-id="22a3a-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="22a3a-139">Vous pouvez effacer ou supprimer les émetteurs (certificats) de la liste à l’aide `<clear>` des `<remove>` éléments et.</span><span class="sxs-lookup"><span data-stu-id="22a3a-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="22a3a-140">L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe `<trustedIssuers>` pour que l’élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="22a3a-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22a3a-141">Exemples</span><span class="sxs-lookup"><span data-stu-id="22a3a-141">Example</span></span>  
 <span data-ttu-id="22a3a-142">Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.</span><span class="sxs-lookup"><span data-stu-id="22a3a-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22a3a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22a3a-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
