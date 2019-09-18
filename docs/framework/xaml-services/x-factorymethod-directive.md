---
title: x:FactoryMethod, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053774"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="97881-102">x:FactoryMethod, directive</span><span class="sxs-lookup"><span data-stu-id="97881-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="97881-103">Spécifie une méthode autre qu’un constructeur qu’un processeur XAML doit utiliser pour initialiser un objet après la résolution de son type de stockage.</span><span class="sxs-lookup"><span data-stu-id="97881-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="97881-104">Utilisation d’attributs XAML, no x :Arguments</span><span class="sxs-lookup"><span data-stu-id="97881-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="97881-105">Utilisation d’attribut XAML, x :Arguments en tant qu’élément (s)</span><span class="sxs-lookup"><span data-stu-id="97881-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="97881-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="97881-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="97881-107">Nom de méthode de chaîne d’une méthode que les processeurs XAML appellent pour initialiser l' `object`instance spécifiée comme.</span><span class="sxs-lookup"><span data-stu-id="97881-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="97881-108">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="97881-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="97881-109">Un ou plusieurs éléments objet pour les objets qui spécifient des paramètres de méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="97881-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="97881-110">L’ordre est important. Il indique l’ordre dans lequel les arguments doivent être passés à la méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="97881-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97881-111">Notes</span><span class="sxs-lookup"><span data-stu-id="97881-111">Remarks</span></span>  
 <span data-ttu-id="97881-112">Si `methodname` est une méthode d’instance, elle ne peut pas être qualifiée.</span><span class="sxs-lookup"><span data-stu-id="97881-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="97881-113">Les méthodes statiques en tant que méthodes de fabrique sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="97881-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="97881-114">Si `methodname` est une méthode statique, `methodname` est fourni en tant que *TypeName*. *combinaison methodName* , où *TypeName* nomme la classe qui définit la méthode de fabrique statique.</span><span class="sxs-lookup"><span data-stu-id="97881-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="97881-115">*TypeName* peut être qualifié par un préfixe s’il fait référence à un type dans un xmlns mappé.</span><span class="sxs-lookup"><span data-stu-id="97881-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="97881-116">*TypeName* peut être un type différent de `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="97881-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="97881-117">La méthode de fabrique doit être une méthode publique déclarée du type qui stocke l’élément objet approprié.</span><span class="sxs-lookup"><span data-stu-id="97881-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="97881-118">La méthode de fabrique doit retourner une instance qui peut être assignée à l’objet approprié.</span><span class="sxs-lookup"><span data-stu-id="97881-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="97881-119">Les méthodes de fabrique ne doivent jamais retourner la valeur null.</span><span class="sxs-lookup"><span data-stu-id="97881-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="97881-120">`x:Arguments`opère sur un principe de meilleure correspondance pour les signatures de méthodes de fabrique.</span><span class="sxs-lookup"><span data-stu-id="97881-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="97881-121">La correspondance évalue le nombre de paramètres en premier.</span><span class="sxs-lookup"><span data-stu-id="97881-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="97881-122">S’il existe plusieurs correspondances possibles pour un nombre de paramètres, le type de paramètre est évalué et la meilleure correspondance est déterminée.</span><span class="sxs-lookup"><span data-stu-id="97881-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="97881-123">S’il y a toujours une ambiguïté après cette phase d’évaluation, le comportement du processeur XAML n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="97881-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="97881-124">L' `x:FactoryMethod` utilisation de l’élément n’est pas une utilisation d’élément de propriété dans le sens normal, car le balisage de directive ne fait pas référence au type de l’élément objet conteneur.</span><span class="sxs-lookup"><span data-stu-id="97881-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="97881-125">Il est prévu que l’utilisation des éléments soit moins courante que l’utilisation des attributs.</span><span class="sxs-lookup"><span data-stu-id="97881-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="97881-126">`x:Arguments`(utilisation de l’attribut ou de l’élément) peut être `x:FactoryMethod` utilisé avec l’utilisation de l’élément, mais cela n’est pas spécifiquement indiqué dans les sections utilisation.</span><span class="sxs-lookup"><span data-stu-id="97881-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="97881-127">`x:FactoryMethod`comme un élément doit précéder tous les autres éléments de propriété, `x:Arguments` doit précéder tout également fourni comme éléments, et doit précéder tout contenu/texte interne/texte d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="97881-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97881-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97881-128">See also</span></span>

- [<span data-ttu-id="97881-129">x:Arguments (directive)</span><span class="sxs-lookup"><span data-stu-id="97881-129">x:Arguments Directive</span></span>](x-arguments-directive.md)
