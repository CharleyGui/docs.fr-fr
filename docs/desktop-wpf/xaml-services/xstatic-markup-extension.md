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
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551609"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="ee77f-102">x:Static, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="ee77f-102">x:Static Markup Extension</span></span>

<span data-ttu-id="ee77f-103">Fait référence à toute entité de code statique par valeur définie dans une méthode conforme à la Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="ee77f-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="ee77f-104">La propriété statique référencée peut être utilisée pour fournir la valeur d’une propriété en XAML.</span><span class="sxs-lookup"><span data-stu-id="ee77f-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="ee77f-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="ee77f-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="ee77f-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="ee77f-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="ee77f-107">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="ee77f-107">Optional.</span></span> <span data-ttu-id="ee77f-108">Préfixe qui fait référence à un espace de noms XAML mappé non défini par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee77f-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="ee77f-109">`prefix` s’affiche de manière explicite dans l’utilisation, car vous référencez rarement des propriétés statiques provenant d’un espace de noms XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee77f-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="ee77f-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="ee77f-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="ee77f-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ee77f-111">Required.</span></span> <span data-ttu-id="ee77f-112">Nom du type qui définit le membre statique souhaité.</span><span class="sxs-lookup"><span data-stu-id="ee77f-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="ee77f-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ee77f-113">Required.</span></span> <span data-ttu-id="ee77f-114">Nom du membre de valeur statique souhaité (une constante, une propriété statique, un champ ou une valeur d’énumération).</span><span class="sxs-lookup"><span data-stu-id="ee77f-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="ee77f-115">Notes</span><span class="sxs-lookup"><span data-stu-id="ee77f-115">Remarks</span></span>

<span data-ttu-id="ee77f-116">L’entité de code référencée doit être l’une des suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee77f-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="ee77f-117">Une constante</span><span class="sxs-lookup"><span data-stu-id="ee77f-117">A constant</span></span>
- <span data-ttu-id="ee77f-118">Une propriété statique</span><span class="sxs-lookup"><span data-stu-id="ee77f-118">A static property</span></span>
- <span data-ttu-id="ee77f-119">Un champ</span><span class="sxs-lookup"><span data-stu-id="ee77f-119">A field</span></span>
- <span data-ttu-id="ee77f-120">Valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="ee77f-120">An enumeration value</span></span>

<span data-ttu-id="ee77f-121">La spécification d’une autre entité de code, telle qu’une propriété non statique, provoque une erreur au moment de la compilation si le XAML est compilé par balisage, ou une exception d’analyse au moment du chargement XAML.</span><span class="sxs-lookup"><span data-stu-id="ee77f-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="ee77f-122">Vous pouvez créer `x:Static` des références à des champs ou des propriétés statiques qui ne sont pas dans l’espace de noms XAML par défaut pour le document XAML actuel ; Toutefois, cela nécessite un mappage de préfixe.</span><span class="sxs-lookup"><span data-stu-id="ee77f-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="ee77f-123">Les espaces de noms XAML sont presque toujours définis sur l’élément racine du document XAML.</span><span class="sxs-lookup"><span data-stu-id="ee77f-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="ee77f-124">Les opérations de recherche pour les propriétés statiques peuvent être effectuées par les services XAML .NET et ses lecteurs et writers XAML, lorsqu’ils s’exécutent avec le contexte de schéma XAML par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee77f-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="ee77f-125">Ce contexte de schéma XAML peut utiliser la réflexion CLR pour fournir les valeurs statiques nécessaires pour la construction du graphique d’objets.</span><span class="sxs-lookup"><span data-stu-id="ee77f-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="ee77f-126">Le `typeName` que vous spécifiez est en fait un nom de type XAML, et non un nom de type CLR, bien qu’il s’agisse d’un nom identique lors de l’utilisation du contexte de schéma XAML par défaut ou de l’utilisation de tous les frameworks d’implémentation XAML basés sur CLR existants.</span><span class="sxs-lookup"><span data-stu-id="ee77f-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="ee77f-127">Soyez prudent lorsque vous faites `x:Static` des références qui ne sont pas directement le type de la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="ee77f-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="ee77f-128">Dans la séquence de traitement XAML, les valeurs fournies par une extension de balisage n’appellent pas la conversion de valeur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="ee77f-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="ee77f-129">Cela est vrai même si votre `x:Static` référence crée une chaîne de texte, et une conversion de valeur pour les valeurs d’attribut basées sur une chaîne de texte se produit généralement pour ce membre spécifique ou pour toutes les valeurs de membre du type de retour.</span><span class="sxs-lookup"><span data-stu-id="ee77f-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="ee77f-130">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="ee77f-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="ee77f-131">Le jeton de chaîne fourni après la chaîne d’identificateur `x:Static` est assigné en tant que valeur <xref:System.Windows.Markup.StaticExtension.Member%2A> de la classe d’extension <xref:System.Windows.Markup.StaticExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="ee77f-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="ee77f-132">Il existe deux autres utilisations de XAML qui sont techniquement possibles.</span><span class="sxs-lookup"><span data-stu-id="ee77f-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="ee77f-133">Toutefois, ces utilisations sont moins courantes, car elles sont inutilement détaillées :</span><span class="sxs-lookup"><span data-stu-id="ee77f-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="ee77f-134">Syntaxe d’élément objet.</span><span class="sxs-lookup"><span data-stu-id="ee77f-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="ee77f-135">Syntaxe d’attribut avec propriété de membre explicite pour la chaîne d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="ee77f-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="ee77f-136">Dans l’implémentation des services XAML .NET, la gestion de cette extension de balisage est définie par la <xref:System.Windows.Markup.StaticExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="ee77f-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="ee77f-137">`x:Static` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="ee77f-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="ee77f-138">Toutes les extensions de balisage en XAML utilisent les `{` `}` caractères et dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="ee77f-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="ee77f-139">Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee77f-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="ee77f-140">Remarques sur l'utilisation de WPF</span><span class="sxs-lookup"><span data-stu-id="ee77f-140">WPF Usage Notes</span></span>

