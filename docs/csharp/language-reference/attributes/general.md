---
title: 'Attributs réservés C# : Conditional, Obsolete, AttributeUsage'
ms.date: 04/09/2020
description: Ces attributs sont interprétés par le compilateur pour affecter le code généré par le compilateur.
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021764"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="0f3dc-103">Attributs réservés : ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="0f3dc-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="0f3dc-104">Ces attributs peuvent être appliqués aux éléments de votre code.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="0f3dc-105">Ils ajoutent une signification sémantique à ces éléments.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="0f3dc-106">Le compilateur utilise ces significations sémantiques pour modifier sa sortie et signaler les erreurs possibles par les développeurs qui utilisent votre code.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="0f3dc-107">Attribut `Conditional`</span><span class="sxs-lookup"><span data-stu-id="0f3dc-107">`Conditional` attribute</span></span>

<span data-ttu-id="0f3dc-108">Avec l’attribut `Conditional`, l’exécution d’une méthode dépend d’un identificateur de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="0f3dc-109">L’attribut `Conditional` est un alias pour <xref:System.Diagnostics.ConditionalAttribute>, et peut être appliqué à une méthode ou une classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="0f3dc-110">Dans l’exemple suivant, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage des informations de diagnostic spécifiques au programme :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="0f3dc-111">Si l' `TRACE_ON` identificateur n’est pas défini, la sortie de trace n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="0f3dc-112">Explorez par vous-même dans la fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="0f3dc-113">L' `Conditional` attribut est souvent utilisé avec l' `DEBUG` identificateur pour activer les fonctionnalités de suivi et de journalisation pour les versions Debug, mais pas dans les versions release, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="0f3dc-114">Quand une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="0f3dc-115">Si le symbole est défini, l’appel est inclus ; sinon, il est omis.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="0f3dc-116">Une méthode conditionnelle doit être une méthode dans une déclaration de classe ou de struct et doit avoir un `void` type de retour.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="0f3dc-117">L’utilisation de `Conditional` est plus propre, plus élégante et moins sujette aux erreurs que les méthodes englobantes à l’intérieur des `#if…#endif` blocs.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="0f3dc-118">Si une méthode a plusieurs `Conditional` attributs, un appel à la méthode est inclus si un ou plusieurs symboles conditionnels sont définis (les symboles sont logiquement liés ensemble à l’aide de l’opérateur or).</span><span class="sxs-lookup"><span data-stu-id="0f3dc-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="0f3dc-119">Dans l’exemple suivant, la présence d' `A` un ou de `B` résultats dans un appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="0f3dc-120">Utiliser `Conditional` avec des classes d’attributs</span><span class="sxs-lookup"><span data-stu-id="0f3dc-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="0f3dc-121">L’attribut `Conditional` peut également être appliqué à une définition de classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="0f3dc-122">Dans l’exemple suivant, l’attribut personnalisé `Documentation` ajoute uniquement des informations aux métadonnées si `DEBUG` est défini.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="0f3dc-123">Attribut `Obsolete`</span><span class="sxs-lookup"><span data-stu-id="0f3dc-123">`Obsolete` attribute</span></span>

