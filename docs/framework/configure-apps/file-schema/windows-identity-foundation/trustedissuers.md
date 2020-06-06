---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251758"
---
# \<trustedIssuers>
<span data-ttu-id="40ae8-101">Configure la liste des certificats d’émetteurs approuvés utilisés par le registre des noms d’émetteurs basés sur la configuration ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> ).</span><span class="sxs-lookup"><span data-stu-id="40ae8-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="40ae8-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40ae8-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40ae8-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="40ae8-103">Attributes and Elements</span></span>  
 <span data-ttu-id="40ae8-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="40ae8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40ae8-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="40ae8-105">Attributes</span></span>  
 <span data-ttu-id="40ae8-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="40ae8-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40ae8-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40ae8-107">Child Elements</span></span>  
  
|<span data-ttu-id="40ae8-108">Élément</span><span class="sxs-lookup"><span data-stu-id="40ae8-108">Element</span></span>|<span data-ttu-id="40ae8-109">Description</span><span class="sxs-lookup"><span data-stu-id="40ae8-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="40ae8-110">Ajoute un certificat à la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="40ae8-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="40ae8-111">Le certificat est spécifié avec l' `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="40ae8-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="40ae8-112">Cet attribut est obligatoire et doit contenir la forme encodée ASN. 1 de l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="40ae8-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="40ae8-113">L' `name` attribut est facultatif et peut être utilisé pour spécifier un nom convivial pour le certificat.</span><span class="sxs-lookup"><span data-stu-id="40ae8-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="40ae8-114">Efface tous les certificats de la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="40ae8-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="40ae8-115">Supprime un certificat de la collection d’émetteurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="40ae8-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="40ae8-116">Le certificat est spécifié avec l' `thumbprint` attribut.</span><span class="sxs-lookup"><span data-stu-id="40ae8-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="40ae8-117">Cet attribut est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="40ae8-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40ae8-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40ae8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="40ae8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="40ae8-119">Element</span></span>|<span data-ttu-id="40ae8-120">Description</span><span class="sxs-lookup"><span data-stu-id="40ae8-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="40ae8-121">Configure le registre des noms d’émetteurs.</span><span class="sxs-lookup"><span data-stu-id="40ae8-121">Configures the issuer name registry.</span></span> <span data-ttu-id="40ae8-122">**Important :**  L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe pour que l' `<trustedIssuers>` élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="40ae8-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40ae8-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="40ae8-123">Remarks</span></span>  
 <span data-ttu-id="40ae8-124">Windows Identity Foundation (WIF) fournit une implémentation unique de la <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe prête à l’emploi, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="40ae8-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="40ae8-125">Le registre des noms d’émetteurs de configuration gère une liste d’émetteurs approuvés qui est chargée à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="40ae8-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="40ae8-126">La liste associe chaque nom d’émetteur au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="40ae8-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="40ae8-127">La liste des certificats d’émetteurs approuvés est spécifiée sous l' `<trustedIssuers>` élément.</span><span class="sxs-lookup"><span data-stu-id="40ae8-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="40ae8-128">Chaque élément de la liste associe un nom d’émetteur mnémonique au certificat X. 509 nécessaire pour vérifier la signature des jetons produits par l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="40ae8-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="40ae8-129">Les certificats approuvés sont spécifiés à l’aide de la forme encodée ASN. 1 de l’empreinte numérique du certificat et sont ajoutés à la collection à l’aide de l' `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="40ae8-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="40ae8-130">Vous pouvez effacer ou supprimer les émetteurs (certificats) de la liste à l’aide `<clear>` des `<remove>` éléments et.</span><span class="sxs-lookup"><span data-stu-id="40ae8-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="40ae8-131">L' `type` attribut de l' `<issuerNameRegistry>` élément doit faire référence <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> à la classe pour que l' `<trustedIssuers>` élément soit valide.</span><span class="sxs-lookup"><span data-stu-id="40ae8-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40ae8-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="40ae8-132">Example</span></span>  
 <span data-ttu-id="40ae8-133">Le code XML suivant montre comment spécifier le registre des noms d’émetteurs basés sur la configuration.</span><span class="sxs-lookup"><span data-stu-id="40ae8-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40ae8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ae8-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
