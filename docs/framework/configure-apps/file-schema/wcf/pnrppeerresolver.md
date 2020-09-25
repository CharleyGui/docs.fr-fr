---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 0a8cc60226b13552d47faec3a156ed1f59acacb9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181399"
---
# \<pnrpPeerResolver>

<span data-ttu-id="fadd9-101">Spécifie que le programme de résolution PNRP (Peer Name Resolution Protocol) doit être utilisé comme un programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="fadd9-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="fadd9-102">Cet élément est facultatif parce que PNRP est le programme de résolution par défaut.</span><span class="sxs-lookup"><span data-stu-id="fadd9-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="fadd9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fadd9-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fadd9-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fadd9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fadd9-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fadd9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fadd9-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="fadd9-106">Attributes</span></span>  
  
|<span data-ttu-id="fadd9-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="fadd9-107">Attribute</span></span>|<span data-ttu-id="fadd9-108">Description</span><span class="sxs-lookup"><span data-stu-id="fadd9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fadd9-109">resolverType</span><span class="sxs-lookup"><span data-stu-id="fadd9-109">resolverType</span></span>|<span data-ttu-id="fadd9-110">Chaîne qui spécifie le programme de résolution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fadd9-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="fadd9-111">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="fadd9-111">This attribute is optional.</span></span> <span data-ttu-id="fadd9-112">S'il n'est pas défini ou s'il a pour valeur une chaîne vide, PNRP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fadd9-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fadd9-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fadd9-113">Child Elements</span></span>  

 <span data-ttu-id="fadd9-114">None</span><span class="sxs-lookup"><span data-stu-id="fadd9-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fadd9-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fadd9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fadd9-116">Élément</span><span class="sxs-lookup"><span data-stu-id="fadd9-116">Element</span></span>|<span data-ttu-id="fadd9-117">Description</span><span class="sxs-lookup"><span data-stu-id="fadd9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="fadd9-118">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fadd9-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fadd9-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="fadd9-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="fadd9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fadd9-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fadd9-121">Liaisons</span><span class="sxs-lookup"><span data-stu-id="fadd9-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fadd9-122">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="fadd9-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fadd9-123">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="fadd9-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="fadd9-124">Programmes de résolution d'homologue</span><span class="sxs-lookup"><span data-stu-id="fadd9-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
