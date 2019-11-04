---
title: x:Arguments, directive
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458654"
---
# <a name="xarguments-directive"></a><span data-ttu-id="d0db3-102">x:Arguments, directive</span><span class="sxs-lookup"><span data-stu-id="d0db3-102">x:Arguments Directive</span></span>
<span data-ttu-id="d0db3-103">Les arguments de construction de packages pour une déclaration d’élément objet de constructeur sans paramètre en XAML, ou pour une déclaration d’objet de méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="d0db3-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="d0db3-104">Utilisation des éléments XAML (constructeur sans paramètre)</span><span class="sxs-lookup"><span data-stu-id="d0db3-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="d0db3-105">Utilisation des éléments XAML (méthode de fabrique)</span><span class="sxs-lookup"><span data-stu-id="d0db3-105">XAML Element Usage (factory method)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d0db3-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="d0db3-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="d0db3-107">Un ou plusieurs éléments objet qui spécifient des arguments à passer au constructeur sans paramètre de sauvegarde ou à la méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="d0db3-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="d0db3-108">L’utilisation classique consiste à utiliser le texte d’initialisation dans les éléments de l’objet pour spécifier les valeurs d’arguments réelles.</span><span class="sxs-lookup"><span data-stu-id="d0db3-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="d0db3-109">Consultez la section exemples.</span><span class="sxs-lookup"><span data-stu-id="d0db3-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="d0db3-110">L’ordre des éléments est significatif.</span><span class="sxs-lookup"><span data-stu-id="d0db3-110">The order of the elements is significant.</span></span> <span data-ttu-id="d0db3-111">Les types XAML dans l’ordre doivent correspondre aux types et à l’ordre de type du constructeur de stockage ou de la surcharge de méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="d0db3-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="d0db3-112">Nom de la méthode de fabrique qui doit traiter tout `x:Arguments` arguments.</span><span class="sxs-lookup"><span data-stu-id="d0db3-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="d0db3-113">Dépendances</span><span class="sxs-lookup"><span data-stu-id="d0db3-113">Dependencies</span></span>  
 <span data-ttu-id="d0db3-114">`x:FactoryMethod` pouvez modifier l’étendue et le comportement dans lesquels `x:Arguments` s’applique.</span><span class="sxs-lookup"><span data-stu-id="d0db3-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="d0db3-115">Si aucun `x:FactoryMethod` n’est spécifié, `x:Arguments` s’applique aux signatures de remplacement (non par défaut) des constructeurs de stockage.</span><span class="sxs-lookup"><span data-stu-id="d0db3-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="d0db3-116">Si `x:FactoryMethod` est spécifié, `x:Arguments` s’applique à une surcharge de la méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="d0db3-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0db3-117">Notes</span><span class="sxs-lookup"><span data-stu-id="d0db3-117">Remarks</span></span>  
 <span data-ttu-id="d0db3-118">XAML 2006 peut prendre en charge l’initialisation non définie par défaut par le texte d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="d0db3-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="d0db3-119">Toutefois, l’application pratique d’une technique de construction de texte d’initialisation est limitée.</span><span class="sxs-lookup"><span data-stu-id="d0db3-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="d0db3-120">Le texte d’initialisation est traité comme une chaîne de texte unique. par conséquent, il ajoute uniquement des fonctionnalités pour l’initialisation d’un seul paramètre, sauf si un convertisseur de type est défini pour le comportement de construction qui peut analyser des éléments d’information personnalisés et des délimiteurs personnalisés de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d0db3-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="d0db3-121">En outre, la chaîne de texte à la logique d’objet est potentiellement un convertisseur de type natif par défaut de l’analyseur XAML donné pour gérer les primitives autres que la chaîne true.</span><span class="sxs-lookup"><span data-stu-id="d0db3-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="d0db3-122">L’utilisation de XAML `x:Arguments` n’est pas une utilisation d’élément de propriété dans le sens type, car le balisage de directive ne fait pas référence au type de l’élément objet conteneur.</span><span class="sxs-lookup"><span data-stu-id="d0db3-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="d0db3-123">Elle est plus similaire à d’autres directives telles que `x:Code` où l’élément délimite une plage dans laquelle le balisage doit être interprété comme autre que celui par défaut pour le contenu enfant.</span><span class="sxs-lookup"><span data-stu-id="d0db3-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="d0db3-124">Dans ce cas, le type XAML de chaque élément Object communique des informations sur les types d’arguments, qui sont utilisés par les analyseurs XAML pour déterminer la signature de méthode de fabrique de constructeur spécifique qu’une utilisation de `x:Arguments` tente de référencer.</span><span class="sxs-lookup"><span data-stu-id="d0db3-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="d0db3-125">`x:Arguments` pour un élément objet en cours de construction doit précéder tout autre élément de propriété, contenu, texte interne ou chaîne d’initialisation de l’élément objet.</span><span class="sxs-lookup"><span data-stu-id="d0db3-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="d0db3-126">Les éléments objet dans `x:Arguments` peuvent inclure des attributs et des chaînes d’initialisation, comme l’autorise ce type XAML et son constructeur de stockage ou sa méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="d0db3-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="d0db3-127">Pour l’objet ou les arguments, vous pouvez spécifier des types XAML personnalisés ou des types XAML qui sont autrement en dehors de l’espace de noms XAML par défaut en référençant les mappages de préfixe établis.</span><span class="sxs-lookup"><span data-stu-id="d0db3-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="d0db3-128">Les processeurs XAML utilisent les indications suivantes pour déterminer comment les arguments spécifiés dans `x:Arguments` doivent être utilisés pour construire un objet.</span><span class="sxs-lookup"><span data-stu-id="d0db3-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="d0db3-129">Si `x:FactoryMethod` est spécifié, les informations sont comparées à la `x:FactoryMethod` spécifiée (Notez que la valeur de `x:FactoryMethod` est le nom de la méthode et que la méthode nommée peut avoir des surcharges.</span><span class="sxs-lookup"><span data-stu-id="d0db3-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="d0db3-130">Si `x:FactoryMethod` n’est pas spécifié, les informations sont comparées à l’ensemble de toutes les surcharges de constructeur public de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d0db3-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="d0db3-131">La logique de traitement XAML compare ensuite le nombre de paramètres et sélectionne la surcharge avec l’arité correspondante.</span><span class="sxs-lookup"><span data-stu-id="d0db3-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="d0db3-132">S’il existe plusieurs correspondances, le processeur XAML doit comparer les types des paramètres en fonction des types XAML des éléments objet fournis.</span><span class="sxs-lookup"><span data-stu-id="d0db3-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="d0db3-133">S’il existe encore plusieurs correspondances, le comportement du processeur XAML n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="d0db3-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="d0db3-134">Si une `x:FactoryMethod` est spécifiée mais que la méthode ne peut pas être résolue, un processeur XAML doit lever une exception.</span><span class="sxs-lookup"><span data-stu-id="d0db3-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="d0db3-135">Un `<x:Arguments>string</x:Arguments>` d’utilisation d’attribut XAML est techniquement possible.</span><span class="sxs-lookup"><span data-stu-id="d0db3-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="d0db3-136">Toutefois, cela ne fournit pas de fonctionnalités au-delà de ce qui pourrait être fait autrement par le biais d’un texte d’initialisation et de convertisseurs de type, et l’utilisation de cette syntaxe n’est pas l’intention de conception des fonctionnalités de la méthode de fabrique XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="d0db3-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d0db3-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="d0db3-137">Examples</span></span>  
 <span data-ttu-id="d0db3-138">L’exemple suivant montre une signature de constructeur sans paramètre, puis l’utilisation de XAML de `x:Arguments` qui accède à cette signature.</span><span class="sxs-lookup"><span data-stu-id="d0db3-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 <span data-ttu-id="d0db3-139">L’exemple suivant illustre une signature de méthode de fabrique cible, puis l’utilisation XAML de `x:Arguments` qui accède à cette signature.</span><span class="sxs-lookup"><span data-stu-id="d0db3-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0db3-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0db3-140">See also</span></span>

- [<span data-ttu-id="d0db3-141">Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0db3-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="d0db3-142">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d0db3-142">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
