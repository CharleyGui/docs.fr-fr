---
title: <Method>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180987"
---
# <a name="method-element-net-native"></a><span data-ttu-id="a4e4d-102">\<Method>, Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a4e4d-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="a4e4d-103">Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4e4d-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4e4d-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a4e4d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a4e4d-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4e4d-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a4e4d-107">Attributes</span></span>  
  
|<span data-ttu-id="a4e4d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a4e4d-108">Attribute</span></span>|<span data-ttu-id="a4e4d-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="a4e4d-109">Attribute type</span></span>|<span data-ttu-id="a4e4d-110">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a4e4d-111">Général</span><span class="sxs-lookup"><span data-stu-id="a4e4d-111">General</span></span>|<span data-ttu-id="a4e4d-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-112">Required attribute.</span></span> <span data-ttu-id="a4e4d-113">Spécifie le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="a4e4d-114">Général</span><span class="sxs-lookup"><span data-stu-id="a4e4d-114">General</span></span>|<span data-ttu-id="a4e4d-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-115">Optional attribute.</span></span> <span data-ttu-id="a4e4d-116">Spécifie la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-116">Specifies the method signature.</span></span> <span data-ttu-id="a4e4d-117">Si plusieurs paramètres sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="a4e4d-118">Par exemple, l'élément `<Method>` suivant définit la stratégie pour la méthode <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="a4e4d-119">Si l'attribut est absent, la directive runtime s'applique à toutes les surcharges de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="a4e4d-120">Réflexion</span><span class="sxs-lookup"><span data-stu-id="a4e4d-120">Reflection</span></span>|<span data-ttu-id="a4e4d-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-121">Optional attribute.</span></span> <span data-ttu-id="a4e4d-122">Contrôle la demande d'informations sur une méthode ou l'énumération de celle-ci, mais ne permet pas d'effectuer un appel dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="a4e4d-123">Réflexion</span><span class="sxs-lookup"><span data-stu-id="a4e4d-123">Reflection</span></span>|<span data-ttu-id="a4e4d-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-124">Optional attribute.</span></span> <span data-ttu-id="a4e4d-125">Contrôle l'accès à un constructeur ou à une méthode au moment de l'exécution pour activer la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="a4e4d-126">Cette stratégie garantit que le membre peut être appelé dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a4e4d-127">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="a4e4d-127">Name attribute</span></span>  
  
|<span data-ttu-id="a4e4d-128">Valeur</span><span class="sxs-lookup"><span data-stu-id="a4e4d-128">Value</span></span>|<span data-ttu-id="a4e4d-129">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4d-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4e4d-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="a4e4d-130">*method_name*</span></span>|<span data-ttu-id="a4e4d-131">Le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-131">The method name.</span></span> <span data-ttu-id="a4e4d-132">Le type de la méthode est défini par l' [\<Type>](type-element-net-native.md) élément parent ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="a4e4d-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="a4e4d-133">Attribut de signature</span><span class="sxs-lookup"><span data-stu-id="a4e4d-133">Signature attribute</span></span>  
  
