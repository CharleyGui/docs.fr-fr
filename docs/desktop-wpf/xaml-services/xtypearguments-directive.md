---
title: x:TypeArguments, directive
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071352"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="fca5b-102">x:TypeArguments, directive</span><span class="sxs-lookup"><span data-stu-id="fca5b-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="fca5b-103">Passes de type de contrainte arguments d’un générique au constructeur du type générique.</span><span class="sxs-lookup"><span data-stu-id="fca5b-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="fca5b-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="fca5b-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="fca5b-105">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="fca5b-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="fca5b-106">Une déclaration d’élément d’objet d’un type XAML, qui est soutenue par un type générique CLR.</span><span class="sxs-lookup"><span data-stu-id="fca5b-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="fca5b-107">Si `object` se réfère à un type XAML qui n’est `object` pas de l’espace nom XAML par défaut, nécessite un préfixe pour indiquer l’espace de nom XAML où `object` existe.</span><span class="sxs-lookup"><span data-stu-id="fca5b-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="fca5b-108">Une chaîne qui déclare un ou plusieurs noms de type XAML comme des chaînes, qui fournit les arguments de type pour le type générique CLR.</span><span class="sxs-lookup"><span data-stu-id="fca5b-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="fca5b-109">Voir Remarques pour des notes de syntaxe supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fca5b-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fca5b-110">Notes</span><span class="sxs-lookup"><span data-stu-id="fca5b-110">Remarks</span></span>