<span data-ttu-id="ee77f-141">L’espace de noms XAML par défaut que vous utilisez pour la programmation WPF ne contient pas de nombreuses propriétés statiques utiles, et la plupart des propriétés statiques utiles prennent en charge des convertisseurs de type qui facilitent l’utilisation sans nécessiter `{x:Static}` .</span><span class="sxs-lookup"><span data-stu-id="ee77f-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="ee77f-142">Pour les propriétés statiques, vous devez mapper un préfixe pour un espace de noms XAML si l’une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="ee77f-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="ee77f-143">Vous référencez un type qui existe dans WPF, mais qui ne fait pas partie de l’espace de noms XAML par défaut pour WPF ( `http://schemas.microsoft.com/winfx/2006/xaml/presentation` ).</span><span class="sxs-lookup"><span data-stu-id="ee77f-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="ee77f-144">Il s’agit d’un scénario assez courant pour l’utilisation de `x:Static` .</span><span class="sxs-lookup"><span data-stu-id="ee77f-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="ee77f-145">Par exemple, vous pouvez utiliser une `x:Static` référence avec un mappage d’espace de noms XAML à l' <xref:System> espace de noms CLR et à l’assembly mscorlib pour référencer les propriétés statiques de la <xref:System.Environment> classe.</span><span class="sxs-lookup"><span data-stu-id="ee77f-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="ee77f-146">Vous référencez un type à partir d’un assembly personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ee77f-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="ee77f-147">Vous référencez un type qui existe dans un assembly WPF, mais ce type se trouve dans un espace de noms CLR qui n’a pas été mappé pour faire partie de l’espace de noms XAML par défaut WPF.</span><span class="sxs-lookup"><span data-stu-id="ee77f-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="ee77f-148">Le mappage des espaces de noms CLR dans l’espace de noms XAML par défaut pour WPF est effectué par les définitions dans les différents assemblys WPF (pour plus d’informations sur ce concept, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span><span class="sxs-lookup"><span data-stu-id="ee77f-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span></span> <span data-ttu-id="ee77f-149">Les espaces de noms CLR non mappés peuvent exister si cet espace de noms CLR est composé principalement de définitions de classe qui ne sont généralement pas prévues pour XAML, telles que <xref:System.Windows.Threading> .</span><span class="sxs-lookup"><span data-stu-id="ee77f-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="ee77f-150">Pour plus d’informations sur l’utilisation des préfixes et des espaces de noms XAML pour WPF, consultez [espaces de noms XAML et mappage d’espace de noms pour XAML WPF](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="ee77f-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee77f-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee77f-151">See also</span></span>

- [<span data-ttu-id="ee77f-152">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="ee77f-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="ee77f-153">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="ee77f-153">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
