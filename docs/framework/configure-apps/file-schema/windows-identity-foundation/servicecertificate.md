---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942411"
---
# <a name="servicecertificate"></a><span data-ttu-id="2cddc-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2cddc-101">\<serviceCertificate></span></span>
<span data-ttu-id="2cddc-102">Configure le certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="2cddc-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="2cddc-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="2cddc-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="2cddc-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="2cddc-104">\<federationConfiguration></span></span>  
<span data-ttu-id="2cddc-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2cddc-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cddc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cddc-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cddc-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2cddc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2cddc-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2cddc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cddc-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2cddc-109">Attributes</span></span>  
 <span data-ttu-id="2cddc-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="2cddc-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2cddc-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2cddc-111">Child Elements</span></span>  
  
|<span data-ttu-id="2cddc-112">Élément</span><span class="sxs-lookup"><span data-stu-id="2cddc-112">Element</span></span>|<span data-ttu-id="2cddc-113">Description</span><span class="sxs-lookup"><span data-stu-id="2cddc-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cddc-114">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="2cddc-114">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="2cddc-115">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="2cddc-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2cddc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2cddc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2cddc-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2cddc-117">Element</span></span>|<span data-ttu-id="2cddc-118">Description</span><span class="sxs-lookup"><span data-stu-id="2cddc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cddc-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="2cddc-119">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="2cddc-120">Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="2cddc-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2cddc-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="2cddc-121">Example</span></span>  
 <span data-ttu-id="2cddc-122">Le code XML suivant montre l’utilisation de \<l’élément serviceCertificate >.</span><span class="sxs-lookup"><span data-stu-id="2cddc-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="2cddc-123">Le code XML est extrait de `CustomToken` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="2cddc-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
