---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: ce8be6eea5469b099a368a0b62e791faa7e3cbfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156990"
---
# \<serviceCertificate>

<span data-ttu-id="64b84-101">Configure le certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="64b84-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="64b84-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64b84-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64b84-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64b84-103">Attributes and Elements</span></span>  

 <span data-ttu-id="64b84-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="64b84-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64b84-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="64b84-105">Attributes</span></span>  

 <span data-ttu-id="64b84-106">None</span><span class="sxs-lookup"><span data-stu-id="64b84-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64b84-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64b84-107">Child Elements</span></span>  
  
|<span data-ttu-id="64b84-108">Élément</span><span class="sxs-lookup"><span data-stu-id="64b84-108">Element</span></span>|<span data-ttu-id="64b84-109">Description</span><span class="sxs-lookup"><span data-stu-id="64b84-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="64b84-110">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="64b84-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64b84-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64b84-111">Parent Elements</span></span>  
  
|<span data-ttu-id="64b84-112">Élément</span><span class="sxs-lookup"><span data-stu-id="64b84-112">Element</span></span>|<span data-ttu-id="64b84-113">Description</span><span class="sxs-lookup"><span data-stu-id="64b84-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="64b84-114">Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="64b84-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64b84-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="64b84-115">Example</span></span>  

 <span data-ttu-id="64b84-116">Le code XML suivant montre l’utilisation de l' \<serviceCertificate> élément.</span><span class="sxs-lookup"><span data-stu-id="64b84-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="64b84-117">Le code XML est extrait de l' `CustomToken` exemple.</span><span class="sxs-lookup"><span data-stu-id="64b84-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