<span data-ttu-id="0f3dc-124">L' `Obsolete` attribut marque un élément de code comme n’est plus recommandé pour une utilisation.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="0f3dc-125">L’utilisation d’une entité marquée comme obsolète génère un avertissement ou une erreur.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="0f3dc-126">`Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="0f3dc-127">`Obsolete` est un alias pour <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="0f3dc-128">Dans l’exemple suivant, l' `Obsolete` attribut est appliqué à la classe `A` et à la méthode `B.OldMethod` .</span><span class="sxs-lookup"><span data-stu-id="0f3dc-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="0f3dc-129">Comme le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a la valeur `true`, l’utilisation de cette méthode entraîne une erreur du compilateur, alors que l’utilisation de la classe `A` n’entraîne qu’un avertissement.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="0f3dc-130">Toutefois, l’appel de `B.NewMethod` ne produit aucun avertissement ni aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="0f3dc-131">Par exemple, utilisé avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="0f3dc-132">La chaîne fournie comme premier argument au constructeur d’attribut sera affichée dans le cadre de l’avertissement ou de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="0f3dc-133">Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="0f3dc-134">L' `Obsolete` attribut peut être utilisé sans arguments, mais il est recommandé d’utiliser à la place une explication.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="0f3dc-135">Attribut `AttributeUsage`</span><span class="sxs-lookup"><span data-stu-id="0f3dc-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="0f3dc-136">L' `AttributeUsage` attribut détermine la manière dont une classe d’attributs personnalisés peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="0f3dc-137"><xref:System.AttributeUsageAttribute> est un attribut que vous appliquez à des définitions d’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="0f3dc-138">L’attribut `AttributeUsage` vous permet de contrôler :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="0f3dc-139">À quels éléments de programme les attributs peuvent être appliqués.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="0f3dc-140">Sauf si vous en limitez l’utilisation, un attribut peut être appliqué aux éléments de programme suivants :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="0f3dc-141">assembly</span><span class="sxs-lookup"><span data-stu-id="0f3dc-141">assembly</span></span>
  - <span data-ttu-id="0f3dc-142">module</span><span class="sxs-lookup"><span data-stu-id="0f3dc-142">module</span></span>
  - <span data-ttu-id="0f3dc-143">field</span><span class="sxs-lookup"><span data-stu-id="0f3dc-143">field</span></span>
  - <span data-ttu-id="0f3dc-144">event</span><span class="sxs-lookup"><span data-stu-id="0f3dc-144">event</span></span>
  - <span data-ttu-id="0f3dc-145">method</span><span class="sxs-lookup"><span data-stu-id="0f3dc-145">method</span></span>
  - <span data-ttu-id="0f3dc-146">param</span><span class="sxs-lookup"><span data-stu-id="0f3dc-146">param</span></span>
  - <span data-ttu-id="0f3dc-147">propriété</span><span class="sxs-lookup"><span data-stu-id="0f3dc-147">property</span></span>
  - <span data-ttu-id="0f3dc-148">return</span><span class="sxs-lookup"><span data-stu-id="0f3dc-148">return</span></span>
  - <span data-ttu-id="0f3dc-149">type</span><span class="sxs-lookup"><span data-stu-id="0f3dc-149">type</span></span>
- <span data-ttu-id="0f3dc-150">Si un attribut peut être appliqué plusieurs fois à un même élément de programme.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="0f3dc-151">Si les attributs sont hérités dans les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="0f3dc-152">L’exemple suivant montre des paramètres par défaut quand ils sont appliqués explicitement :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="0f3dc-153">Dans cet exemple, la classe `NewAttribute` peut être appliquée à n’importe quel élément de programme pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="0f3dc-154">Elle ne peut cependant être appliquée qu’une seule fois à chaque entité.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="0f3dc-155">L’attribut est hérité par les classes dérivées quand il est appliqué à une classe de base.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="0f3dc-156">Les arguments <xref:System.AttributeUsageAttribute.AllowMultiple> et <xref:System.AttributeUsageAttribute.Inherited> étant facultatifs, le code suivant a le même effet :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="0f3dc-157">Le premier argument <xref:System.AttributeUsageAttribute> doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="0f3dc-158">Vous pouvez lier ensemble plusieurs types de cibles avec l’opérateur OR, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="0f3dc-159">À compter de C# 7.3, les attributs peuvent être appliqués à la propriété ou au champ de stockage pour une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="0f3dc-160">L’attribut s’applique à la propriété, sauf si vous spécifiez le spécificateur `field` sur l’attribut.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="0f3dc-161">Les deux cas sont illustrés dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="0f3dc-162">Si l’argument <xref:System.AttributeUsageAttribute.AllowMultiple> est défini sur `true`, l’attribut résultant peut être appliqué plusieurs fois à une même entité, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="0f3dc-163">Dans ce cas, `MultiUseAttribute` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="0f3dc-164">Les deux formats indiqués pour appliquer plusieurs attributs sont valides.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="0f3dc-165">Si <xref:System.AttributeUsageAttribute.Inherited> est `false`, l’attribut n’est pas hérité par les classes dérivées d’une classe avec attributs.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="0f3dc-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0f3dc-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="0f3dc-167">Dans ce cas, `NonInheritedAttribute` n’est pas appliqué à `DClass` via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="0f3dc-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f3dc-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f3dc-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="0f3dc-169">Attributs</span><span class="sxs-lookup"><span data-stu-id="0f3dc-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="0f3dc-170">Réflexion</span><span class="sxs-lookup"><span data-stu-id="0f3dc-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
