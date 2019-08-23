---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940611"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="de870-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="de870-101">\<useManagedPresentation></span></span>
<span data-ttu-id="de870-102">Élément de liaison utilisé pour communiquer avec un service d’émission de jeton de sécurité CardSpace qui prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="de870-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="de870-103">Cet élément n'a aucun attribut et est présent en tant que commutateur vide.</span><span class="sxs-lookup"><span data-stu-id="de870-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="de870-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="de870-104">\<system.serviceModel></span></span>  
<span data-ttu-id="de870-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="de870-105">\<bindings></span></span>  
<span data-ttu-id="de870-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="de870-106">\<customBinding></span></span>  
<span data-ttu-id="de870-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="de870-107">\<binding></span></span>  
<span data-ttu-id="de870-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="de870-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de870-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de870-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de870-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de870-110">Attributes and Elements</span></span>  
 <span data-ttu-id="de870-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="de870-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de870-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="de870-112">Attributes</span></span>  
 <span data-ttu-id="de870-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="de870-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de870-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de870-114">Child Elements</span></span>  
 <span data-ttu-id="de870-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="de870-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de870-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de870-116">Parent Elements</span></span>  
  
|<span data-ttu-id="de870-117">Élément</span><span class="sxs-lookup"><span data-stu-id="de870-117">Element</span></span>|<span data-ttu-id="de870-118">Description</span><span class="sxs-lookup"><span data-stu-id="de870-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de870-119">\<binding></span><span class="sxs-lookup"><span data-stu-id="de870-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="de870-120">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="de870-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de870-121">Notes</span><span class="sxs-lookup"><span data-stu-id="de870-121">Remarks</span></span>  
 <span data-ttu-id="de870-122">Cet élément est utilisé par un fournisseur d'identité pour exprimer dans sa stratégie le fait qu'il prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="de870-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="de870-123">Les fournisseurs d'identité qui publient une telle assertion de stratégie doivent être en mesure de publier des jetons selon ce profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="de870-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de870-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de870-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="de870-125">Liaisons</span><span class="sxs-lookup"><span data-stu-id="de870-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="de870-126">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="de870-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="de870-127">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="de870-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="de870-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="de870-128">\<customBinding></span></span>](custombinding.md)
