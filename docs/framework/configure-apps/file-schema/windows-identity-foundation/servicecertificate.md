---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251854"
---
# <a name="servicecertificate"></a><span data-ttu-id="05094-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="05094-101">\<serviceCertificate></span></span>
<span data-ttu-id="05094-102">Configure le certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="05094-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
<span data-ttu-id="05094-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="05094-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="05094-104">&nbsp;&nbsp;[ **\<System. identityModel. services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="05094-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="05094-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="05094-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="05094-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="05094-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05094-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05094-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05094-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="05094-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05094-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="05094-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05094-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="05094-110">Attributes</span></span>  
 <span data-ttu-id="05094-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="05094-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05094-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="05094-112">Child Elements</span></span>  
  
|<span data-ttu-id="05094-113">Élément</span><span class="sxs-lookup"><span data-stu-id="05094-113">Element</span></span>|<span data-ttu-id="05094-114">Description</span><span class="sxs-lookup"><span data-stu-id="05094-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05094-115">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="05094-115">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="05094-116">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="05094-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05094-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="05094-117">Parent Elements</span></span>  
  
|<span data-ttu-id="05094-118">Élément</span><span class="sxs-lookup"><span data-stu-id="05094-118">Element</span></span>|<span data-ttu-id="05094-119">Description</span><span class="sxs-lookup"><span data-stu-id="05094-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05094-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="05094-120">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="05094-121">Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="05094-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05094-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="05094-122">Example</span></span>  
 <span data-ttu-id="05094-123">Le code XML suivant montre l’utilisation de \<l’élément serviceCertificate >.</span><span class="sxs-lookup"><span data-stu-id="05094-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="05094-124">Le code XML est extrait de `CustomToken` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="05094-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
