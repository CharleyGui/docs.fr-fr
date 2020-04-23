---
title: x:Arguments, directive
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071590"
---
# <a name="xarguments-directive"></a><span data-ttu-id="fe314-102">x:Arguments, directive</span><span class="sxs-lookup"><span data-stu-id="fe314-102">x:Arguments Directive</span></span>

<span data-ttu-id="fe314-103">Arguments de construction de paquets pour une déclaration d’élément constructeur non-paramètre dans XAML, ou pour une déclaration d’objet de méthode d’usine.</span><span class="sxs-lookup"><span data-stu-id="fe314-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>

## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="fe314-104">Utilisation d’éléments XAML (constructeur non nonparameterless)</span><span class="sxs-lookup"><span data-stu-id="fe314-104">XAML Element Usage (Nonparameterless constructor)</span></span>

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="fe314-105">Utilisation d’éléments XAML (méthode d’usine)</span><span class="sxs-lookup"><span data-stu-id="fe314-105">XAML Element Usage (factory method)</span></span>

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="fe314-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="fe314-106">XAML Values</span></span>

|||
|-|-|
|`oneOrMoreObjectElements`|<span data-ttu-id="fe314-107">Un ou plusieurs éléments d’objet qui spécifient des arguments à transmettre au constructeur ou à la méthode d’usine sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="fe314-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="fe314-108">L’utilisation typique consiste à utiliser le texte de initialisation dans les éléments de l’objet pour spécifier les valeurs réelles de l’argument.</span><span class="sxs-lookup"><span data-stu-id="fe314-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="fe314-109">Voir la section Exemples.</span><span class="sxs-lookup"><span data-stu-id="fe314-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="fe314-110">L’ordre des éléments est significatif.</span><span class="sxs-lookup"><span data-stu-id="fe314-110">The order of the elements is significant.</span></span> <span data-ttu-id="fe314-111">Les types XAML afin de correspondre aux types et à l’ordre de type du constructeur de support ou de la surcharge de méthode d’usine.</span><span class="sxs-lookup"><span data-stu-id="fe314-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|
|`methodName`|<span data-ttu-id="fe314-112">Le nom de la méthode `x:Arguments` de l’usine qui doit traiter tous les arguments.</span><span class="sxs-lookup"><span data-stu-id="fe314-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="fe314-113">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="fe314-113">Dependencies</span></span>

<span data-ttu-id="fe314-114">`x:FactoryMethod`peut modifier la portée `x:Arguments` et le comportement lorsque cela s’applique.</span><span class="sxs-lookup"><span data-stu-id="fe314-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>

<span data-ttu-id="fe314-115">Si `x:FactoryMethod` aucun n’est spécifié, `x:Arguments` s’applique aux signatures alternatives (non-par défaut) des constructeurs de support.</span><span class="sxs-lookup"><span data-stu-id="fe314-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>

<span data-ttu-id="fe314-116">Si `x:FactoryMethod` elle `x:Arguments` est spécifiée, s’applique à une surcharge de la méthode nommée.</span><span class="sxs-lookup"><span data-stu-id="fe314-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe314-117">Notes</span><span class="sxs-lookup"><span data-stu-id="fe314-117">Remarks</span></span>

<span data-ttu-id="fe314-118">XAML 2006 peut prendre en charge l’initialisation par défaut par le biais du texte de initialisation.</span><span class="sxs-lookup"><span data-stu-id="fe314-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="fe314-119">Cependant, l’application pratique d’une technique de construction de texte d’initialisation est limitée.</span><span class="sxs-lookup"><span data-stu-id="fe314-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="fe314-120">Le texte de initialisation est traité comme une seule chaîne de texte; par conséquent, il ajoute seulement la capacité pour une initialisation de paramètres unique à moins qu’un convertisseur de type soit défini pour le comportement de construction qui peut analyser des éléments d’information personnalisés et des délimitations personnalisées de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="fe314-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="fe314-121">En outre, la chaîne de texte à la logique d’objet est potentiellement un convertisseur de type par défaut natif d’un par défaut de XAML pour manipuler des primitifs autres qu’une vraie chaîne.</span><span class="sxs-lookup"><span data-stu-id="fe314-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>

