---
title: x:FactoryMethod, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071534"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="e6894-102">x:FactoryMethod, directive</span><span class="sxs-lookup"><span data-stu-id="e6894-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="e6894-103">Specifie une méthode autre qu’un constructeur qu’un processeur XAML devrait utiliser pour initialiser un objet après avoir résolu son type de support.</span><span class="sxs-lookup"><span data-stu-id="e6894-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="e6894-104">XAML Attribute Utilisation, no x:Arguments XAML Attribute Utilisation, no x:Arguments XAML Attribute Utilisation, no x:Arguments XAM</span><span class="sxs-lookup"><span data-stu-id="e6894-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="e6894-105">XAML Attribute Usage, x:Arguments as Element(s)</span><span class="sxs-lookup"><span data-stu-id="e6894-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e6894-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="e6894-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="e6894-107">Le nom de méthode de chaîne d’une méthode que les `object`processeurs XAML appellent pour initialiser l’instance spécifiée comme .</span><span class="sxs-lookup"><span data-stu-id="e6894-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="e6894-108">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="e6894-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="e6894-109">Un ou plusieurs éléments d’objets pour les objets qui spécifient les paramètres de la méthode d’usine.</span><span class="sxs-lookup"><span data-stu-id="e6894-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="e6894-110">L’ordre est important; il signifie l’ordre dans lequel les arguments doivent être transmis à la méthode de l’usine.</span><span class="sxs-lookup"><span data-stu-id="e6894-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6894-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e6894-111">Remarks</span></span>  
 <span data-ttu-id="e6894-112">S’il `methodname` s’agit d’une méthode d’instance, elle ne peut pas être qualifiée.</span><span class="sxs-lookup"><span data-stu-id="e6894-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="e6894-113">Les méthodes statiques en tant que méthodes d’usine sont soutenues.</span><span class="sxs-lookup"><span data-stu-id="e6894-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="e6894-114">Si `methodname` est une `methodname` méthode statique, `typeName.methodName` est `typeName` fourni comme une combinaison, où les noms de la classe qui définit la méthode d’usine statique.</span><span class="sxs-lookup"><span data-stu-id="e6894-114">If `methodname` is a static method, `methodname` is provided as a `typeName.methodName` combination, where `typeName` names the class that defines the static factory method.</span></span> <span data-ttu-id="e6894-115">`typeName`peut être préfixe-qualifié si se référant à un type dans un xmlns cartographié.</span><span class="sxs-lookup"><span data-stu-id="e6894-115">`typeName` can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="e6894-116">`typeName`peut être un `typeof(object)`type différent de .</span><span class="sxs-lookup"><span data-stu-id="e6894-116">`typeName` can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="e6894-117">La méthode de l’usine doit être une méthode publique déclarée du type qui soutient l’élément objet pertinent.</span><span class="sxs-lookup"><span data-stu-id="e6894-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="e6894-118">La méthode de l’usine doit renvoyer une instance qui est assignable à l’objet pertinent.</span><span class="sxs-lookup"><span data-stu-id="e6894-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="e6894-119">Les méthodes d’usine ne doivent jamais revenir nulles.</span><span class="sxs-lookup"><span data-stu-id="e6894-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="e6894-120">`x:Arguments`fonctionne selon le principe du meilleur assortiment pour les signatures de méthodes d’usine.</span><span class="sxs-lookup"><span data-stu-id="e6894-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="e6894-121">L’appariement évalue d’abord le nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="e6894-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="e6894-122">S’il y a plus d’une correspondance possible pour un nombre de paramètres, le type de paramètre est alors évalué et le meilleur match est déterminé.</span><span class="sxs-lookup"><span data-stu-id="e6894-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="e6894-123">S’il y a encore de l’ambiguïté après cette phase d’évaluation, le comportement du processeur XAML n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="e6894-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="e6894-124">L’utilisation `x:FactoryMethod` de l’élément n’est pas l’utilisation de l’élément de propriété au sens typique du terme, car le balisage de la directive ne fait pas référence au type d’élément objet contenant.</span><span class="sxs-lookup"><span data-stu-id="e6894-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="e6894-125">On s’attend à ce que l’utilisation des éléments soit moins courante que l’utilisation d’attributs.</span><span class="sxs-lookup"><span data-stu-id="e6894-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="e6894-126">`x:Arguments`(l’utilisation d’attribut ou d’élément) peut être utilisée avec `x:FactoryMethod` l’utilisation d’éléments, mais cela n’est pas spécifiquement indiqué dans les sections d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="e6894-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="e6894-127">`x:FactoryMethod`en tant qu’élément doit précéder `x:Arguments` tout autre élément de propriété, doit précéder tout élément également fourni comme éléments, et doit précéder tout contenu/texte intérieur/texte d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="e6894-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6894-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6894-128">See also</span></span>

- [<span data-ttu-id="e6894-129">x:Arguments, directive</span><span class="sxs-lookup"><span data-stu-id="e6894-129">x:Arguments Directive</span></span>](xarguments-directive.md)
