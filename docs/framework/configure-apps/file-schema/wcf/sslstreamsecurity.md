---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 5ed87adfb3963513602844fc69afce8f7994fa8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932424"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="c439a-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="c439a-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="c439a-102">Représente un élément de liaison personnalisé qui prend en charge la sécurité de canal à l'aide d'un flux SSL.</span><span class="sxs-lookup"><span data-stu-id="c439a-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="c439a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c439a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c439a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c439a-104">\<bindings></span></span>  
<span data-ttu-id="c439a-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c439a-105">\<customBinding></span></span>  
<span data-ttu-id="c439a-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="c439a-106">\<binding></span></span>  
<span data-ttu-id="c439a-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="c439a-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c439a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c439a-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c439a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c439a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c439a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c439a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c439a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c439a-111">Attributes</span></span>  
  
|<span data-ttu-id="c439a-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="c439a-112">Attribute</span></span>|<span data-ttu-id="c439a-113">Description</span><span class="sxs-lookup"><span data-stu-id="c439a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c439a-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="c439a-114">requireClientCertificate</span></span>|<span data-ttu-id="c439a-115">Valeur booléenne qui spécifie si un certificat client est requis pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="c439a-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="c439a-116">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="c439a-116">The default is `false`.</span></span>|  
|<span data-ttu-id="c439a-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="c439a-117">sslProtocols</span></span>|<span data-ttu-id="c439a-118">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c439a-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="c439a-119">La valeur par défaut&#124;est&#124;Ssl3&#124;TLS Tls11 Tls12.</span><span class="sxs-lookup"><span data-stu-id="c439a-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c439a-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c439a-120">Child Elements</span></span>  
 <span data-ttu-id="c439a-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c439a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c439a-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c439a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c439a-123">Élément</span><span class="sxs-lookup"><span data-stu-id="c439a-123">Element</span></span>|<span data-ttu-id="c439a-124">Description</span><span class="sxs-lookup"><span data-stu-id="c439a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c439a-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="c439a-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="c439a-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c439a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c439a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c439a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="c439a-128">Liaisons</span><span class="sxs-lookup"><span data-stu-id="c439a-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c439a-129">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="c439a-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c439a-130">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c439a-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c439a-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c439a-131">\<customBinding></span></span>](custombinding.md)
