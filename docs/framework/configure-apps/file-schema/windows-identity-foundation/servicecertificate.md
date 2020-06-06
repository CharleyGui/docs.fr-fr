---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251854"
---
# \<serviceCertificate>
<span data-ttu-id="44a75-101">Configure le certificat X. 509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="44a75-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="44a75-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44a75-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44a75-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="44a75-103">Attributes and Elements</span></span>  
 <span data-ttu-id="44a75-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="44a75-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44a75-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="44a75-105">Attributes</span></span>  
 <span data-ttu-id="44a75-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="44a75-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44a75-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="44a75-107">Child Elements</span></span>  
  
|<span data-ttu-id="44a75-108">Élément</span><span class="sxs-lookup"><span data-stu-id="44a75-108">Element</span></span>|<span data-ttu-id="44a75-109">Description</span><span class="sxs-lookup"><span data-stu-id="44a75-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="44a75-110">Spécifie les paramètres utilisés pour rechercher et valider un certificat X. 509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="44a75-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44a75-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="44a75-111">Parent Elements</span></span>  
  
|<span data-ttu-id="44a75-112">Élément</span><span class="sxs-lookup"><span data-stu-id="44a75-112">Element</span></span>|<span data-ttu-id="44a75-113">Description</span><span class="sxs-lookup"><span data-stu-id="44a75-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="44a75-114">Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="44a75-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44a75-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="44a75-115">Example</span></span>  
 <span data-ttu-id="44a75-116">Le code XML suivant montre l’utilisation de l' \<serviceCertificate> élément.</span><span class="sxs-lookup"><span data-stu-id="44a75-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="44a75-117">Le code XML est extrait de l' `CustomToken` exemple.</span><span class="sxs-lookup"><span data-stu-id="44a75-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
