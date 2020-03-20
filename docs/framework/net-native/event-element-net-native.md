---
title: <Event>Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181036"
---
# <a name="event-element-net-native"></a><span data-ttu-id="067ee-102">\<Événement> Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="067ee-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="067ee-103">Applique la stratégie de réflexion runtime à un événement.</span><span class="sxs-lookup"><span data-stu-id="067ee-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="067ee-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="067ee-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="067ee-105">Attributes and Elements</span></span>  
 <span data-ttu-id="067ee-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="067ee-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="067ee-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="067ee-107">Attributes</span></span>  
  
|<span data-ttu-id="067ee-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="067ee-108">Attribute</span></span>|<span data-ttu-id="067ee-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="067ee-109">Attribute type</span></span>|<span data-ttu-id="067ee-110">Description</span><span class="sxs-lookup"><span data-stu-id="067ee-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="067ee-111">Général</span><span class="sxs-lookup"><span data-stu-id="067ee-111">General</span></span>|<span data-ttu-id="067ee-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="067ee-112">Required attribute.</span></span> <span data-ttu-id="067ee-113">Spécifie le nom de l'événement.</span><span class="sxs-lookup"><span data-stu-id="067ee-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="067ee-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="067ee-114">Reflection</span></span>|<span data-ttu-id="067ee-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="067ee-115">Optional attribute.</span></span> <span data-ttu-id="067ee-116">Contrôle la demande d'informations sur l'événement ou l'énumération de celui-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="067ee-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="067ee-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="067ee-117">Reflection</span></span>|<span data-ttu-id="067ee-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="067ee-118">Optional attribute.</span></span> <span data-ttu-id="067ee-119">Contrôle l'accès à l'événement au moment de l'exécution pour autoriser la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="067ee-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="067ee-120">Cette stratégie garantit qu'un événement peut être géré dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="067ee-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="067ee-121">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="067ee-121">Name attribute</span></span>  
  
|<span data-ttu-id="067ee-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="067ee-122">Value</span></span>|<span data-ttu-id="067ee-123">Description</span><span class="sxs-lookup"><span data-stu-id="067ee-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="067ee-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="067ee-124">*method_name*</span></span>|<span data-ttu-id="067ee-125">Nom de l'événement.</span><span class="sxs-lookup"><span data-stu-id="067ee-125">The event name.</span></span> <span data-ttu-id="067ee-126">Le type de l’événement est défini par le [ \<parent Type>](type-element-net-native.md) ou [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) élément.</span><span class="sxs-lookup"><span data-stu-id="067ee-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="067ee-127">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="067ee-127">All other attributes</span></span>  
  
|<span data-ttu-id="067ee-128">Valeur</span><span class="sxs-lookup"><span data-stu-id="067ee-128">Value</span></span>|<span data-ttu-id="067ee-129">Description</span><span class="sxs-lookup"><span data-stu-id="067ee-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="067ee-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="067ee-130">*policy_setting*</span></span>|<span data-ttu-id="067ee-131">Paramètre à appliquer à ce type de stratégie pour l'événement.</span><span class="sxs-lookup"><span data-stu-id="067ee-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="067ee-132">Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`.</span><span class="sxs-lookup"><span data-stu-id="067ee-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="067ee-133">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="067ee-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="067ee-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="067ee-134">Child Elements</span></span>  
 <span data-ttu-id="067ee-135">Aucun.</span><span class="sxs-lookup"><span data-stu-id="067ee-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="067ee-136">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="067ee-136">Parent Elements</span></span>  
  
|<span data-ttu-id="067ee-137">Élément</span><span class="sxs-lookup"><span data-stu-id="067ee-137">Element</span></span>|<span data-ttu-id="067ee-138">Description</span><span class="sxs-lookup"><span data-stu-id="067ee-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="067ee-139">\<Type></span><span class="sxs-lookup"><span data-stu-id="067ee-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="067ee-140">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="067ee-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="067ee-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="067ee-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="067ee-142">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="067ee-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="067ee-143">Notes </span><span class="sxs-lookup"><span data-stu-id="067ee-143">Remarks</span></span>  
 <span data-ttu-id="067ee-144">Si la stratégie d'un événement n'est pas définie explicitement, elle hérite la stratégie runtime de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="067ee-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067ee-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="067ee-145">See also</span></span>

- [<span data-ttu-id="067ee-146">Informations de référence sur le fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="067ee-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="067ee-147">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="067ee-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="067ee-148">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="067ee-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
