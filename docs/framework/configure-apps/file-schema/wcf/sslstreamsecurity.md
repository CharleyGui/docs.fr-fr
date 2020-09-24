---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: aa6bc7f5a94afc8a190d3d9d2d71ea8b38d8c25b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153571"
---
# \<sslStreamSecurity>

<span data-ttu-id="5eda2-101">Représente un élément de liaison personnalisé qui prend en charge la sécurité de canal à l'aide d'un flux SSL.</span><span class="sxs-lookup"><span data-stu-id="5eda2-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="5eda2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eda2-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5eda2-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5eda2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5eda2-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5eda2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5eda2-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="5eda2-105">Attributes</span></span>  
  
|<span data-ttu-id="5eda2-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="5eda2-106">Attribute</span></span>|<span data-ttu-id="5eda2-107">Description</span><span class="sxs-lookup"><span data-stu-id="5eda2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5eda2-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5eda2-108">requireClientCertificate</span></span>|<span data-ttu-id="5eda2-109">Valeur booléenne qui spécifie si un certificat client est requis pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="5eda2-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="5eda2-110">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="5eda2-110">The default is `false`.</span></span>|  
|<span data-ttu-id="5eda2-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5eda2-111">sslProtocols</span></span>|<span data-ttu-id="5eda2-112">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5eda2-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5eda2-113">La valeur par défaut est Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="5eda2-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5eda2-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5eda2-114">Child Elements</span></span>  

 <span data-ttu-id="5eda2-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5eda2-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5eda2-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5eda2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5eda2-117">Élément</span><span class="sxs-lookup"><span data-stu-id="5eda2-117">Element</span></span>|<span data-ttu-id="5eda2-118">Description</span><span class="sxs-lookup"><span data-stu-id="5eda2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5eda2-119">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="5eda2-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eda2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5eda2-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="5eda2-121">Liaisons</span><span class="sxs-lookup"><span data-stu-id="5eda2-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5eda2-122">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="5eda2-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5eda2-123">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="5eda2-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
