---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735939"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="d6914-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="d6914-101">\<useManagedPresentation></span></span>
<span data-ttu-id="d6914-102">Élément de liaison utilisé pour communiquer avec un service d’émission de jeton de sécurité CardSpace qui prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="d6914-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d6914-103">Cet élément n'a aucun attribut et est présent en tant que commutateur vide.</span><span class="sxs-lookup"><span data-stu-id="d6914-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="d6914-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d6914-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d6914-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d6914-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d6914-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="d6914-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="d6914-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="d6914-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="d6914-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="d6914-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="d6914-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="d6914-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6914-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6914-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6914-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d6914-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6914-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d6914-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6914-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d6914-113">Attributes</span></span>  
 <span data-ttu-id="d6914-114">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="d6914-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6914-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d6914-115">Child Elements</span></span>  
 <span data-ttu-id="d6914-116">aucune.</span><span class="sxs-lookup"><span data-stu-id="d6914-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6914-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d6914-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d6914-118">Élément</span><span class="sxs-lookup"><span data-stu-id="d6914-118">Element</span></span>|<span data-ttu-id="d6914-119">Description</span><span class="sxs-lookup"><span data-stu-id="d6914-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6914-120">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="d6914-120">\<binding></span></span>](bindings.md)|<span data-ttu-id="d6914-121">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d6914-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6914-122">Notes</span><span class="sxs-lookup"><span data-stu-id="d6914-122">Remarks</span></span>  
 <span data-ttu-id="d6914-123">Cet élément est utilisé par un fournisseur d'identité pour exprimer dans sa stratégie le fait qu'il prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="d6914-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d6914-124">Les fournisseurs d'identité qui publient une telle assertion de stratégie doivent être en mesure de publier des jetons selon ce profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="d6914-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6914-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6914-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d6914-126">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d6914-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6914-127">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="d6914-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d6914-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="d6914-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d6914-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d6914-129">\<customBinding></span></span>](custombinding.md)
