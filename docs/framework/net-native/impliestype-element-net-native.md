---
title: <ImpliesType>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10fa3a0ac04038bb686311a4d86c99442c0fcf26
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049674"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="e737f-102">\<ImpliesType >, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e737f-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="e737f-103">Applique la stratégie à un type, si cette stratégie a été appliquée à la méthode ou au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="e737f-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e737f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e737f-104">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e737f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e737f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e737f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e737f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e737f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e737f-107">Attributes</span></span>  
  
|<span data-ttu-id="e737f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e737f-108">Attribute</span></span>|<span data-ttu-id="e737f-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="e737f-109">Attribute type</span></span>|<span data-ttu-id="e737f-110">Description</span><span class="sxs-lookup"><span data-stu-id="e737f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e737f-111">Généralités</span><span class="sxs-lookup"><span data-stu-id="e737f-111">General</span></span>|<span data-ttu-id="e737f-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e737f-112">Required attribute.</span></span> <span data-ttu-id="e737f-113">Spécifie le nom du type.</span><span class="sxs-lookup"><span data-stu-id="e737f-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="e737f-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="e737f-114">Reflection</span></span>|<span data-ttu-id="e737f-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-115">Optional attribute.</span></span> <span data-ttu-id="e737f-116">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e737f-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="e737f-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="e737f-117">Reflection</span></span>|<span data-ttu-id="e737f-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-118">Optional attribute.</span></span> <span data-ttu-id="e737f-119">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e737f-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="e737f-120">Réflexion</span><span class="sxs-lookup"><span data-stu-id="e737f-120">Reflection</span></span>|<span data-ttu-id="e737f-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-121">Optional attribute.</span></span> <span data-ttu-id="e737f-122">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="e737f-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="e737f-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e737f-123">Serialization</span></span>|<span data-ttu-id="e737f-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-124">Optional attribute.</span></span> <span data-ttu-id="e737f-125">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="e737f-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="e737f-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e737f-126">Serialization</span></span>|<span data-ttu-id="e737f-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-127">Optional attribute.</span></span> <span data-ttu-id="e737f-128">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e737f-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="e737f-129">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e737f-129">Serialization</span></span>|<span data-ttu-id="e737f-130">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-130">Optional attribute.</span></span> <span data-ttu-id="e737f-131">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e737f-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="e737f-132">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e737f-132">Serialization</span></span>|<span data-ttu-id="e737f-133">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-133">Optional attribute.</span></span> <span data-ttu-id="e737f-134">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e737f-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="e737f-135">Interop</span><span class="sxs-lookup"><span data-stu-id="e737f-135">Interop</span></span>|<span data-ttu-id="e737f-136">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-136">Optional attribute.</span></span> <span data-ttu-id="e737f-137">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="e737f-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="e737f-138">Interop</span><span class="sxs-lookup"><span data-stu-id="e737f-138">Interop</span></span>|<span data-ttu-id="e737f-139">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-139">Optional attribute.</span></span> <span data-ttu-id="e737f-140">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="e737f-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="e737f-141">Interop</span><span class="sxs-lookup"><span data-stu-id="e737f-141">Interop</span></span>|<span data-ttu-id="e737f-142">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e737f-142">Optional attribute.</span></span> <span data-ttu-id="e737f-143">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="e737f-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e737f-144">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="e737f-144">Name attribute</span></span>  
  
|<span data-ttu-id="e737f-145">Valeur</span><span class="sxs-lookup"><span data-stu-id="e737f-145">Value</span></span>|<span data-ttu-id="e737f-146">Description</span><span class="sxs-lookup"><span data-stu-id="e737f-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e737f-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="e737f-147">*type_name*</span></span>|<span data-ttu-id="e737f-148">Nom du type.</span><span class="sxs-lookup"><span data-stu-id="e737f-148">The type name.</span></span> <span data-ttu-id="e737f-149">Si le type représenté par cet élément `<ImpliesType>` se trouve dans le même espace de noms que son élément `<Type>` conteneur, *type_name* peut inclure le nom du type sans son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e737f-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="e737f-150">Dans le cas contraire, *type_name* doit inclure le nom de type complet.</span><span class="sxs-lookup"><span data-stu-id="e737f-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e737f-151">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="e737f-151">All other attributes</span></span>  
  
