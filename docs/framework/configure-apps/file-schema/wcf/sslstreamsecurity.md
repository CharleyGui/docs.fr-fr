---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738592"
---
# \<sslStreamSecurity>
<span data-ttu-id="8875c-101">Représente un élément de liaison personnalisé qui prend en charge la sécurité de canal à l'aide d'un flux SSL.</span><span class="sxs-lookup"><span data-stu-id="8875c-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="8875c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8875c-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8875c-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8875c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8875c-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8875c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8875c-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="8875c-105">Attributes</span></span>  
  
|<span data-ttu-id="8875c-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="8875c-106">Attribute</span></span>|<span data-ttu-id="8875c-107">Description</span><span class="sxs-lookup"><span data-stu-id="8875c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8875c-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="8875c-108">requireClientCertificate</span></span>|<span data-ttu-id="8875c-109">Valeur booléenne qui spécifie si un certificat client est requis pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="8875c-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="8875c-110">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="8875c-110">The default is `false`.</span></span>|  
|<span data-ttu-id="8875c-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="8875c-111">sslProtocols</span></span>|<span data-ttu-id="8875c-112">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8875c-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="8875c-113">La valeur par défaut est Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="8875c-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8875c-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8875c-114">Child Elements</span></span>  
 <span data-ttu-id="8875c-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8875c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8875c-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8875c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8875c-117">Élément</span><span class="sxs-lookup"><span data-stu-id="8875c-117">Element</span></span>|<span data-ttu-id="8875c-118">Description</span><span class="sxs-lookup"><span data-stu-id="8875c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8875c-119">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8875c-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8875c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8875c-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="8875c-121">Liaisons</span><span class="sxs-lookup"><span data-stu-id="8875c-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8875c-122">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="8875c-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8875c-123">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="8875c-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
