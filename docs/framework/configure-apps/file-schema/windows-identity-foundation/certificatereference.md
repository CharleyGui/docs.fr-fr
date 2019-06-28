---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c7dc9cfff15e70eff0086cfd98a19f3360ab8bb0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423027"
---
# <a name="certificatereference"></a><span data-ttu-id="047b8-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="047b8-101">\<certificateReference></span></span>
<span data-ttu-id="047b8-102">Spécifie les paramètres qui sont utilisés pour rechercher et valider le certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="047b8-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="047b8-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="047b8-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="047b8-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="047b8-104">\<federationConfiguration></span></span>  
<span data-ttu-id="047b8-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="047b8-105">\<serviceCertificate></span></span>  
<span data-ttu-id="047b8-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="047b8-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047b8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="047b8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="047b8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="047b8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="047b8-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="047b8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="047b8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="047b8-110">Attributes</span></span>  
  
|<span data-ttu-id="047b8-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="047b8-111">Attribute</span></span>|<span data-ttu-id="047b8-112">Description</span><span class="sxs-lookup"><span data-stu-id="047b8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="047b8-113">storeName</span><span class="sxs-lookup"><span data-stu-id="047b8-113">storeName</span></span>|<span data-ttu-id="047b8-114">Le nom du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="047b8-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="047b8-115">La valeur par défaut est « My ».</span><span class="sxs-lookup"><span data-stu-id="047b8-115">The default is "My".</span></span> <span data-ttu-id="047b8-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="047b8-116">Optional.</span></span>|  
|<span data-ttu-id="047b8-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="047b8-117">storeLocation</span></span>|<span data-ttu-id="047b8-118">Un <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie l’emplacement du magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="047b8-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="047b8-119">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="047b8-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="047b8-120">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="047b8-120">Optional.</span></span>|  
|<span data-ttu-id="047b8-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="047b8-121">x509FindType</span></span>|<span data-ttu-id="047b8-122">Un <xref:System.Security.Cryptography.X509Certificates.X509FindType> valeur qui spécifie le type de recherche doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="047b8-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="047b8-123">La valeur par défaut est « FindBySubjectDistinguishedName ».</span><span class="sxs-lookup"><span data-stu-id="047b8-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="047b8-124">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="047b8-124">Optional.</span></span>|  
|<span data-ttu-id="047b8-125">findValue</span><span class="sxs-lookup"><span data-stu-id="047b8-125">findValue</span></span>|<span data-ttu-id="047b8-126">Valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="047b8-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="047b8-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="047b8-127">Optional.</span></span>|  
|<span data-ttu-id="047b8-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="047b8-128">isChainIncluded</span></span>|<span data-ttu-id="047b8-129">Spécifie si la validation doit être effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="047b8-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="047b8-130">La valeur par défaut est « true » ; la validation est effectuée à l’aide de la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="047b8-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="047b8-131">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="047b8-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="047b8-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="047b8-132">Child Elements</span></span>  
 <span data-ttu-id="047b8-133">None</span><span class="sxs-lookup"><span data-stu-id="047b8-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="047b8-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="047b8-134">Parent Elements</span></span>  
  
|<span data-ttu-id="047b8-135">Élément</span><span class="sxs-lookup"><span data-stu-id="047b8-135">Element</span></span>|<span data-ttu-id="047b8-136">Description</span><span class="sxs-lookup"><span data-stu-id="047b8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="047b8-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="047b8-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="047b8-138">Configure le certificat qui est utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="047b8-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="047b8-139">Notes</span><span class="sxs-lookup"><span data-stu-id="047b8-139">Remarks</span></span>  
 <span data-ttu-id="047b8-140">Le `<certificateReference>` élément spécifie les paramètres qui sont utilisés pour rechercher et valider le certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="047b8-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="047b8-141">Lorsqu’il est spécifié comme élément enfant de le `<serviceCertificate>` élément, elle spécifie les paramètres d’emplacement et la vérification du certificat X.509 qui est utilisée pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="047b8-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="047b8-142">Le `<certificateReference>` élément est représenté par la <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="047b8-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
