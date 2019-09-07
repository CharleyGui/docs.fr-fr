---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399212"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="db825-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="db825-101">\<useManagedPresentation></span></span>
<span data-ttu-id="db825-102">Élément de liaison utilisé pour communiquer avec un service d’émission de jeton de sécurité CardSpace qui prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="db825-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="db825-103">Cet élément n'a aucun attribut et est présent en tant que commutateur vide.</span><span class="sxs-lookup"><span data-stu-id="db825-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="db825-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db825-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db825-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="db825-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="db825-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="db825-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="db825-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="db825-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="db825-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="db825-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="db825-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="db825-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db825-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db825-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db825-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db825-111">Attributes and Elements</span></span>  
 <span data-ttu-id="db825-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db825-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db825-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="db825-113">Attributes</span></span>  
 <span data-ttu-id="db825-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db825-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="db825-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db825-115">Child Elements</span></span>  
 <span data-ttu-id="db825-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="db825-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db825-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db825-117">Parent Elements</span></span>  
  
|<span data-ttu-id="db825-118">Élément</span><span class="sxs-lookup"><span data-stu-id="db825-118">Element</span></span>|<span data-ttu-id="db825-119">Description</span><span class="sxs-lookup"><span data-stu-id="db825-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db825-120">\<binding></span><span class="sxs-lookup"><span data-stu-id="db825-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="db825-121">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="db825-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db825-122">Notes</span><span class="sxs-lookup"><span data-stu-id="db825-122">Remarks</span></span>  
 <span data-ttu-id="db825-123">Cet élément est utilisé par un fournisseur d'identité pour exprimer dans sa stratégie le fait qu'il prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="db825-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="db825-124">Les fournisseurs d'identité qui publient une telle assertion de stratégie doivent être en mesure de publier des jetons selon ce profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="db825-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db825-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db825-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="db825-126">Liaisons</span><span class="sxs-lookup"><span data-stu-id="db825-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="db825-127">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="db825-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="db825-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="db825-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="db825-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="db825-129">\<customBinding></span></span>](custombinding.md)
