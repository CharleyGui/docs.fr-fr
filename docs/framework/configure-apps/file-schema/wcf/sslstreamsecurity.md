---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 9b7092878c604142c29dcd8d27e3c458d203f9fa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399532"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="e9050-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="e9050-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="e9050-102">Représente un élément de liaison personnalisé qui prend en charge la sécurité de canal à l'aide d'un flux SSL.</span><span class="sxs-lookup"><span data-stu-id="e9050-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="e9050-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9050-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9050-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e9050-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e9050-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e9050-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e9050-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e9050-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e9050-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="e9050-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e9050-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Section sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="e9050-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9050-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9050-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9050-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e9050-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e9050-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e9050-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9050-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e9050-112">Attributes</span></span>  
  
|<span data-ttu-id="e9050-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e9050-113">Attribute</span></span>|<span data-ttu-id="e9050-114">Description</span><span class="sxs-lookup"><span data-stu-id="e9050-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9050-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e9050-115">requireClientCertificate</span></span>|<span data-ttu-id="e9050-116">Valeur booléenne qui spécifie si un certificat client est requis pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="e9050-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="e9050-117">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="e9050-117">The default is `false`.</span></span>|  
|<span data-ttu-id="e9050-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="e9050-118">sslProtocols</span></span>|<span data-ttu-id="e9050-119">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e9050-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e9050-120">La valeur par défaut&#124;est&#124;Ssl3&#124;TLS Tls11 Tls12.</span><span class="sxs-lookup"><span data-stu-id="e9050-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9050-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e9050-121">Child Elements</span></span>  
 <span data-ttu-id="e9050-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e9050-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9050-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e9050-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9050-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e9050-124">Element</span></span>|<span data-ttu-id="e9050-125">Description</span><span class="sxs-lookup"><span data-stu-id="e9050-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9050-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="e9050-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e9050-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e9050-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9050-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9050-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="e9050-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e9050-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9050-130">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="e9050-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e9050-131">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e9050-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e9050-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e9050-132">\<customBinding></span></span>](custombinding.md)
