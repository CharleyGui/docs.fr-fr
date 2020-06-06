---
title: <Subtypes>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180933"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="4e358-102">\<Subtypes>, Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="4e358-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="4e358-103">Applique la stratégie runtime à toutes les classes héritées du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="4e358-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e358-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e358-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e358-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e358-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4e358-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e358-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e358-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e358-107">Attributes</span></span>  
  
|<span data-ttu-id="4e358-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e358-108">Attribute</span></span>|<span data-ttu-id="4e358-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="4e358-109">Attribute type</span></span>|<span data-ttu-id="4e358-110">Description</span><span class="sxs-lookup"><span data-stu-id="4e358-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="4e358-111">Réflexion</span><span class="sxs-lookup"><span data-stu-id="4e358-111">Reflection</span></span>|<span data-ttu-id="4e358-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-112">Optional attribute.</span></span> <span data-ttu-id="4e358-113">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="4e358-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="4e358-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="4e358-114">Reflection</span></span>|<span data-ttu-id="4e358-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-115">Optional attribute.</span></span> <span data-ttu-id="4e358-116">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="4e358-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="4e358-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="4e358-117">Reflection</span></span>|<span data-ttu-id="4e358-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-118">Optional attribute.</span></span> <span data-ttu-id="4e358-119">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="4e358-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="4e358-120">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="4e358-120">Serialization</span></span>|<span data-ttu-id="4e358-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-121">Optional attribute.</span></span> <span data-ttu-id="4e358-122">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="4e358-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="4e358-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="4e358-123">Serialization</span></span>|<span data-ttu-id="4e358-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-124">Optional attribute.</span></span> <span data-ttu-id="4e358-125">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e358-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="4e358-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="4e358-126">Serialization</span></span>|<span data-ttu-id="4e358-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-127">Optional attribute.</span></span> <span data-ttu-id="4e358-128">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e358-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="4e358-129">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="4e358-129">Serialization</span></span>|<span data-ttu-id="4e358-130">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-130">Optional attribute.</span></span> <span data-ttu-id="4e358-131">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e358-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="4e358-132">Interop</span><span class="sxs-lookup"><span data-stu-id="4e358-132">Interop</span></span>|<span data-ttu-id="4e358-133">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-133">Optional attribute.</span></span> <span data-ttu-id="4e358-134">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="4e358-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="4e358-135">Interop</span><span class="sxs-lookup"><span data-stu-id="4e358-135">Interop</span></span>|<span data-ttu-id="4e358-136">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-136">Optional attribute.</span></span> <span data-ttu-id="4e358-137">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="4e358-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="4e358-138">Interop</span><span class="sxs-lookup"><span data-stu-id="4e358-138">Interop</span></span>|<span data-ttu-id="4e358-139">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e358-139">Optional attribute.</span></span> <span data-ttu-id="4e358-140">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="4e358-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="4e358-141">Tous les attributs</span><span class="sxs-lookup"><span data-stu-id="4e358-141">All attributes</span></span>  
  
|<span data-ttu-id="4e358-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="4e358-142">Value</span></span>|<span data-ttu-id="4e358-143">Description</span><span class="sxs-lookup"><span data-stu-id="4e358-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e358-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="4e358-144">*policy_setting*</span></span>|<span data-ttu-id="4e358-145">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="4e358-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="4e358-146">Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="4e358-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="4e358-147">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4e358-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e358-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e358-148">Child Elements</span></span>  
 <span data-ttu-id="4e358-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e358-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e358-150">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e358-150">Parent Elements</span></span>  
  
|<span data-ttu-id="4e358-151">Élément</span><span class="sxs-lookup"><span data-stu-id="4e358-151">Element</span></span>|<span data-ttu-id="4e358-152">Description</span><span class="sxs-lookup"><span data-stu-id="4e358-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="4e358-153">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="4e358-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e358-154">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e358-154">Remarks</span></span>  
 <span data-ttu-id="4e358-155">L'élément `<Subtypes>` applique la stratégie à tous les sous-types de son type conteneur.</span><span class="sxs-lookup"><span data-stu-id="4e358-155">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="4e358-156">Utilisez-le pour appliquer des stratégies distinctes aux types dérivés et à leurs classes de base.</span><span class="sxs-lookup"><span data-stu-id="4e358-156">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="4e358-157">Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.</span><span class="sxs-lookup"><span data-stu-id="4e358-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e358-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e358-158">Example</span></span>  
 <span data-ttu-id="4e358-159">L'exemple suivant définit une classe nommée `BaseClass` et une sous-classe nommée `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="4e358-159">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="4e358-160">Comme le montre le code suivant, le fichier de directives runtime définit explicitement les stratégies `Dynamic` et `Activate` pour `BaseClass` sur `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="4e358-160">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="4e358-161">Ainsi, les objets de type `BaseClass` ne peuvent pas être instanciés dynamiquement ou par des appels du constructeur de classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="4e358-161">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="4e358-162">Toutefois, l'élément `<Subtypes>` permet aux classes dérivées de `BaseClass` d'être instanciées dynamiquement et via des appels de leurs constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="4e358-162">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="4e358-163">Grâce à la directive `<Subtypes>`, le code suivant qui instancie une instance `Derived1` dynamiquement en appelant la méthode <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> s'exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="4e358-163">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="4e358-164">En l'occurrence, la variable de bloc est un objet <xref:System.Windows.Controls.TextBlock> dans une application du Windows Store vide.</span><span class="sxs-lookup"><span data-stu-id="4e358-164">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4e358-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e358-165">See also</span></span>

- [<span data-ttu-id="4e358-166">\<Type>Appartient</span><span class="sxs-lookup"><span data-stu-id="4e358-166">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="4e358-167">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="4e358-167">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="4e358-168">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="4e358-168">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="4e358-169">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="4e358-169">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
