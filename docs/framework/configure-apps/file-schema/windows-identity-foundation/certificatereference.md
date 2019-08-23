---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: da8ea128466457409334cd0b4ee3246a923f969a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941928"
---
# <a name="certificatereference"></a><span data-ttu-id="63195-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="63195-101">\<certificateReference></span></span>
<span data-ttu-id="63195-102">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="63195-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="63195-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="63195-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="63195-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="63195-104">\<federationConfiguration></span></span>  
<span data-ttu-id="63195-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="63195-105">\<serviceCertificate></span></span>  
<span data-ttu-id="63195-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="63195-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63195-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63195-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63195-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="63195-108">Attributes and Elements</span></span>  
 <span data-ttu-id="63195-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="63195-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63195-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="63195-110">Attributes</span></span>  
  
|<span data-ttu-id="63195-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="63195-111">Attribute</span></span>|<span data-ttu-id="63195-112">Description</span><span class="sxs-lookup"><span data-stu-id="63195-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63195-113">storeName</span><span class="sxs-lookup"><span data-stu-id="63195-113">storeName</span></span>|<span data-ttu-id="63195-114">Nom du magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="63195-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="63195-115">La valeur par défaut est «My».</span><span class="sxs-lookup"><span data-stu-id="63195-115">The default is "My".</span></span> <span data-ttu-id="63195-116">facultatif.</span><span class="sxs-lookup"><span data-stu-id="63195-116">Optional.</span></span>|  
|<span data-ttu-id="63195-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="63195-117">storeLocation</span></span>|<span data-ttu-id="63195-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie l’emplacement du magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="63195-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="63195-119">La valeur par défaut est «LocalMachine».</span><span class="sxs-lookup"><span data-stu-id="63195-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="63195-120">facultatif.</span><span class="sxs-lookup"><span data-stu-id="63195-120">Optional.</span></span>|  
|<span data-ttu-id="63195-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="63195-121">x509FindType</span></span>|<span data-ttu-id="63195-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Valeur qui spécifie le type de recherche à exécuter.</span><span class="sxs-lookup"><span data-stu-id="63195-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="63195-123">La valeur par défaut est «FindBySubjectDistinguishedName».</span><span class="sxs-lookup"><span data-stu-id="63195-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="63195-124">facultatif.</span><span class="sxs-lookup"><span data-stu-id="63195-124">Optional.</span></span>|  
|<span data-ttu-id="63195-125">findValue</span><span class="sxs-lookup"><span data-stu-id="63195-125">findValue</span></span>|<span data-ttu-id="63195-126">Valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="63195-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="63195-127">facultatif.</span><span class="sxs-lookup"><span data-stu-id="63195-127">Optional.</span></span>|  
|<span data-ttu-id="63195-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="63195-128">isChainIncluded</span></span>|<span data-ttu-id="63195-129">Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="63195-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="63195-130">La valeur par défaut est «true». la validation est effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="63195-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="63195-131">facultatif.</span><span class="sxs-lookup"><span data-stu-id="63195-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63195-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63195-132">Child Elements</span></span>  
 <span data-ttu-id="63195-133">Aucun</span><span class="sxs-lookup"><span data-stu-id="63195-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63195-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63195-134">Parent Elements</span></span>  
  
|<span data-ttu-id="63195-135">Élément</span><span class="sxs-lookup"><span data-stu-id="63195-135">Element</span></span>|<span data-ttu-id="63195-136">Description</span><span class="sxs-lookup"><span data-stu-id="63195-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63195-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="63195-137">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="63195-138">Configure le certificat utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="63195-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63195-139">Notes</span><span class="sxs-lookup"><span data-stu-id="63195-139">Remarks</span></span>  
 <span data-ttu-id="63195-140">L' `<certificateReference>` élément spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="63195-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="63195-141">Lorsqu’il est spécifié en tant qu’élément enfant de `<serviceCertificate>` l’élément, il spécifie l’emplacement et les paramètres de vérification du certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="63195-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="63195-142">L' `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="63195-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
