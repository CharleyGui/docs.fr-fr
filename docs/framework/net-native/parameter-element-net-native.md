---
title: <Parameter>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: c6dfc347d44a794ee8496c45ca879f9daab12b22
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128200"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="8929b-102">\<Parameter>, Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="8929b-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="8929b-103">Applique la stratégie de réflexion au type de l’argument passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="8929b-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8929b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8929b-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8929b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8929b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8929b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8929b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8929b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8929b-107">Attributes</span></span>  
  
|<span data-ttu-id="8929b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="8929b-108">Attribute</span></span>|<span data-ttu-id="8929b-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="8929b-109">Attribute type</span></span>|<span data-ttu-id="8929b-110">Description</span><span class="sxs-lookup"><span data-stu-id="8929b-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8929b-111">Général</span><span class="sxs-lookup"><span data-stu-id="8929b-111">General</span></span>|<span data-ttu-id="8929b-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="8929b-112">Required attribute.</span></span> <span data-ttu-id="8929b-113">Le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="8929b-113">The parameter name.</span></span> <span data-ttu-id="8929b-114">Par exemple, pour la signature de méthode `String.CompareTo(Object value)`, la valeur de l'attribut `Name` est « value ».</span><span class="sxs-lookup"><span data-stu-id="8929b-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="8929b-115">Réflexion</span><span class="sxs-lookup"><span data-stu-id="8929b-115">Reflection</span></span>|<span data-ttu-id="8929b-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-116">Optional attribute.</span></span> <span data-ttu-id="8929b-117">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="8929b-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8929b-118">Réflexion</span><span class="sxs-lookup"><span data-stu-id="8929b-118">Reflection</span></span>|<span data-ttu-id="8929b-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-119">Optional attribute.</span></span> <span data-ttu-id="8929b-120">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="8929b-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8929b-121">Réflexion</span><span class="sxs-lookup"><span data-stu-id="8929b-121">Reflection</span></span>|<span data-ttu-id="8929b-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-122">Optional attribute.</span></span> <span data-ttu-id="8929b-123">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="8929b-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8929b-124">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="8929b-124">Serialization</span></span>|<span data-ttu-id="8929b-125">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-125">Optional attribute.</span></span> <span data-ttu-id="8929b-126">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="8929b-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8929b-127">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="8929b-127">Serialization</span></span>|<span data-ttu-id="8929b-128">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-128">Optional attribute.</span></span> <span data-ttu-id="8929b-129">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8929b-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8929b-130">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="8929b-130">Serialization</span></span>|<span data-ttu-id="8929b-131">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-131">Optional attribute.</span></span> <span data-ttu-id="8929b-132">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8929b-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8929b-133">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="8929b-133">Serialization</span></span>|<span data-ttu-id="8929b-134">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-134">Optional attribute.</span></span> <span data-ttu-id="8929b-135">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8929b-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8929b-136">Interop</span><span class="sxs-lookup"><span data-stu-id="8929b-136">Interop</span></span>|<span data-ttu-id="8929b-137">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-137">Optional attribute.</span></span> <span data-ttu-id="8929b-138">Contrôle la stratégie de marshaling des types référence vers WinRT et COM.</span><span class="sxs-lookup"><span data-stu-id="8929b-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8929b-139">Interop</span><span class="sxs-lookup"><span data-stu-id="8929b-139">Interop</span></span>|<span data-ttu-id="8929b-140">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-140">Optional attribute.</span></span> <span data-ttu-id="8929b-141">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="8929b-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8929b-142">Interop</span><span class="sxs-lookup"><span data-stu-id="8929b-142">Interop</span></span>|<span data-ttu-id="8929b-143">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="8929b-143">Optional attribute.</span></span> <span data-ttu-id="8929b-144">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="8929b-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8929b-145">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="8929b-145">Name attribute</span></span>  
  
|<span data-ttu-id="8929b-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="8929b-146">Value</span></span>|<span data-ttu-id="8929b-147">Description</span><span class="sxs-lookup"><span data-stu-id="8929b-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8929b-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="8929b-148">*parameter_name*</span></span>|<span data-ttu-id="8929b-149">Nom du paramètre de méthode auquel la stratégie est appliquée.</span><span class="sxs-lookup"><span data-stu-id="8929b-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="8929b-150">Par exemple, pour la signature de méthode `String.CompareTo(Object value)`, la valeur de l'attribut `Name` est « value ».</span><span class="sxs-lookup"><span data-stu-id="8929b-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8929b-151">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="8929b-151">All other attributes</span></span>  
  
|<span data-ttu-id="8929b-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="8929b-152">Value</span></span>|<span data-ttu-id="8929b-153">Description</span><span class="sxs-lookup"><span data-stu-id="8929b-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8929b-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8929b-154">*policy_setting*</span></span>|<span data-ttu-id="8929b-155">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="8929b-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="8929b-156">Les valeurs possibles sont `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="8929b-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8929b-157">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8929b-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8929b-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8929b-158">Child Elements</span></span>  
 <span data-ttu-id="8929b-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8929b-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8929b-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8929b-160">Parent Elements</span></span>  
  
|<span data-ttu-id="8929b-161">Élément</span><span class="sxs-lookup"><span data-stu-id="8929b-161">Element</span></span>|<span data-ttu-id="8929b-162">Description</span><span class="sxs-lookup"><span data-stu-id="8929b-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="8929b-163">Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.</span><span class="sxs-lookup"><span data-stu-id="8929b-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8929b-164">Remarques</span><span class="sxs-lookup"><span data-stu-id="8929b-164">Remarks</span></span>  
 <span data-ttu-id="8929b-165">L' `<Parameter>` élément est un enfant de l' [\<Method>](method-element-net-native.md) élément et est utilisé pour appliquer la stratégie à un paramètre de méthode particulier.</span><span class="sxs-lookup"><span data-stu-id="8929b-165">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="8929b-166">Le paramètre de méthode spécifique est défini par le nom plutôt que par le type.</span><span class="sxs-lookup"><span data-stu-id="8929b-166">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="8929b-167">Au moins un attribut qui représente un type de stratégie, tel que `Activate` ou `Dynamic`, doit être présent.</span><span class="sxs-lookup"><span data-stu-id="8929b-167">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8929b-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8929b-168">See also</span></span>

- [<span data-ttu-id="8929b-169">\<Method>Appartient</span><span class="sxs-lookup"><span data-stu-id="8929b-169">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="8929b-170">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8929b-170">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8929b-171">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="8929b-171">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="8929b-172">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="8929b-172">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