<span data-ttu-id="fca5b-111">Dans la plupart des cas, les types XAML `typeString` qui sont utilisés comme élément d’information dans une chaîne sont préfixés.</span><span class="sxs-lookup"><span data-stu-id="fca5b-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="fca5b-112">Les types typiques de contraintes <xref:System.Int32> génériques CLR (par exemple, et <xref:System.String>) proviennent de bibliothèques de classe de base CLR.</span><span class="sxs-lookup"><span data-stu-id="fca5b-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="fca5b-113">Ces bibliothèques ne sont pas cartographiées selon des espaces de noms XAML spécifiques au cadre typique et nécessitent donc une cartographie préfixe pour l’utilisation de XAML.</span><span class="sxs-lookup"><span data-stu-id="fca5b-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="fca5b-114">Vous pouvez spécifier plus d’un nom de type XAML en utilisant un délimit de virgule.</span><span class="sxs-lookup"><span data-stu-id="fca5b-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="fca5b-115">Si les contraintes génériques elles-mêmes utilisent des types génériques, les arguments de type contrainte imbriqués peuvent être contenus par parenthèses ().</span><span class="sxs-lookup"><span data-stu-id="fca5b-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="fca5b-116">Notez que `x:TypeArguments` cette définition est spécifique à .NET XAML Services et en utilisant le support CLR.</span><span class="sxs-lookup"><span data-stu-id="fca5b-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="fca5b-117">Une définition du niveau de langue se trouve dans [ \[la section 5.3.11 de MS-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="fca5b-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="fca5b-118">Exemples d’utilisation</span><span class="sxs-lookup"><span data-stu-id="fca5b-118">Usage Examples</span></span>

<span data-ttu-id="fca5b-119">Pour ces exemples, supposons que les définitions suivantes de l’espace de nom XAML sont déclarées :</span><span class="sxs-lookup"><span data-stu-id="fca5b-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="fca5b-120">Liste\<Des> de chaîne</span><span class="sxs-lookup"><span data-stu-id="fca5b-120">List\<String></span></span>

<span data-ttu-id="fca5b-121">`<scg:List x:TypeArguments="sys:String" ...>`instantanés un <xref:System.Collections.Generic.List%601> nouveau <xref:System.String> avec un argument de type.</span><span class="sxs-lookup"><span data-stu-id="fca5b-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="fca5b-122">Chaîne\<de dictionnaire,> de chaîne</span><span class="sxs-lookup"><span data-stu-id="fca5b-122">Dictionary\<String,String></span></span>

<span data-ttu-id="fca5b-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`instantiates un <xref:System.Collections.Generic.Dictionary%602> nouveau <xref:System.String> avec deux types d’arguments.</span><span class="sxs-lookup"><span data-stu-id="fca5b-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="fca5b-124">File d’attente<Chaîne\<KeyValuePair, String>></span><span class="sxs-lookup"><span data-stu-id="fca5b-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="fca5b-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`instantanés un <xref:System.Collections.Generic.Queue%601> nouveau qui a <xref:System.Collections.Generic.KeyValuePair%602> une contrainte de avec <xref:System.String> <xref:System.String>les arguments de type contrainte intérieure et .</span><span class="sxs-lookup"><span data-stu-id="fca5b-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="fca5b-126">XAML 2006 et WPF Generic XAML Usages</span><span class="sxs-lookup"><span data-stu-id="fca5b-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="fca5b-127">Pour l’utilisation de XAML 2006, et XAML qui est `x:TypeArguments` utilisé pour les applications WPF, les restrictions suivantes existent pour et les utilisations de type générique de XAML en général:</span><span class="sxs-lookup"><span data-stu-id="fca5b-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="fca5b-128">Seul l’élément racine d’un fichier XAML peut prendre en charge une utilisation générique XAML qui fait référence à un type générique.</span><span class="sxs-lookup"><span data-stu-id="fca5b-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="fca5b-129">L’élément racine doit cartographier à un type générique avec au moins un argument de type.</span><span class="sxs-lookup"><span data-stu-id="fca5b-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="fca5b-130">par exemple <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="fca5b-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="fca5b-131">Les fonctions de page sont le scénario principal pour le support d’utilisation générique XAML dans WPF.</span><span class="sxs-lookup"><span data-stu-id="fca5b-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="fca5b-132">L’élément racine XAML élément objet pour le `x:Class`générique doit également déclarer une classe partielle en utilisant .</span><span class="sxs-lookup"><span data-stu-id="fca5b-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="fca5b-133">Cela est vrai même si la définition d’une action WPF construire.</span><span class="sxs-lookup"><span data-stu-id="fca5b-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="fca5b-134">`x:TypeArguments`ne peut pas faire référence aux contraintes génériques imbriquées.</span><span class="sxs-lookup"><span data-stu-id="fca5b-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="fca5b-135">XAML 2009 ou XAML 2006 sans WPF 3.0 ou WPF 3.5 Dépendance</span><span class="sxs-lookup"><span data-stu-id="fca5b-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="fca5b-136">Dans .NET XAML Services pour XAML 2006 ou XAML 2009, les restrictions liées au WPF sur l’utilisation générique de XAML sont assouplies.</span><span class="sxs-lookup"><span data-stu-id="fca5b-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="fca5b-137">Vous pouvez instantané un élément d’objet générique à n’importe quelle position dans le balisage XAML que le système de support et le modèle d’objet peuvent prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="fca5b-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="fca5b-138">Si vous utilisez XAML 2009 au lieu de cartographier les types de base CLR pour obtenir des types XAML pour les primitifs de langage commun, vous pouvez utiliser [les types intégrés pour les primitifs de langue XAML communs](types-for-primitives.md) comme éléments d’information dans un `typeString`.</span><span class="sxs-lookup"><span data-stu-id="fca5b-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="fca5b-139">Par exemple, vous pouvez déclarer ce qui suit (les cartes préfixes non affichées, mais x est l’espace de nom XAML en langue XAML pour XAML 2009) :</span><span class="sxs-lookup"><span data-stu-id="fca5b-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="fca5b-140">Dans WPF et lors du ciblage .NET Framework 4 ou .NET Core 3.0 (ou plus `x:TypeArguments` tard), vous pouvez utiliser XAML 2009 fonctionnalités avec mais seulement pour le lâche XAML (XAML qui n’est pas compilée de balisage).</span><span class="sxs-lookup"><span data-stu-id="fca5b-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="fca5b-141">Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="fca5b-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="fca5b-142">Si vous avez besoin de compiler le XAML, vous devez opérer en vertu des restrictions indiquées dans la section [XAML 2006 et WPF Generic XAML Usages.](#xaml-2006-and-wpf-generic-xaml-usages)</span><span class="sxs-lookup"><span data-stu-id="fca5b-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="fca5b-143">BAML n’est pris en charge que dans le cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="fca5b-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="fca5b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fca5b-144">See also</span></span>

- [<span data-ttu-id="fca5b-145">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="fca5b-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="fca5b-146">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="fca5b-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="fca5b-147">Types intégrés pour les primitives associées au langage XAML courant</span><span class="sxs-lookup"><span data-stu-id="fca5b-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="fca5b-148">Génériques en XAML</span><span class="sxs-lookup"><span data-stu-id="fca5b-148">Generics in XAML</span></span>](generics.md)
