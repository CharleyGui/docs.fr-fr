---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252140"
---
# <a name="certificatereference"></a><span data-ttu-id="5bfa8-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="5bfa8-101">\<certificateReference></span></span>
<span data-ttu-id="5bfa8-102">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="5bfa8-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5bfa8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bfa8-104">&nbsp;&nbsp;[ **\<System. identityModel. services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="5bfa8-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="5bfa8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5bfa8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="5bfa8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="5bfa8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="5bfa8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**</span><span class="sxs-lookup"><span data-stu-id="5bfa8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfa8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bfa8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bfa8-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5bfa8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5bfa8-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bfa8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="5bfa8-111">Attributes</span></span>  
  
|<span data-ttu-id="5bfa8-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="5bfa8-112">Attribute</span></span>|<span data-ttu-id="5bfa8-113">Description</span><span class="sxs-lookup"><span data-stu-id="5bfa8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bfa8-114">storeName</span><span class="sxs-lookup"><span data-stu-id="5bfa8-114">storeName</span></span>|<span data-ttu-id="5bfa8-115">Nom du magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="5bfa8-116">La valeur par défaut est « My ».</span><span class="sxs-lookup"><span data-stu-id="5bfa8-116">The default is "My".</span></span> <span data-ttu-id="5bfa8-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-117">Optional.</span></span>|  
|<span data-ttu-id="5bfa8-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="5bfa8-118">storeLocation</span></span>|<span data-ttu-id="5bfa8-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie l’emplacement du magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="5bfa8-120">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="5bfa8-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="5bfa8-121">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-121">Optional.</span></span>|  
|<span data-ttu-id="5bfa8-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="5bfa8-122">x509FindType</span></span>|<span data-ttu-id="5bfa8-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Valeur qui spécifie le type de recherche à exécuter.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="5bfa8-124">La valeur par défaut est « FindBySubjectDistinguishedName ».</span><span class="sxs-lookup"><span data-stu-id="5bfa8-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="5bfa8-125">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-125">Optional.</span></span>|  
|<span data-ttu-id="5bfa8-126">findValue</span><span class="sxs-lookup"><span data-stu-id="5bfa8-126">findValue</span></span>|<span data-ttu-id="5bfa8-127">Valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="5bfa8-128">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-128">Optional.</span></span>|  
|<span data-ttu-id="5bfa8-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="5bfa8-129">isChainIncluded</span></span>|<span data-ttu-id="5bfa8-130">Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="5bfa8-131">La valeur par défaut est « true ». la validation est effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="5bfa8-132">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bfa8-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5bfa8-133">Child Elements</span></span>  
 <span data-ttu-id="5bfa8-134">Aucun</span><span class="sxs-lookup"><span data-stu-id="5bfa8-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bfa8-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5bfa8-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5bfa8-136">Élément</span><span class="sxs-lookup"><span data-stu-id="5bfa8-136">Element</span></span>|<span data-ttu-id="5bfa8-137">Description</span><span class="sxs-lookup"><span data-stu-id="5bfa8-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bfa8-138">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="5bfa8-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="5bfa8-139">Configure le certificat utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bfa8-140">Notes</span><span class="sxs-lookup"><span data-stu-id="5bfa8-140">Remarks</span></span>  
 <span data-ttu-id="5bfa8-141">L' `<certificateReference>` élément spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="5bfa8-142">Lorsqu’il est spécifié en tant qu’élément enfant de `<serviceCertificate>` l’élément, il spécifie l’emplacement et les paramètres de vérification du certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="5bfa8-143">L' `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="5bfa8-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
