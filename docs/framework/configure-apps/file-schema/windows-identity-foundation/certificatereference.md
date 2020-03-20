---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152812"
---
# <a name="certificatereference"></a><span data-ttu-id="f86c3-101">\<certificatReference></span><span class="sxs-lookup"><span data-stu-id="f86c3-101">\<certificateReference></span></span>
<span data-ttu-id="f86c3-102">Spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f86c3-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="f86c3-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f86c3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f86c3-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="f86c3-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="f86c3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<fédérationConfiguration>**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f86c3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="f86c3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="f86c3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="f86c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificatReference>**</span><span class="sxs-lookup"><span data-stu-id="f86c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86c3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f86c3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f86c3-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f86c3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f86c3-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f86c3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f86c3-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f86c3-111">Attributes</span></span>  
  
|<span data-ttu-id="f86c3-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f86c3-112">Attribute</span></span>|<span data-ttu-id="f86c3-113">Description</span><span class="sxs-lookup"><span data-stu-id="f86c3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f86c3-114">storeName</span><span class="sxs-lookup"><span data-stu-id="f86c3-114">storeName</span></span>|<span data-ttu-id="f86c3-115">Nom du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="f86c3-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="f86c3-116">La valeur par défaut est "My".</span><span class="sxs-lookup"><span data-stu-id="f86c3-116">The default is "My".</span></span> <span data-ttu-id="f86c3-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f86c3-117">Optional.</span></span>|  
|<span data-ttu-id="f86c3-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="f86c3-118">storeLocation</span></span>|<span data-ttu-id="f86c3-119">Une <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui précise l’emplacement du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="f86c3-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="f86c3-120">La valeur par défaut est "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="f86c3-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="f86c3-121">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f86c3-121">Optional.</span></span>|  
|<span data-ttu-id="f86c3-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="f86c3-122">x509FindType</span></span>|<span data-ttu-id="f86c3-123">Une <xref:System.Security.Cryptography.X509Certificates.X509FindType> valeur qui spécifie le type de recherche qui doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="f86c3-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="f86c3-124">La valeur par défaut est "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="f86c3-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="f86c3-125">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f86c3-125">Optional.</span></span>|  
|<span data-ttu-id="f86c3-126">findValue</span><span class="sxs-lookup"><span data-stu-id="f86c3-126">findValue</span></span>|<span data-ttu-id="f86c3-127">Valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="f86c3-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="f86c3-128">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f86c3-128">Optional.</span></span>|  
|<span data-ttu-id="f86c3-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="f86c3-129">isChainIncluded</span></span>|<span data-ttu-id="f86c3-130">Précise si la validation doit être effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="f86c3-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="f86c3-131">La valeur par défaut est "vraie"; validation est effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="f86c3-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="f86c3-132">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f86c3-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f86c3-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f86c3-133">Child Elements</span></span>  
 <span data-ttu-id="f86c3-134">None</span><span class="sxs-lookup"><span data-stu-id="f86c3-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f86c3-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f86c3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f86c3-136">Élément</span><span class="sxs-lookup"><span data-stu-id="f86c3-136">Element</span></span>|<span data-ttu-id="f86c3-137">Description</span><span class="sxs-lookup"><span data-stu-id="f86c3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f86c3-138">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="f86c3-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="f86c3-139">Configure le certificat utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="f86c3-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f86c3-140">Notes </span><span class="sxs-lookup"><span data-stu-id="f86c3-140">Remarks</span></span>  
 <span data-ttu-id="f86c3-141">L’élément `<certificateReference>` spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f86c3-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="f86c3-142">Lorsqu’il est spécifié comme `<serviceCertificate>` l’élément enfant de l’élément, il spécifie les paramètres de localisation et de vérification du certificat X.509 qui est utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="f86c3-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="f86c3-143">L’élément `<certificateReference>` est représenté <xref:System.ServiceModel.Configuration.CertificateReferenceElement> par la classe.</span><span class="sxs-lookup"><span data-stu-id="f86c3-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
