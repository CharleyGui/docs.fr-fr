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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837192"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="779d2-102">x:TypeArguments, directive</span><span class="sxs-lookup"><span data-stu-id="779d2-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="779d2-103">Passe des arguments de type de restriction d’un générique au constructeur du type générique.</span><span class="sxs-lookup"><span data-stu-id="779d2-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="779d2-104">Utilisation des attributs XAML</span><span class="sxs-lookup"><span data-stu-id="779d2-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="779d2-105">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="779d2-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="779d2-106">Déclaration d’élément objet d’un type XAML, qui est stockée par un type CLR générique.</span><span class="sxs-lookup"><span data-stu-id="779d2-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="779d2-107">Si `object` fait référence à un type XAML qui ne provient pas de l’espace de noms XAML par défaut, `object` requiert un préfixe pour indiquer l’espace de noms XAML dans lequel `object` existe.</span><span class="sxs-lookup"><span data-stu-id="779d2-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="779d2-108">Chaîne qui déclare un ou plusieurs noms de types XAML sous forme de chaînes, qui fournit les arguments de type pour le type générique CLR.</span><span class="sxs-lookup"><span data-stu-id="779d2-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="779d2-109">Consultez la section Notes pour obtenir des remarques supplémentaires sur la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="779d2-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="779d2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="779d2-110">Remarks</span></span>  
 <span data-ttu-id="779d2-111">Dans la plupart des cas, les types XAML qui sont utilisés comme élément d’information dans une chaîne `typeString` sont préfixés.</span><span class="sxs-lookup"><span data-stu-id="779d2-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="779d2-112">Les types typiques de contraintes génériques CLR (par exemple, <xref:System.Int32> et <xref:System.String>) proviennent des bibliothèques de classes de base CLR.</span><span class="sxs-lookup"><span data-stu-id="779d2-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="779d2-113">Ces bibliothèques ne sont pas mappées à des espaces de noms XAML par défaut propres à un Framework standard, et par conséquent requièrent un mappage de préfixe pour l’utilisation de XAML.</span><span class="sxs-lookup"><span data-stu-id="779d2-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="779d2-114">Vous pouvez spécifier plusieurs noms de type XAML à l’aide d’un délimiteur de virgule.</span><span class="sxs-lookup"><span data-stu-id="779d2-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="779d2-115">Si les contraintes génériques elles-mêmes utilisent des types génériques, les arguments de type de contrainte imbriquée peuvent être contenus entre parenthèses ().</span><span class="sxs-lookup"><span data-stu-id="779d2-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="779d2-116">Notez que cette définition de `x:TypeArguments` est spécifique à .NET Framework les services XAML et à l’utilisation du stockage CLR.</span><span class="sxs-lookup"><span data-stu-id="779d2-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="779d2-117">Une définition au niveau du langage se trouve dans [\[Section\] MS-XAML 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="779d2-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="779d2-118">Exemples d’utilisation</span><span class="sxs-lookup"><span data-stu-id="779d2-118">Usage Examples</span></span>  
 <span data-ttu-id="779d2-119">Pour ces exemples, supposez que les définitions d’espace de noms XAML suivantes sont déclarées :</span><span class="sxs-lookup"><span data-stu-id="779d2-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="779d2-120">Liste\<chaîne ></span><span class="sxs-lookup"><span data-stu-id="779d2-120">List\<String></span></span>  
 <span data-ttu-id="779d2-121">`<scg:List x:TypeArguments="sys:String" ...>` instancie une nouvelle <xref:System.Collections.Generic.List%601> avec un argument de type <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="779d2-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="779d2-122">Dictionary\<String, String ></span><span class="sxs-lookup"><span data-stu-id="779d2-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="779d2-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instancie une nouvelle <xref:System.Collections.Generic.Dictionary%602> avec deux arguments de type <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="779d2-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="779d2-124">Queue < KeyValuePair\<String, String > ></span><span class="sxs-lookup"><span data-stu-id="779d2-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="779d2-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instancie une nouvelle <xref:System.Collections.Generic.Queue%601> qui a une contrainte de <xref:System.Collections.Generic.KeyValuePair%602> avec les arguments de type de contrainte interne <xref:System.String> et <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="779d2-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="779d2-126">XAML 2006 et utilisations XAML génériques WPF</span><span class="sxs-lookup"><span data-stu-id="779d2-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="779d2-127">Pour l’utilisation de XAML 2006 et XAML utilisé pour les applications WPF, les restrictions suivantes existent pour les `x:TypeArguments` et les utilisations de type générique à partir de XAML en général :</span><span class="sxs-lookup"><span data-stu-id="779d2-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
- <span data-ttu-id="779d2-128">Seul l’élément racine d’un fichier XAML peut prendre en charge une utilisation générique XAML qui référence un type générique.</span><span class="sxs-lookup"><span data-stu-id="779d2-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
- <span data-ttu-id="779d2-129">L’élément racine doit être mappé à un type générique avec au moins un argument de type.</span><span class="sxs-lookup"><span data-stu-id="779d2-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="779d2-130">par exemple <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="779d2-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="779d2-131">Les fonctions de page sont le scénario principal pour la prise en charge de l’utilisation générique XAML dans WPF.</span><span class="sxs-lookup"><span data-stu-id="779d2-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
- <span data-ttu-id="779d2-132">L’élément racine élément objet XAML pour le générique doit également déclarer une classe partielle à l’aide de `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="779d2-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="779d2-133">Cela est vrai même si vous définissez une action de génération WPF.</span><span class="sxs-lookup"><span data-stu-id="779d2-133">This is true even if defining a WPF build action.</span></span>  
  
- <span data-ttu-id="779d2-134">`x:TypeArguments` ne peut pas faire référence à des contraintes génériques imbriquées.</span><span class="sxs-lookup"><span data-stu-id="779d2-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="779d2-135">XAML 2009 ou XAML 2006 sans dépendance WPF 3,0 ou 3,5 WPF</span><span class="sxs-lookup"><span data-stu-id="779d2-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="779d2-136">Dans .NET Framework les services XAML pour XAML 2006 ou XAML 2009, les restrictions liées à WPF sur l’utilisation de XAML générique sont assouplies.</span><span class="sxs-lookup"><span data-stu-id="779d2-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="779d2-137">Vous pouvez instancier un élément objet générique à n’importe quelle position dans le balisage XAML que le système de type de stockage et le modèle objet peuvent prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="779d2-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="779d2-138">Si vous utilisez XAML 2009 au lieu de mapper les types de base CLR pour obtenir des types XAML pour les primitives de langage courantes, vous pouvez utiliser [des types intégrés pour les primitives de langage XAML courantes](built-in-types-for-common-xaml-language-primitives.md) en tant qu’éléments d’information dans un `typeString`.</span><span class="sxs-lookup"><span data-stu-id="779d2-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="779d2-139">Par exemple, vous pouvez déclarer ce qui suit (les mappages de préfixe ne sont pas affichés, mais x est l’espace de noms XAML du langage XAML pour XAML 2009) :</span><span class="sxs-lookup"><span data-stu-id="779d2-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="779d2-140">Dans WPF et lorsque vous ciblez .NET Framework 4, vous pouvez utiliser les fonctionnalités XAML 2009 avec `x:TypeArguments`, mais uniquement pour le XAML libre (XAML qui n’est pas compilé par balisage).</span><span class="sxs-lookup"><span data-stu-id="779d2-140">In WPF and when targeting .NET Framework 4, you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="779d2-141">Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="779d2-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="779d2-142">Si vous devez compiler le code XAML, vous devez utiliser les restrictions indiquées dans la section « XAML 2006 et les utilisations XAML génériques WPF ».</span><span class="sxs-lookup"><span data-stu-id="779d2-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779d2-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="779d2-143">See also</span></span>

- [<span data-ttu-id="779d2-144">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="779d2-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="779d2-145">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="779d2-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="779d2-146">Types intégrés pour les primitives associées au langage XAML courant</span><span class="sxs-lookup"><span data-stu-id="779d2-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="779d2-147">Génériques en XAML</span><span class="sxs-lookup"><span data-stu-id="779d2-147">Generics in XAML</span></span>](generics-in-xaml.md)
