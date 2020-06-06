---
title: <MethodInstantiation>, Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128327"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="bec4f-102">\<MethodInstantiation>, Élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="bec4f-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="bec4f-103">Applique la stratégie de réflexion runtime à une méthode générique construite.</span><span class="sxs-lookup"><span data-stu-id="bec4f-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bec4f-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bec4f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bec4f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bec4f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bec4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bec4f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="bec4f-107">Attributes</span></span>  
  
|<span data-ttu-id="bec4f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="bec4f-108">Attribute</span></span>|<span data-ttu-id="bec4f-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="bec4f-109">Attribute type</span></span>|<span data-ttu-id="bec4f-110">Description</span><span class="sxs-lookup"><span data-stu-id="bec4f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="bec4f-111">Général</span><span class="sxs-lookup"><span data-stu-id="bec4f-111">General</span></span>|<span data-ttu-id="bec4f-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="bec4f-112">Required attribute.</span></span> <span data-ttu-id="bec4f-113">Spécifie le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bec4f-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="bec4f-114">Général</span><span class="sxs-lookup"><span data-stu-id="bec4f-114">General</span></span>|<span data-ttu-id="bec4f-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="bec4f-115">Optional attribute.</span></span> <span data-ttu-id="bec4f-116">Spécifie les paramètres nommés de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bec4f-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="bec4f-117">Si plusieurs paramètres nommés sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="bec4f-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="bec4f-118">L'attribut `Signature` est utilisé pour différencier les méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="bec4f-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="bec4f-119">Général</span><span class="sxs-lookup"><span data-stu-id="bec4f-119">General</span></span>|<span data-ttu-id="bec4f-120">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="bec4f-120">Required attribute.</span></span> <span data-ttu-id="bec4f-121">Spécifie les arguments de type générique.</span><span class="sxs-lookup"><span data-stu-id="bec4f-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="bec4f-122">Si plusieurs arguments sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="bec4f-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="bec4f-123">Réflexion</span><span class="sxs-lookup"><span data-stu-id="bec4f-123">Reflection</span></span>|<span data-ttu-id="bec4f-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="bec4f-124">Optional attribute.</span></span> <span data-ttu-id="bec4f-125">Contrôle la demande d'informations sur une méthode ou l'énumération de celle-ci, mais ne permet pas d'effectuer un appel dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="bec4f-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="bec4f-126">Réflexion</span><span class="sxs-lookup"><span data-stu-id="bec4f-126">Reflection</span></span>|<span data-ttu-id="bec4f-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="bec4f-127">Optional attribute.</span></span> <span data-ttu-id="bec4f-128">Contrôle l'accès à un constructeur ou à une méthode au moment de l'exécution pour activer la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="bec4f-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="bec4f-129">Cette stratégie garantit que le membre peut être appelé dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="bec4f-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="bec4f-130">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="bec4f-130">Name attribute</span></span>  
  
|<span data-ttu-id="bec4f-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="bec4f-131">Value</span></span>|<span data-ttu-id="bec4f-132">Description</span><span class="sxs-lookup"><span data-stu-id="bec4f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bec4f-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="bec4f-133">*method_name*</span></span>|<span data-ttu-id="bec4f-134">Le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bec4f-134">The method name.</span></span> <span data-ttu-id="bec4f-135">Le type de la méthode est défini par l' [\<Type>](type-element-net-native.md) élément parent ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="bec4f-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="bec4f-136">Attribut de signature</span><span class="sxs-lookup"><span data-stu-id="bec4f-136">Signature attribute</span></span>  
  
|<span data-ttu-id="bec4f-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="bec4f-137">Value</span></span>|<span data-ttu-id="bec4f-138">Description</span><span class="sxs-lookup"><span data-stu-id="bec4f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bec4f-139">*signature_méthode*</span><span class="sxs-lookup"><span data-stu-id="bec4f-139">*method_signature*</span></span>|<span data-ttu-id="bec4f-140">Spécifie les paramètres nommés de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bec4f-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="bec4f-141">Si plusieurs paramètres sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="bec4f-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="bec4f-142">Attribut Arguments</span><span class="sxs-lookup"><span data-stu-id="bec4f-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="bec4f-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="bec4f-143">Value</span></span>|<span data-ttu-id="bec4f-144">Description</span><span class="sxs-lookup"><span data-stu-id="bec4f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bec4f-145">*arguments_méthode*</span><span class="sxs-lookup"><span data-stu-id="bec4f-145">*method_arguments*</span></span>|<span data-ttu-id="bec4f-146">Spécifie les arguments de type générique.</span><span class="sxs-lookup"><span data-stu-id="bec4f-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="bec4f-147">Si plusieurs arguments sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="bec4f-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="bec4f-148">Chaque argument doit être composé du nom de type qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="bec4f-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="bec4f-149">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="bec4f-149">All other attributes</span></span>  
  
|<span data-ttu-id="bec4f-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="bec4f-150">Value</span></span>|<span data-ttu-id="bec4f-151">Description</span><span class="sxs-lookup"><span data-stu-id="bec4f-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bec4f-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="bec4f-152">*policy_setting*</span></span>|<span data-ttu-id="bec4f-153">Paramètre à appliquer à ce type de stratégie pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="bec4f-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="bec4f-154">Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`.</span><span class="sxs-lookup"><span data-stu-id="bec4f-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="bec4f-155">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="bec4f-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bec4f-156">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bec4f-156">Child Elements</span></span>  
 <span data-ttu-id="bec4f-157">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bec4f-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bec4f-158">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bec4f-158">Parent Elements</span></span>  
  
|<span data-ttu-id="bec4f-159">Élément</span><span class="sxs-lookup"><span data-stu-id="bec4f-159">Element</span></span>|<span data-ttu-id="bec4f-160">Description</span><span class="sxs-lookup"><span data-stu-id="bec4f-160">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="bec4f-161">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="bec4f-161">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="bec4f-162">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="bec4f-162">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bec4f-163">Remarques</span><span class="sxs-lookup"><span data-stu-id="bec4f-163">Remarks</span></span>  
 <span data-ttu-id="bec4f-164">L'élément `<MethodInstantiation>` remplace la stratégie de réflexion runtime de la méthode générique ouverte correspondante.</span><span class="sxs-lookup"><span data-stu-id="bec4f-164">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec4f-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bec4f-165">See also</span></span>

- [<span data-ttu-id="bec4f-166">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="bec4f-166">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="bec4f-167">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="bec4f-167">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="bec4f-168">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="bec4f-168">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="bec4f-169">\<Method>Appartient</span><span class="sxs-lookup"><span data-stu-id="bec4f-169">\<Method> Element</span></span>](method-element-net-native.md)
