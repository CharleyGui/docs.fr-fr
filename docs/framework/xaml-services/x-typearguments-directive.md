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
ms.openlocfilehash: 41f29673622fa7918238dd014b97ee3cf0766257
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486212"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="436f1-102">x:TypeArguments, directive</span><span class="sxs-lookup"><span data-stu-id="436f1-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="436f1-103">Passes contraindre les arguments d’un générique au constructeur du type générique de type.</span><span class="sxs-lookup"><span data-stu-id="436f1-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="436f1-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="436f1-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="436f1-105">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="436f1-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="436f1-106">Une déclaration d’élément objet d’un type XAML, qui repose sur un type générique du CLR.</span><span class="sxs-lookup"><span data-stu-id="436f1-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="436f1-107">Si `object` fait référence à un type XAML qui n’est pas à partir de l’espace de noms XAML par défaut, `object` nécessite un préfixe pour indiquer l’espace de noms XAML où `object` existe.</span><span class="sxs-lookup"><span data-stu-id="436f1-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="436f1-108">Chaîne qui déclare le XAML d’un ou plusieurs noms de type sous forme de chaînes, qui fournit les arguments de type pour le type générique du CLR.</span><span class="sxs-lookup"><span data-stu-id="436f1-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="436f1-109">Consultez la section Notes pour accéder aux notes de la syntaxe supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="436f1-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="436f1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="436f1-110">Remarks</span></span>  
 <span data-ttu-id="436f1-111">Dans la plupart des cas, les types XAML qui sont utilisés comme un élément d’information dans un `typeString` chaîne sont préfixés.</span><span class="sxs-lookup"><span data-stu-id="436f1-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="436f1-112">Les types classiques de contraintes génériques CLR (par exemple, <xref:System.Int32> et <xref:System.String>) proviennent de bibliothèques de classe de base CLR.</span><span class="sxs-lookup"><span data-stu-id="436f1-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="436f1-113">Ces bibliothèques ne sont pas des espaces de noms XAML mappé à un type valeur par défaut spécifiques à l’infrastructure et par conséquent, requièrent un mappage de préfixe pour l’utilisation XAML.</span><span class="sxs-lookup"><span data-stu-id="436f1-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="436f1-114">Vous pouvez spécifier plusieurs noms de type XAML à l’aide d’une virgule.</span><span class="sxs-lookup"><span data-stu-id="436f1-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="436f1-115">Si les contraintes génériques eux-mêmes utilisent des types génériques, les arguments de type de contrainte imbriqué peuvent être contenus par des parenthèses ().</span><span class="sxs-lookup"><span data-stu-id="436f1-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="436f1-116">Notez que cette définition de `x:TypeArguments` est spécifique aux Services de XAML .NET Framework et à l’aide de stockage CLR.</span><span class="sxs-lookup"><span data-stu-id="436f1-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="436f1-117">Vous trouverez une définition au niveau du langage dans [ \[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="436f1-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="436f1-118">Exemples d’utilisation</span><span class="sxs-lookup"><span data-stu-id="436f1-118">Usage Examples</span></span>  
 <span data-ttu-id="436f1-119">Pour ces exemples, supposons que les définitions d’espace de noms XAML suivantes sont déclarées :</span><span class="sxs-lookup"><span data-stu-id="436f1-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="436f1-120">Liste\<chaîne ></span><span class="sxs-lookup"><span data-stu-id="436f1-120">List\<String></span></span>  
 <span data-ttu-id="436f1-121">`<scg:List x:TypeArguments="sys:String" ...>` instancie un nouveau <xref:System.Collections.Generic.List%601> avec un <xref:System.String> argument de type.</span><span class="sxs-lookup"><span data-stu-id="436f1-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="436f1-122">Dictionnaire\<String, String ></span><span class="sxs-lookup"><span data-stu-id="436f1-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="436f1-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instancie un nouveau <xref:System.Collections.Generic.Dictionary%602> avec deux <xref:System.String> arguments de type.</span><span class="sxs-lookup"><span data-stu-id="436f1-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="436f1-124">File d’attente < KeyValuePair\<String, String >></span><span class="sxs-lookup"><span data-stu-id="436f1-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="436f1-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instancie un nouveau <xref:System.Collections.Generic.Queue%601> qui a une contrainte de <xref:System.Collections.Generic.KeyValuePair%602> avec les arguments de type de contrainte interne <xref:System.String> et <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="436f1-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="436f1-126">Utilisations XAML générique de XAML 2006 et WPF</span><span class="sxs-lookup"><span data-stu-id="436f1-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="436f1-127">Pour l’utilisation de XAML 2006 et XAML qui est utilisé pour les applications WPF, les restrictions suivantes existent pour `x:TypeArguments` et utilisations de type générique à partir de XAML en général :</span><span class="sxs-lookup"><span data-stu-id="436f1-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
- <span data-ttu-id="436f1-128">Seul l’élément racine d’un fichier XAML peut prendre en charge une utilisation XAML générique qui fait référence à un type générique.</span><span class="sxs-lookup"><span data-stu-id="436f1-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
- <span data-ttu-id="436f1-129">L’élément racine doit mapper à un type générique au moins un argument de type.</span><span class="sxs-lookup"><span data-stu-id="436f1-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="436f1-130">Par exemple, <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="436f1-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="436f1-131">Les fonctions de page sont le scénario principal pour la prise en charge des génériques de l’utilisation XAML dans WPF.</span><span class="sxs-lookup"><span data-stu-id="436f1-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
- <span data-ttu-id="436f1-132">L’élément d’objet racine élément XAML pour le modèle générique doit également déclarer une classe partielle à l’aide `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="436f1-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="436f1-133">Cela est vrai même si l’action de génération de définition d’un WPF.</span><span class="sxs-lookup"><span data-stu-id="436f1-133">This is true even if defining a WPF build action.</span></span>  
  
- <span data-ttu-id="436f1-134">`x:TypeArguments` Impossible de référencer les contraintes génériques imbriqués.</span><span class="sxs-lookup"><span data-stu-id="436f1-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="436f1-135">XAML 2009 ou 2006 XAML sans WPF 3.0 ni les WPF 3.5 dépendance</span><span class="sxs-lookup"><span data-stu-id="436f1-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="436f1-136">Dans les Services XAML .NET Framework pour XAML 2006 ou XAML 2009, les restrictions liées à WPF sur l’utilisation XAML générique sont assouplies.</span><span class="sxs-lookup"><span data-stu-id="436f1-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="436f1-137">Vous pouvez instancier un élément objet générique à n’importe quelle position dans le balisage XAML prenant en charge la sauvegarde type système et le modèle objet.</span><span class="sxs-lookup"><span data-stu-id="436f1-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="436f1-138">Si vous utilisez XAML 2009 au lieu de mapper le CLR des types pour obtenir les types XAML pour les primitives de langage courantes de base, vous pouvez utiliser [des Types intégrés pour les Primitives de langage XAML courantes](built-in-types-for-common-xaml-language-primitives.md) en tant qu’éléments d’informations dans un `typeString`.</span><span class="sxs-lookup"><span data-stu-id="436f1-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="436f1-139">Par exemple, vous pouvez déclarer les éléments suivants (les mappages de préfixe ne pas affichés, mais x est l’espace de noms XAML de langage XAML pour XAML 2009) :</span><span class="sxs-lookup"><span data-stu-id="436f1-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="436f1-140">Dans WPF et lorsque vous ciblez .NET Framework 4, vous pouvez utiliser les fonctionnalités XAML 2009 avec `x:TypeArguments` mais uniquement pour XAML libre (XAML non compilé par balisage).</span><span class="sxs-lookup"><span data-stu-id="436f1-140">In WPF and when targeting .NET Framework 4, you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="436f1-141">Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="436f1-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="436f1-142">Si vous avez besoin de compiler le XAML par balisage, vous devez fonctionner selon les restrictions notées dans la section « XAML 2006 et WPF XAML utilisations générique ».</span><span class="sxs-lookup"><span data-stu-id="436f1-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436f1-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="436f1-143">See also</span></span>

- [<span data-ttu-id="436f1-144">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="436f1-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="436f1-145">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="436f1-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="436f1-146">Types intégrés pour les primitives associées au langage XAML courant</span><span class="sxs-lookup"><span data-stu-id="436f1-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="436f1-147">Génériques en XAML</span><span class="sxs-lookup"><span data-stu-id="436f1-147">Generics in XAML</span></span>](generics-in-xaml.md)