|<span data-ttu-id="e737f-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="e737f-152">Value</span></span>|<span data-ttu-id="e737f-153">Description</span><span class="sxs-lookup"><span data-stu-id="e737f-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e737f-154">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="e737f-154">*policy_setting*</span></span>|<span data-ttu-id="e737f-155">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="e737f-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="e737f-156">Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="e737f-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e737f-157">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e737f-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e737f-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e737f-158">Child Elements</span></span>  
 <span data-ttu-id="e737f-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e737f-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e737f-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e737f-160">Parent Elements</span></span>  
  
|<span data-ttu-id="e737f-161">Élément</span><span class="sxs-lookup"><span data-stu-id="e737f-161">Element</span></span>|<span data-ttu-id="e737f-162">Description</span><span class="sxs-lookup"><span data-stu-id="e737f-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e737f-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="e737f-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="e737f-164">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e737f-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="e737f-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="e737f-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e737f-166">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e737f-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="e737f-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="e737f-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="e737f-168">Applique la stratégie de réflexion à une méthode.</span><span class="sxs-lookup"><span data-stu-id="e737f-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e737f-169">Notes</span><span class="sxs-lookup"><span data-stu-id="e737f-169">Remarks</span></span>  
 <span data-ttu-id="e737f-170">L'élément `<ImpliesType>` est essentiellement conçu pour une utilisation par des bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="e737f-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="e737f-171">Il traite le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="e737f-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="e737f-172">Si une routine a besoin de réfléchir un type, elle doit nécessairement réfléchir un second type.</span><span class="sxs-lookup"><span data-stu-id="e737f-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="e737f-173">Sinon, les métadonnées de l'instanciation implicite du second type sont indisponibles, car l'analyse statique n'indique pas qu'elles sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e737f-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="e737f-174">En règle générale, les deux types sont des instanciations génériques partageant des arguments de type.</span><span class="sxs-lookup"><span data-stu-id="e737f-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="e737f-175">L'élément `<ImpliesType>` a été défini en partant du principe que la nécessité de réfléchir le type spécifié par son élément parent implique la nécessité de réfléchir le type spécifié par l'élément `<ImpliesType>`.</span><span class="sxs-lookup"><span data-stu-id="e737f-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="e737f-176">Par exemple, les directives de réflexion suivantes s'appliquent aux deux types `Explicit<T>` et `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="e737f-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="e737f-177">Cette directive n'a d'effet que si une instanciation d'`Explicit` possède un paramètre de stratégie `Dynamic` défini.</span><span class="sxs-lookup"><span data-stu-id="e737f-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="e737f-178">Par exemple, si c'est le cas pour `Explicit<Int32>`, `Implicit<Int32>` est instancié avec ses membres publics associés à une racine, et leurs métadonnées sont accessibles pour une programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="e737f-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="e737f-179">Voici un exemple concret qui s'applique à au moins un sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="e737f-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="e737f-180">Les directives capturent le fait que la réflexion d’un élément de type `IList<`*quelque chose*`>` implique nécessairement la réflexion du type `List<`*quelque chose*`>` correspondant sans nécessiter d’annotation par application.</span><span class="sxs-lookup"><span data-stu-id="e737f-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="e737f-181">L'élément `<ImpliesType>` peut également apparaître dans un élément `<Method>`, car dans certains cas l'instanciation d'une méthode générique implique la réflexion d'une instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="e737f-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="e737f-182">Par exemple, Imaginez une méthode `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` générique à laquelle une bibliothèque donnée accède dynamiquement avec les types et <xref:System.Collections.Generic.List%601> <xref:System.Array> associés.</span><span class="sxs-lookup"><span data-stu-id="e737f-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="e737f-183">Cela peut être exprimé sous la forme :</span><span class="sxs-lookup"><span data-stu-id="e737f-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e737f-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e737f-184">See also</span></span>

- [<span data-ttu-id="e737f-185">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e737f-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e737f-186">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="e737f-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e737f-187">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="e737f-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
