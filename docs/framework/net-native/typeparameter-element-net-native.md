---
title: <TypeParameter>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0de00b9313b60b3a527dd0380ae90d82731a8c02
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049060"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="1023c-102">\<TypeParameter >, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="1023c-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="1023c-103">Applique la stratégie au type représenté par un argument Type passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="1023c-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1023c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1023c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1023c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1023c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1023c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1023c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1023c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="1023c-107">Attributes</span></span>  
  
|<span data-ttu-id="1023c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="1023c-108">Attribute</span></span>|<span data-ttu-id="1023c-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="1023c-109">Attribute type</span></span>|<span data-ttu-id="1023c-110">Description</span><span class="sxs-lookup"><span data-stu-id="1023c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1023c-111">Généralités</span><span class="sxs-lookup"><span data-stu-id="1023c-111">General</span></span>|<span data-ttu-id="1023c-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="1023c-112">Required attribute.</span></span> <span data-ttu-id="1023c-113">Nom du paramètre de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1023c-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="1023c-114">Par exemple, pour la signature de méthode `Type.GetInterfaceMap(Type interfaceType)`, la valeur de l'attribut `Name` est « interfaceType ».</span><span class="sxs-lookup"><span data-stu-id="1023c-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="1023c-115">Réflexion</span><span class="sxs-lookup"><span data-stu-id="1023c-115">Reflection</span></span>|<span data-ttu-id="1023c-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-116">Optional attribute.</span></span> <span data-ttu-id="1023c-117">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1023c-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="1023c-118">Réflexion</span><span class="sxs-lookup"><span data-stu-id="1023c-118">Reflection</span></span>|<span data-ttu-id="1023c-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-119">Optional attribute.</span></span> <span data-ttu-id="1023c-120">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1023c-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="1023c-121">Réflexion</span><span class="sxs-lookup"><span data-stu-id="1023c-121">Reflection</span></span>|<span data-ttu-id="1023c-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-122">Optional attribute.</span></span> <span data-ttu-id="1023c-123">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="1023c-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="1023c-124">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1023c-124">Serialization</span></span>|<span data-ttu-id="1023c-125">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-125">Optional attribute.</span></span> <span data-ttu-id="1023c-126">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="1023c-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="1023c-127">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1023c-127">Serialization</span></span>|<span data-ttu-id="1023c-128">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-128">Optional attribute.</span></span> <span data-ttu-id="1023c-129">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1023c-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="1023c-130">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1023c-130">Serialization</span></span>|<span data-ttu-id="1023c-131">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-131">Optional attribute.</span></span> <span data-ttu-id="1023c-132">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1023c-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="1023c-133">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1023c-133">Serialization</span></span>|<span data-ttu-id="1023c-134">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-134">Optional attribute.</span></span> <span data-ttu-id="1023c-135">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1023c-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="1023c-136">Interop</span><span class="sxs-lookup"><span data-stu-id="1023c-136">Interop</span></span>|<span data-ttu-id="1023c-137">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-137">Optional attribute.</span></span> <span data-ttu-id="1023c-138">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="1023c-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="1023c-139">Interop</span><span class="sxs-lookup"><span data-stu-id="1023c-139">Interop</span></span>|<span data-ttu-id="1023c-140">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-140">Optional attribute.</span></span> <span data-ttu-id="1023c-141">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="1023c-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="1023c-142">Interop</span><span class="sxs-lookup"><span data-stu-id="1023c-142">Interop</span></span>|<span data-ttu-id="1023c-143">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="1023c-143">Optional attribute.</span></span> <span data-ttu-id="1023c-144">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="1023c-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1023c-145">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="1023c-145">Name attribute</span></span>  
  
|<span data-ttu-id="1023c-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="1023c-146">Value</span></span>|<span data-ttu-id="1023c-147">Description</span><span class="sxs-lookup"><span data-stu-id="1023c-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1023c-148">*nom_paramètre*</span><span class="sxs-lookup"><span data-stu-id="1023c-148">*parameter_name*</span></span>|<span data-ttu-id="1023c-149">Nom du paramètre de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1023c-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="1023c-150">Par exemple, pour la signature de méthode `Type.GetInterfaceMap(Type interfaceType)`, la valeur de l'attribut `Name` est « interfaceType ».</span><span class="sxs-lookup"><span data-stu-id="1023c-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1023c-151">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="1023c-151">All other attributes</span></span>  
  
|<span data-ttu-id="1023c-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="1023c-152">Value</span></span>|<span data-ttu-id="1023c-153">Description</span><span class="sxs-lookup"><span data-stu-id="1023c-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1023c-154">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="1023c-154">*policy_setting*</span></span>|<span data-ttu-id="1023c-155">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="1023c-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="1023c-156">Les valeurs possibles sont `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="1023c-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="1023c-157">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="1023c-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1023c-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1023c-158">Child Elements</span></span>  
 <span data-ttu-id="1023c-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1023c-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1023c-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1023c-160">Parent Elements</span></span>  
  
|<span data-ttu-id="1023c-161">Élément</span><span class="sxs-lookup"><span data-stu-id="1023c-161">Element</span></span>|<span data-ttu-id="1023c-162">Description</span><span class="sxs-lookup"><span data-stu-id="1023c-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1023c-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="1023c-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="1023c-164">Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.</span><span class="sxs-lookup"><span data-stu-id="1023c-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1023c-165">Notes</span><span class="sxs-lookup"><span data-stu-id="1023c-165">Remarks</span></span>  
 <span data-ttu-id="1023c-166">L’élément `<TypeParameter>` est similaire à l’élément [\<Parameter>](parameter-element-net-native.md), à ceci près qu’il peut uniquement être appliqué à des paramètres de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1023c-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="1023c-167">Il applique la stratégie à tout type représenté au moment de l'exécution par l'argument de type spécifié par l'attribut `Name`.</span><span class="sxs-lookup"><span data-stu-id="1023c-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="1023c-168">Par exemple, le sérialiseur JSON NewtonSoft inclut une méthode `JsonConvert.DeserializeObject(String value, Type type)` statique.</span><span class="sxs-lookup"><span data-stu-id="1023c-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="1023c-169">Les directives de réflexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="1023c-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="1023c-170">spécifient que les métadonnées pour le type de runtime représenté par l’argument `type` doivent être accessibles pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1023c-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="1023c-171">Si ces directives runtime s'appliquent à un projet qui inclut le code source suivant :</span><span class="sxs-lookup"><span data-stu-id="1023c-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="1023c-172">les directives de réflexion rendent les métadonnées pour le type `StockQuote` disponibles pour le sérialiseur JSON NewtonSoft au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1023c-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1023c-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1023c-173">See also</span></span>

- [<span data-ttu-id="1023c-174">\<Method>, élément</span><span class="sxs-lookup"><span data-stu-id="1023c-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="1023c-175">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="1023c-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1023c-176">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="1023c-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="1023c-177">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="1023c-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