<span data-ttu-id="fe314-122">L’utilisation `x:Arguments` de XAML n’est pas l’utilisation de l’élément de propriété dans le sens typique, parce que le balisage de la directive ne fait pas référence au type de l’élément objet contenant.</span><span class="sxs-lookup"><span data-stu-id="fe314-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="fe314-123">Il s’apparente davantage à `x:Code` d’autres directives telles que l’endroit où l’élément marque une plage dans laquelle la majoration doit être interprétée comme autre que la valeur par défaut pour le contenu de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="fe314-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="fe314-124">Dans ce cas, le type XAML de chaque élément d’objet communique des informations sur les types d’argument, `x:Arguments` qui est utilisé par les analyseurs XAML pour déterminer quelle signature spécifique de méthode d’usine de constructeur une utilisation tente de référence.</span><span class="sxs-lookup"><span data-stu-id="fe314-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>

<span data-ttu-id="fe314-125">`x:Arguments`pour un élément d’objet en construction doit précéder tout autre élément de propriété, contenu, texte intérieur ou chaînes d’initialisation de l’élément objet.</span><span class="sxs-lookup"><span data-stu-id="fe314-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="fe314-126">Les éléments `x:Arguments` d’objet à l’intérieur peuvent inclure des attributs et des chaînes d’initialisation, comme le permet ce type XAML et sa méthode de construction ou d’usine.</span><span class="sxs-lookup"><span data-stu-id="fe314-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="fe314-127">Pour l’objet ou les arguments, vous pouvez spécifier les types XAML personnalisés ou les types XAML qui sont autrement en dehors de l’espace nom XAML par défaut en faisant référence aux cartes préfixes établies.</span><span class="sxs-lookup"><span data-stu-id="fe314-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>

<span data-ttu-id="fe314-128">Les processeurs XAML utilisent les lignes directrices suivantes pour déterminer comment les arguments spécifiés `x:Arguments` devraient être utilisés pour construire un objet.</span><span class="sxs-lookup"><span data-stu-id="fe314-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="fe314-129">Si `x:FactoryMethod` elle est spécifiée, `x:FactoryMethod` l’information est `x:FactoryMethod` comparée à la spécifiée (notez que la valeur est le nom de la méthode, et la méthode nommée peut avoir des surcharges.</span><span class="sxs-lookup"><span data-stu-id="fe314-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="fe314-130">Si `x:FactoryMethod` elle n’est pas spécifiée, l’information est comparée à l’ensemble de toutes les surcharges constructoraires publiques de l’objet.</span><span class="sxs-lookup"><span data-stu-id="fe314-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="fe314-131">La logique de traitement XAML compare ensuite le nombre de paramètres et sélectionne la surcharge avec une aité assortie.</span><span class="sxs-lookup"><span data-stu-id="fe314-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="fe314-132">S’il y a plus d’une correspondance, le processeur XAML doit comparer les types de paramètres en fonction des types XAML des éléments d’objets fournis.</span><span class="sxs-lookup"><span data-stu-id="fe314-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="fe314-133">S’il y a encore plus d’un match, le comportement du processeur XAML n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="fe314-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="fe314-134">Si `x:FactoryMethod` un a est spécifié mais que la méthode ne peut pas être résolue, un processeur XAML doit faire une exception.</span><span class="sxs-lookup"><span data-stu-id="fe314-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>

<span data-ttu-id="fe314-135">Une utilisation d’attribut `<x:Arguments>string</x:Arguments>` XAML est techniquement possible.</span><span class="sxs-lookup"><span data-stu-id="fe314-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="fe314-136">Cependant, cela ne fournit aucune capacité au-delà de ce qui pourrait être fait autrement par le biais de la initialisation texte et convertisseurs de type, et l’utilisation de cette syntaxe n’est pas l’intention de conception de la XAML 2009 caractéristiques de la méthode d’usine.</span><span class="sxs-lookup"><span data-stu-id="fe314-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>

## <a name="examples"></a><span data-ttu-id="fe314-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="fe314-137">Examples</span></span>

<span data-ttu-id="fe314-138">L’exemple suivant montre une signature constructeur non sans paramètres, `x:Arguments` puis l’utilisation XAML de celui accès à cette signature.</span><span class="sxs-lookup"><span data-stu-id="fe314-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

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

<span data-ttu-id="fe314-139">L’exemple suivant montre une signature de méthode d’usine cible, puis l’utilisation XAML de `x:Arguments` celui accès à cette signature.</span><span class="sxs-lookup"><span data-stu-id="fe314-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fe314-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe314-140">See also</span></span>

- [<span data-ttu-id="fe314-141">Définition de types personnalisés pour les utiliser avec les services XAML .NET</span><span class="sxs-lookup"><span data-stu-id="fe314-141">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
- [<span data-ttu-id="fe314-142">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="fe314-142">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
