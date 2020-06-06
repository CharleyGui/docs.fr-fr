---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152812"
---
# \<certificateReference>
<span data-ttu-id="78d40-101">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="78d40-101">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="78d40-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78d40-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78d40-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="78d40-103">Attributes and Elements</span></span>  
 <span data-ttu-id="78d40-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="78d40-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78d40-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="78d40-105">Attributes</span></span>  
  
|<span data-ttu-id="78d40-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="78d40-106">Attribute</span></span>|<span data-ttu-id="78d40-107">Description</span><span class="sxs-lookup"><span data-stu-id="78d40-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78d40-108">storeName</span><span class="sxs-lookup"><span data-stu-id="78d40-108">storeName</span></span>|<span data-ttu-id="78d40-109">Nom du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="78d40-109">The name of the X.509 certificate store.</span></span> <span data-ttu-id="78d40-110">La valeur par défaut est « My ».</span><span class="sxs-lookup"><span data-stu-id="78d40-110">The default is "My".</span></span> <span data-ttu-id="78d40-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="78d40-111">Optional.</span></span>|  
|<span data-ttu-id="78d40-112">storeLocation</span><span class="sxs-lookup"><span data-stu-id="78d40-112">storeLocation</span></span>|<span data-ttu-id="78d40-113"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie l’emplacement du magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="78d40-113">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="78d40-114">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="78d40-114">The default value is "LocalMachine".</span></span> <span data-ttu-id="78d40-115">facultatif.</span><span class="sxs-lookup"><span data-stu-id="78d40-115">Optional.</span></span>|  
|<span data-ttu-id="78d40-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="78d40-116">x509FindType</span></span>|<span data-ttu-id="78d40-117"><xref:System.Security.Cryptography.X509Certificates.X509FindType>Valeur qui spécifie le type de recherche à exécuter.</span><span class="sxs-lookup"><span data-stu-id="78d40-117">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="78d40-118">La valeur par défaut est « FindBySubjectDistinguishedName ».</span><span class="sxs-lookup"><span data-stu-id="78d40-118">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="78d40-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="78d40-119">Optional.</span></span>|  
|<span data-ttu-id="78d40-120">findValue</span><span class="sxs-lookup"><span data-stu-id="78d40-120">findValue</span></span>|<span data-ttu-id="78d40-121">Valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="78d40-121">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="78d40-122">facultatif.</span><span class="sxs-lookup"><span data-stu-id="78d40-122">Optional.</span></span>|  
|<span data-ttu-id="78d40-123">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="78d40-123">isChainIncluded</span></span>|<span data-ttu-id="78d40-124">Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="78d40-124">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="78d40-125">La valeur par défaut est « true ». la validation est effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="78d40-125">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="78d40-126">facultatif.</span><span class="sxs-lookup"><span data-stu-id="78d40-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78d40-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="78d40-127">Child Elements</span></span>  
 <span data-ttu-id="78d40-128">Aucune</span><span class="sxs-lookup"><span data-stu-id="78d40-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78d40-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="78d40-129">Parent Elements</span></span>  
  
|<span data-ttu-id="78d40-130">Élément</span><span class="sxs-lookup"><span data-stu-id="78d40-130">Element</span></span>|<span data-ttu-id="78d40-131">Description</span><span class="sxs-lookup"><span data-stu-id="78d40-131">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="78d40-132">Configure le certificat utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="78d40-132">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78d40-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="78d40-133">Remarks</span></span>  
 <span data-ttu-id="78d40-134">L' `<certificateReference>` élément spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="78d40-134">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="78d40-135">Lorsqu’il est spécifié en tant qu’élément enfant de l' `<serviceCertificate>` élément, il spécifie l’emplacement et les paramètres de vérification du certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="78d40-135">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="78d40-136">L' `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="78d40-136">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
