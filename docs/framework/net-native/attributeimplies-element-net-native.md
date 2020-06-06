---
title: <AttributeImplies>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181067"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="50684-102">\<AttributeImplies>, Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="50684-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="50684-103">Définit la stratégie pour les éléments de code auxquels l'attribut conteneur est appliqué.</span><span class="sxs-lookup"><span data-stu-id="50684-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50684-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50684-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50684-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50684-105">Attributes and Elements</span></span>  
 <span data-ttu-id="50684-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="50684-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50684-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="50684-107">Attributes</span></span>  
  
|<span data-ttu-id="50684-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="50684-108">Attribute</span></span>|<span data-ttu-id="50684-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="50684-109">Attribute type</span></span>|<span data-ttu-id="50684-110">Description</span><span class="sxs-lookup"><span data-stu-id="50684-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="50684-111">Réflexion</span><span class="sxs-lookup"><span data-stu-id="50684-111">Reflection</span></span>|<span data-ttu-id="50684-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-112">Optional attribute.</span></span> <span data-ttu-id="50684-113">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="50684-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="50684-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="50684-114">Reflection</span></span>|<span data-ttu-id="50684-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-115">Optional attribute.</span></span> <span data-ttu-id="50684-116">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="50684-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="50684-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="50684-117">Reflection</span></span>|<span data-ttu-id="50684-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-118">Optional attribute.</span></span> <span data-ttu-id="50684-119">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="50684-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="50684-120">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="50684-120">Serialization</span></span>|<span data-ttu-id="50684-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-121">Optional attribute.</span></span> <span data-ttu-id="50684-122">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="50684-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="50684-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="50684-123">Serialization</span></span>|<span data-ttu-id="50684-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-124">Optional attribute.</span></span> <span data-ttu-id="50684-125">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50684-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="50684-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="50684-126">Serialization</span></span>|<span data-ttu-id="50684-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-127">Optional attribute.</span></span> <span data-ttu-id="50684-128">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50684-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="50684-129">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="50684-129">Serialization</span></span>|<span data-ttu-id="50684-130">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-130">Optional attribute.</span></span> <span data-ttu-id="50684-131">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50684-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="50684-132">Interop</span><span class="sxs-lookup"><span data-stu-id="50684-132">Interop</span></span>|<span data-ttu-id="50684-133">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-133">Optional attribute.</span></span> <span data-ttu-id="50684-134">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="50684-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="50684-135">Interop</span><span class="sxs-lookup"><span data-stu-id="50684-135">Interop</span></span>|<span data-ttu-id="50684-136">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-136">Optional attribute.</span></span> <span data-ttu-id="50684-137">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="50684-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="50684-138">Interop</span><span class="sxs-lookup"><span data-stu-id="50684-138">Interop</span></span>|<span data-ttu-id="50684-139">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="50684-139">Optional attribute.</span></span> <span data-ttu-id="50684-140">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="50684-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="50684-141">Tous les attributs</span><span class="sxs-lookup"><span data-stu-id="50684-141">All attributes</span></span>  
  
|<span data-ttu-id="50684-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="50684-142">Value</span></span>|<span data-ttu-id="50684-143">Description</span><span class="sxs-lookup"><span data-stu-id="50684-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50684-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="50684-144">*policy_setting*</span></span>|<span data-ttu-id="50684-145">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="50684-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="50684-146">Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="50684-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="50684-147">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="50684-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50684-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50684-148">Child Elements</span></span>  
 <span data-ttu-id="50684-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50684-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50684-150">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50684-150">Parent Elements</span></span>  
  
|<span data-ttu-id="50684-151">Élément</span><span class="sxs-lookup"><span data-stu-id="50684-151">Element</span></span>|<span data-ttu-id="50684-152">Description</span><span class="sxs-lookup"><span data-stu-id="50684-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="50684-153">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="50684-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50684-154">Remarques</span><span class="sxs-lookup"><span data-stu-id="50684-154">Remarks</span></span>  
 <span data-ttu-id="50684-155">L'élément `<AttributeImplies>` est utilisé si son type conteneur est un attribut (autrement dit, une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="50684-155">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="50684-156">Si l'attribut est appliqué à un élément de programme particulier, la stratégie définie par l'élément `<AttributeImplies>` s'applique à cet élément de programme.</span><span class="sxs-lookup"><span data-stu-id="50684-156">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="50684-157">Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.</span><span class="sxs-lookup"><span data-stu-id="50684-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50684-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50684-158">See also</span></span>

- [<span data-ttu-id="50684-159">\<Type>Appartient</span><span class="sxs-lookup"><span data-stu-id="50684-159">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="50684-160">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="50684-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="50684-161">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="50684-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="50684-162">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="50684-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
