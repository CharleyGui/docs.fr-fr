---
title: <Subtypes>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af1acc02b18c5b97ef66ccae9b70c1f5327bff4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049127"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="05ef2-102">\<Subtypes, élément > (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="05ef2-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="05ef2-103">Applique la stratégie runtime à toutes les classes héritées du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="05ef2-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ef2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ef2-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05ef2-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="05ef2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="05ef2-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="05ef2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05ef2-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="05ef2-107">Attributes</span></span>  
  
|<span data-ttu-id="05ef2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="05ef2-108">Attribute</span></span>|<span data-ttu-id="05ef2-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="05ef2-109">Attribute type</span></span>|<span data-ttu-id="05ef2-110">Description</span><span class="sxs-lookup"><span data-stu-id="05ef2-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="05ef2-111">Réflexion</span><span class="sxs-lookup"><span data-stu-id="05ef2-111">Reflection</span></span>|<span data-ttu-id="05ef2-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-112">Optional attribute.</span></span> <span data-ttu-id="05ef2-113">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="05ef2-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="05ef2-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="05ef2-114">Reflection</span></span>|<span data-ttu-id="05ef2-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-115">Optional attribute.</span></span> <span data-ttu-id="05ef2-116">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="05ef2-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="05ef2-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="05ef2-117">Reflection</span></span>|<span data-ttu-id="05ef2-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-118">Optional attribute.</span></span> <span data-ttu-id="05ef2-119">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="05ef2-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="05ef2-120">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="05ef2-120">Serialization</span></span>|<span data-ttu-id="05ef2-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-121">Optional attribute.</span></span> <span data-ttu-id="05ef2-122">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="05ef2-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="05ef2-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="05ef2-123">Serialization</span></span>|<span data-ttu-id="05ef2-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-124">Optional attribute.</span></span> <span data-ttu-id="05ef2-125">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05ef2-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="05ef2-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="05ef2-126">Serialization</span></span>|<span data-ttu-id="05ef2-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-127">Optional attribute.</span></span> <span data-ttu-id="05ef2-128">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05ef2-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="05ef2-129">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="05ef2-129">Serialization</span></span>|<span data-ttu-id="05ef2-130">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-130">Optional attribute.</span></span> <span data-ttu-id="05ef2-131">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05ef2-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="05ef2-132">Interop</span><span class="sxs-lookup"><span data-stu-id="05ef2-132">Interop</span></span>|<span data-ttu-id="05ef2-133">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-133">Optional attribute.</span></span> <span data-ttu-id="05ef2-134">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="05ef2-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="05ef2-135">Interop</span><span class="sxs-lookup"><span data-stu-id="05ef2-135">Interop</span></span>|<span data-ttu-id="05ef2-136">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-136">Optional attribute.</span></span> <span data-ttu-id="05ef2-137">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="05ef2-138">Interop</span><span class="sxs-lookup"><span data-stu-id="05ef2-138">Interop</span></span>|<span data-ttu-id="05ef2-139">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-139">Optional attribute.</span></span> <span data-ttu-id="05ef2-140">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="05ef2-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="05ef2-141">Tous les attributs</span><span class="sxs-lookup"><span data-stu-id="05ef2-141">All attributes</span></span>  
  
|<span data-ttu-id="05ef2-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="05ef2-142">Value</span></span>|<span data-ttu-id="05ef2-143">Description</span><span class="sxs-lookup"><span data-stu-id="05ef2-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05ef2-144">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="05ef2-144">*policy_setting*</span></span>|<span data-ttu-id="05ef2-145">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="05ef2-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="05ef2-146">Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="05ef2-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="05ef2-147">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="05ef2-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05ef2-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="05ef2-148">Child Elements</span></span>  
 <span data-ttu-id="05ef2-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="05ef2-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05ef2-150">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="05ef2-150">Parent Elements</span></span>  
  
|<span data-ttu-id="05ef2-151">Élément</span><span class="sxs-lookup"><span data-stu-id="05ef2-151">Element</span></span>|<span data-ttu-id="05ef2-152">Description</span><span class="sxs-lookup"><span data-stu-id="05ef2-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05ef2-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="05ef2-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="05ef2-154">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="05ef2-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ef2-155">Notes</span><span class="sxs-lookup"><span data-stu-id="05ef2-155">Remarks</span></span>  
 <span data-ttu-id="05ef2-156">L'élément `<Subtypes>` applique la stratégie à tous les sous-types de son type conteneur.</span><span class="sxs-lookup"><span data-stu-id="05ef2-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="05ef2-157">Utilisez-le pour appliquer des stratégies distinctes aux types dérivés et à leurs classes de base.</span><span class="sxs-lookup"><span data-stu-id="05ef2-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="05ef2-158">Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.</span><span class="sxs-lookup"><span data-stu-id="05ef2-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05ef2-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="05ef2-159">Example</span></span>  
 <span data-ttu-id="05ef2-160">L'exemple suivant définit une classe nommée `BaseClass` et une sous-classe nommée `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="05ef2-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="05ef2-161">Comme le montre le code suivant, le fichier de directives runtime définit explicitement les stratégies `Dynamic` et `Activate` pour `BaseClass` sur `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="05ef2-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="05ef2-162">Ainsi, les objets de type `BaseClass` ne peuvent pas être instanciés dynamiquement ou par des appels du constructeur de classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="05ef2-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="05ef2-163">Toutefois, l'élément `<Subtypes>` permet aux classes dérivées de `BaseClass` d'être instanciées dynamiquement et via des appels de leurs constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="05ef2-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="05ef2-164">Grâce à la directive `<Subtypes>`, le code suivant qui instancie une instance `Derived1` dynamiquement en appelant la méthode <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> s'exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="05ef2-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="05ef2-165">En l'occurrence, la variable de bloc est un objet <xref:System.Windows.Controls.TextBlock> dans une application du Windows Store vide.</span><span class="sxs-lookup"><span data-stu-id="05ef2-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="05ef2-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05ef2-166">See also</span></span>

- [<span data-ttu-id="05ef2-167">\<Type >, élément</span><span class="sxs-lookup"><span data-stu-id="05ef2-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="05ef2-168">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="05ef2-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="05ef2-169">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="05ef2-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="05ef2-170">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="05ef2-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