|<span data-ttu-id="a4e4d-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="a4e4d-134">Value</span></span>|<span data-ttu-id="a4e4d-135">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4d-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4e4d-136">*signature_méthode*</span><span class="sxs-lookup"><span data-stu-id="a4e4d-136">*method_signature*</span></span>|<span data-ttu-id="a4e4d-137">Types de paramètre qui constituent la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="a4e4d-138">Si plusieurs paramètres sont présents, ils sont séparés par des virgules. Par exemple : `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="a4e4d-139">Les noms de type de paramètre doivent être qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a4e4d-140">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="a4e4d-140">All other attributes</span></span>  
  
|<span data-ttu-id="a4e4d-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="a4e4d-141">Value</span></span>|<span data-ttu-id="a4e4d-142">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4d-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4e4d-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a4e4d-143">*policy_setting*</span></span>|<span data-ttu-id="a4e4d-144">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="a4e4d-145">Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="a4e4d-146">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a4e4d-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4e4d-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a4e4d-147">Child Elements</span></span>  
  
|<span data-ttu-id="a4e4d-148">Élément</span><span class="sxs-lookup"><span data-stu-id="a4e4d-148">Element</span></span>|<span data-ttu-id="a4e4d-149">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4d-149">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="a4e4d-150">Applique la stratégie au type de l'argument passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-150">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="a4e4d-151">Applique la stratégie au type de paramètre d'un type ou d'une méthode générique.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-151">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="a4e4d-152">Applique la stratégie à un type, si cette stratégie a été appliquée à la méthode représentée par l'élément `<Method>` conteneur.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-152">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="a4e4d-153">Applique la stratégie au type représenté par un argument <xref:System.Type> passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-153">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4e4d-154">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a4e4d-154">Parent Elements</span></span>  
  
|<span data-ttu-id="a4e4d-155">Élément</span><span class="sxs-lookup"><span data-stu-id="a4e4d-155">Element</span></span>|<span data-ttu-id="a4e4d-156">Description</span><span class="sxs-lookup"><span data-stu-id="a4e4d-156">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="a4e4d-157">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-157">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="a4e4d-158">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-158">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4e4d-159">Remarques</span><span class="sxs-lookup"><span data-stu-id="a4e4d-159">Remarks</span></span>  
 <span data-ttu-id="a4e4d-160">Un élément `<Method>` d'une méthode générique applique sa stratégie à toutes les instanciations qui n'ont pas leur propre stratégie.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-160">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="a4e4d-161">Vous pouvez utiliser l'attribut `Signature` pour spécifier la stratégie d'une surcharge de méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-161">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="a4e4d-162">Sinon, si l'attribut `Signature` est absent, la directive runtime s'applique à toutes les surcharges de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-162">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="a4e4d-163">Vous ne pouvez pas définir la stratégie de réflexion runtime d'un constructeur à l'aide de l'élément `<Method>`.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-163">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="a4e4d-164">Utilisez plutôt l' `Activate` attribut de l' [\<Assembly>](assembly-element-net-native.md) élément, [\<Namespace>](namespace-element-net-native.md) , [\<Type>](type-element-net-native.md) ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="a4e4d-164">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4e4d-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4e4d-165">Example</span></span>  
 <span data-ttu-id="a4e4d-166">La méthode `Stringify` dans l'exemple suivant est une méthode de mise en forme à usage général qui utilise la réflexion pour convertir un objet sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-166">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="a4e4d-167">En plus d'appeler la méthode `ToString` par défaut de l'objet, la méthode peut produire une chaîne de résultat mise en forme en passant à la méthode `ToString` d'un objet une chaîne de format et/ou une implémentation <xref:System.IFormatProvider>.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-167">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="a4e4d-168">Elle peut également appeler l'une des surcharges <xref:System.Convert.ToString%2A?displayProperty=nameWithType> qui convertit un nombre au format binaire, hexadécimale ou octale.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-168">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="a4e4d-169">La méthode `Stringify` peut être appelée par du code comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4e4d-169">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="a4e4d-170">Toutefois, quand il est compilé avec .NET Native, l’exemple peut lever de nombreuses exceptions au moment de l’exécution, notamment les exceptions <xref:System.NullReferenceException> et [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md). En effet, la méthode `Stringify` est principalement destinée à prendre en charge la mise en forme dynamique des types primitifs dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-170">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="a4e4d-171">Cependant, leurs métadonnées ne sont pas rendues disponibles par le fichier de directives par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-171">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="a4e4d-172">Toutefois, même quand leurs métadonnées sont rendues disponibles, l’exemple lève des exceptions [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md), car les implémentations `ToString` appropriées n’ont pas été incluses dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-172">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="a4e4d-173">Ces exceptions peuvent être éliminées en utilisant l' [\<Type>](type-element-net-native.md) élément pour définir les types dont les métadonnées doivent être présentes et en ajoutant des `<Method>` éléments pour garantir que l’implémentation de surcharges de méthode qui peuvent être appelées de façon dynamique est également présente.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-173">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="a4e4d-174">Voici le fichier default.rd.xml qui élimine ces exceptions et qui permet à l'exemple de s'exécuter sans erreur.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-174">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4e4d-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4e4d-175">See also</span></span>

- [<span data-ttu-id="a4e4d-176">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a4e4d-176">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a4e4d-177">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="a4e4d-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a4e4d-178">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="a4e4d-178">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="a4e4d-179">\<MethodInstantiation>Appartient</span><span class="sxs-lookup"><span data-stu-id="a4e4d-179">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
