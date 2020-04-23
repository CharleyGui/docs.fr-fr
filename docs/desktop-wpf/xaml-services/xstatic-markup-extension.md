---
title: x:Static, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072024"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="eac9c-102">x:Static, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="eac9c-102">x:Static Markup Extension</span></span>

<span data-ttu-id="eac9c-103">Mentionne toute entité de code de valeur nominale statique qui est définie d’une manière conforme à la spécification linguistique commune (CLS).</span><span class="sxs-lookup"><span data-stu-id="eac9c-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="eac9c-104">La propriété statique qui est référencée peut être utilisée pour fournir la valeur d’une propriété dans XAML.</span><span class="sxs-lookup"><span data-stu-id="eac9c-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="eac9c-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="eac9c-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="eac9c-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="eac9c-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="eac9c-107">facultatif.</span><span class="sxs-lookup"><span data-stu-id="eac9c-107">Optional.</span></span> <span data-ttu-id="eac9c-108">Un préfixe qui fait référence à un espace de nom XAML cartographié et non par défaut.</span><span class="sxs-lookup"><span data-stu-id="eac9c-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="eac9c-109">`prefix`est montré explicitement dans l’utilisation parce que vous faites rarement référence aux propriétés statiques qui proviennent d’un espace de nom XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="eac9c-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="eac9c-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="eac9c-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="eac9c-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eac9c-111">Required.</span></span> <span data-ttu-id="eac9c-112">Le nom du type qui définit le membre statique désiré.</span><span class="sxs-lookup"><span data-stu-id="eac9c-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="eac9c-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eac9c-113">Required.</span></span> <span data-ttu-id="eac9c-114">Le nom du membre de valeur statique souhaité (une constante, une propriété statique, un champ ou une valeur de recensement).</span><span class="sxs-lookup"><span data-stu-id="eac9c-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="eac9c-115">Notes</span><span class="sxs-lookup"><span data-stu-id="eac9c-115">Remarks</span></span>

<span data-ttu-id="eac9c-116">L’entité de code référencée doit être l’une des suivantes :</span><span class="sxs-lookup"><span data-stu-id="eac9c-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="eac9c-117">Une constante</span><span class="sxs-lookup"><span data-stu-id="eac9c-117">A constant</span></span>
- <span data-ttu-id="eac9c-118">Une propriété statique</span><span class="sxs-lookup"><span data-stu-id="eac9c-118">A static property</span></span>
- <span data-ttu-id="eac9c-119">Un champ</span><span class="sxs-lookup"><span data-stu-id="eac9c-119">A field</span></span>
- <span data-ttu-id="eac9c-120">Une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="eac9c-120">An enumeration value</span></span>

<span data-ttu-id="eac9c-121">Spécifier toute autre entité de code, telle qu’une propriété non indiquée, provoque une erreur de compilation-temps si le XAML est compilé, ou une exception XAML de temps de charge.</span><span class="sxs-lookup"><span data-stu-id="eac9c-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="eac9c-122">Vous pouvez `x:Static` faire des références à des champs statiques ou des propriétés qui ne sont pas dans l’espace de nom XAML par défaut pour le document XAML actuel; cependant, cela nécessite une cartographie préfixe.</span><span class="sxs-lookup"><span data-stu-id="eac9c-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="eac9c-123">Les espaces de noms XAML sont presque toujours définis sur l’élément racine du document XAML.</span><span class="sxs-lookup"><span data-stu-id="eac9c-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="eac9c-124">Les opérations de recherche pour les propriétés statiques peuvent être effectuées par .NET XAML Services et ses lecteurs XAML et les écrivains XAML, quand ils sont en cours d’exécution avec le contexte de schéma XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="eac9c-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="eac9c-125">Ce contexte de schéma XAML peut utiliser la réflexion CLR pour fournir les valeurs statiques nécessaires pour la construction de graphiques d’objets.</span><span class="sxs-lookup"><span data-stu-id="eac9c-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="eac9c-126">Le `typeName` nom que vous spécifiez est en fait un nom de type XAML, pas un nom de type CLR, bien que ce sont essentiellement le même nom lors de l’utilisation du contexte par défaut de schéma XAML ou lors de l’utilisation de tous les cadres existants à base de CLR XAML-mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="eac9c-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="eac9c-127">Faites preuve de `x:Static` prudence lorsque vous faites des références qui ne sont pas directement le type de valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="eac9c-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="eac9c-128">Dans la séquence de traitement XAML, les valeurs fournies à partir d’une extension de balisage n’invoquent pas la conversion de valeur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="eac9c-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="eac9c-129">Cela est vrai `x:Static` même si votre référence crée une chaîne de texte, et une conversion de valeur pour les valeurs d’attribut basée sur la chaîne de texte se produit généralement soit pour ce membre spécifique ou pour les valeurs membres du type de retour.</span><span class="sxs-lookup"><span data-stu-id="eac9c-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="eac9c-130">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="eac9c-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="eac9c-131">Le jeton de chaîne fourni après la chaîne d’identificateur `x:Static` est assigné en tant que valeur <xref:System.Windows.Markup.StaticExtension.Member%2A> de la classe d’extension <xref:System.Windows.Markup.StaticExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="eac9c-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="eac9c-132">Il y a deux autres utilisations de XAML qui sont techniquement possibles.</span><span class="sxs-lookup"><span data-stu-id="eac9c-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="eac9c-133">Cependant, ces utilisations sont moins fréquentes parce qu’elles sont inutilement verbeuses :</span><span class="sxs-lookup"><span data-stu-id="eac9c-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="eac9c-134">Syntaxe d’élément d’objet.</span><span class="sxs-lookup"><span data-stu-id="eac9c-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="eac9c-135">Attribuer la syntaxe avec la propriété explicite du membre pour la chaîne d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="eac9c-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="eac9c-136">Dans la mise en œuvre de .NET XAML <xref:System.Windows.Markup.StaticExtension> Services, le traitement de cette extension de balisage est défini par la classe.</span><span class="sxs-lookup"><span data-stu-id="eac9c-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="eac9c-137">`x:Static` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="eac9c-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="eac9c-138">Toutes les extensions de balisage dans XAML utilisent la `{` syntaxe d’attribut, `}` qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="eac9c-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="eac9c-139">Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eac9c-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="eac9c-140">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="eac9c-140">WPF Usage Notes</span></span>

