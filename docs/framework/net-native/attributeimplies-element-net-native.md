---
title: <AttributeImplies>Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181067"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="7311c-102">\<AttributImplies> Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7311c-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="7311c-103">Définit la stratégie pour les éléments de code auxquels l'attribut conteneur est appliqué.</span><span class="sxs-lookup"><span data-stu-id="7311c-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7311c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7311c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7311c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7311c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7311c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7311c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7311c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7311c-107">Attributes</span></span>  
  
|<span data-ttu-id="7311c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7311c-108">Attribute</span></span>|<span data-ttu-id="7311c-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="7311c-109">Attribute type</span></span>|<span data-ttu-id="7311c-110">Description</span><span class="sxs-lookup"><span data-stu-id="7311c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="7311c-111">Réflexion</span><span class="sxs-lookup"><span data-stu-id="7311c-111">Reflection</span></span>|<span data-ttu-id="7311c-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-112">Optional attribute.</span></span> <span data-ttu-id="7311c-113">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7311c-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="7311c-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="7311c-114">Reflection</span></span>|<span data-ttu-id="7311c-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-115">Optional attribute.</span></span> <span data-ttu-id="7311c-116">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7311c-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="7311c-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="7311c-117">Reflection</span></span>|<span data-ttu-id="7311c-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-118">Optional attribute.</span></span> <span data-ttu-id="7311c-119">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="7311c-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="7311c-120">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="7311c-120">Serialization</span></span>|<span data-ttu-id="7311c-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-121">Optional attribute.</span></span> <span data-ttu-id="7311c-122">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="7311c-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="7311c-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="7311c-123">Serialization</span></span>|<span data-ttu-id="7311c-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-124">Optional attribute.</span></span> <span data-ttu-id="7311c-125">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7311c-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="7311c-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="7311c-126">Serialization</span></span>|<span data-ttu-id="7311c-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-127">Optional attribute.</span></span> <span data-ttu-id="7311c-128">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7311c-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="7311c-129">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="7311c-129">Serialization</span></span>|<span data-ttu-id="7311c-130">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-130">Optional attribute.</span></span> <span data-ttu-id="7311c-131">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7311c-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="7311c-132">Interop</span><span class="sxs-lookup"><span data-stu-id="7311c-132">Interop</span></span>|<span data-ttu-id="7311c-133">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-133">Optional attribute.</span></span> <span data-ttu-id="7311c-134">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="7311c-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="7311c-135">Interop</span><span class="sxs-lookup"><span data-stu-id="7311c-135">Interop</span></span>|<span data-ttu-id="7311c-136">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-136">Optional attribute.</span></span> <span data-ttu-id="7311c-137">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="7311c-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="7311c-138">Interop</span><span class="sxs-lookup"><span data-stu-id="7311c-138">Interop</span></span>|<span data-ttu-id="7311c-139">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7311c-139">Optional attribute.</span></span> <span data-ttu-id="7311c-140">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="7311c-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="7311c-141">Tous les attributs</span><span class="sxs-lookup"><span data-stu-id="7311c-141">All attributes</span></span>  
  
|<span data-ttu-id="7311c-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="7311c-142">Value</span></span>|<span data-ttu-id="7311c-143">Description</span><span class="sxs-lookup"><span data-stu-id="7311c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7311c-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7311c-144">*policy_setting*</span></span>|<span data-ttu-id="7311c-145">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="7311c-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="7311c-146">Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="7311c-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7311c-147">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7311c-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7311c-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7311c-148">Child Elements</span></span>  
 <span data-ttu-id="7311c-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7311c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7311c-150">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7311c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="7311c-151">Élément</span><span class="sxs-lookup"><span data-stu-id="7311c-151">Element</span></span>|<span data-ttu-id="7311c-152">Description</span><span class="sxs-lookup"><span data-stu-id="7311c-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7311c-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="7311c-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="7311c-154">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="7311c-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7311c-155">Notes </span><span class="sxs-lookup"><span data-stu-id="7311c-155">Remarks</span></span>  
 <span data-ttu-id="7311c-156">L'élément `<AttributeImplies>` est utilisé si son type conteneur est un attribut (autrement dit, une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="7311c-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="7311c-157">Si l'attribut est appliqué à un élément de programme particulier, la stratégie définie par l'élément `<AttributeImplies>` s'applique à cet élément de programme.</span><span class="sxs-lookup"><span data-stu-id="7311c-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="7311c-158">Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.</span><span class="sxs-lookup"><span data-stu-id="7311c-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7311c-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7311c-159">See also</span></span>

- [<span data-ttu-id="7311c-160">\<Type> Élément</span><span class="sxs-lookup"><span data-stu-id="7311c-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="7311c-161">Informations de référence sur le fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7311c-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7311c-162">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="7311c-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="7311c-163">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="7311c-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