<span data-ttu-id="eac9c-141">L’espace de nom XAML par défaut que vous utilisez pour la programmation WPF ne contient pas de nombreuses `{x:Static}` propriétés statiques utiles, et la plupart des propriétés statiques utiles ont pris en charge tels que les convertisseurs de type qui facilitent l’utilisation sans avoir besoin .</span><span class="sxs-lookup"><span data-stu-id="eac9c-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="eac9c-142">Pour les propriétés statiques, vous devez cartographier un préfixe pour un espace de nom XAML si l’un des éléments suivants est vrai :</span><span class="sxs-lookup"><span data-stu-id="eac9c-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="eac9c-143">Vous faites référence à un type qui existe dans WPF mais ne fait pas`http://schemas.microsoft.com/winfx/2006/xaml/presentation`partie de l’espace de nom XAML par défaut pour WPF ( ).</span><span class="sxs-lookup"><span data-stu-id="eac9c-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="eac9c-144">Il s’agit d’un scénario assez commun pour l’utilisation `x:Static`.</span><span class="sxs-lookup"><span data-stu-id="eac9c-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="eac9c-145">Par exemple, vous `x:Static` pouvez utiliser une référence avec une <xref:System> cartographie XAML namespace à l’espace de <xref:System.Environment> nom CLR et l’assemblage mscorlib afin de référencer les propriétés statiques de la classe.</span><span class="sxs-lookup"><span data-stu-id="eac9c-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="eac9c-146">Vous faites référence à un type d’assemblage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="eac9c-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="eac9c-147">Vous faites référence à un type qui existe dans un assemblage WPF, mais ce type est dans un espace de nom CLR qui n’a pas été cartographié pour faire partie de l’espace de nom par défaut WPF XAML.</span><span class="sxs-lookup"><span data-stu-id="eac9c-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="eac9c-148">La cartographie des espaces de noms CLR dans l’espace de nom XAML par défaut pour WPF est effectuée par définition dans les différents assemblages WPF (pour plus d’informations sur ce concept, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="eac9c-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="eac9c-149">Les espaces de noms CLR non cartographiés peuvent exister si cet espace de nom CLR est <xref:System.Windows.Threading>composé principalement de définitions de classe qui ne sont généralement pas destinées à XAML, telles que .</span><span class="sxs-lookup"><span data-stu-id="eac9c-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="eac9c-150">Pour plus d’informations sur la façon d’utiliser les préfixes et les espaces de noms XAML pour WPF, voir [XAML Namespaces et Namespace Mapping pour WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="eac9c-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eac9c-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eac9c-151">See also</span></span>

- [<span data-ttu-id="eac9c-152">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="eac9c-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="eac9c-153">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="eac9c-153">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
