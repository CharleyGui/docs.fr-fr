---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396205"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="2c1f6-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c1f6-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="2c1f6-103">Spécifie qu’une classe peut être utilisée uniquement comme classe de base et que vous ne pouvez pas créer un objet directement à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c1f6-104">Notes</span><span class="sxs-lookup"><span data-stu-id="2c1f6-104">Remarks</span></span>  
 <span data-ttu-id="2c1f6-105">L’objectif d’une *classe de base* (également appelée *classe abstraite*) est de définir des fonctionnalités communes à toutes les classes qui en sont dérivées.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="2c1f6-106">Cela évite aux classes dérivées d’avoir à redéfinir les éléments communs.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="2c1f6-107">Dans certains cas, cette fonctionnalité commune n’est pas assez complète pour créer un objet utilisable, et chaque classe dérivée définit les fonctionnalités manquantes.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="2c1f6-108">Dans ce cas, vous souhaitez que le code de consommation crée uniquement des objets à partir des classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="2c1f6-109">Vous utilisez `MustInherit` sur la classe de base pour appliquer cette.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="2c1f6-110">Une autre utilisation d’une `MustInherit` classe consiste à limiter une variable à un ensemble de classes connexes.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="2c1f6-111">Vous pouvez définir une classe de base et dériver toutes ces classes associées à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="2c1f6-112">La classe de base n’a pas besoin de fournir des fonctionnalités communes à toutes les classes dérivées, mais elle peut servir de filtre pour assigner des valeurs à des variables.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="2c1f6-113">Si votre code de consommation déclare une variable comme classe de base, Visual Basic vous permet d’assigner uniquement un objet à partir de l’une des classes dérivées de cette variable.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="2c1f6-114">Le .NET Framework définit plusieurs `MustInherit` classes, parmi celles-ci <xref:System.Array> , <xref:System.Enum> et <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="2c1f6-115"><xref:System.ValueType>est un exemple de classe de base qui restreint une variable.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="2c1f6-116">Tous les types valeur dérivent de <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="2c1f6-117">Si vous déclarez une variable en tant que <xref:System.ValueType> , vous pouvez assigner uniquement des types valeur à cette variable.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2c1f6-118">Règles</span><span class="sxs-lookup"><span data-stu-id="2c1f6-118">Rules</span></span>  
  
- <span data-ttu-id="2c1f6-119">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="2c1f6-119">**Declaration Context.**</span></span> <span data-ttu-id="2c1f6-120">Vous pouvez utiliser `MustInherit` uniquement dans une `Class` instruction.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="2c1f6-121">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="2c1f6-121">**Combined Modifiers.**</span></span> <span data-ttu-id="2c1f6-122">Vous ne pouvez pas spécifier `MustInherit` avec `NotInheritable` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c1f6-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="2c1f6-123">Example</span></span>  
 <span data-ttu-id="2c1f6-124">L’exemple suivant illustre l’héritage forcé et le remplacement forcé.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="2c1f6-125">La classe `shape` de base définit une variable `acrossLine` .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="2c1f6-126">Les classes `circle` et `square` dérivent de `shape` .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="2c1f6-127">Ils héritent de la définition de `acrossLine` , mais ils doivent définir la fonction, `area` car ce calcul est différent pour chaque type de forme.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2c1f6-128">Vous pouvez déclarer `shape1` et `shape2` être de type `shape` .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="2c1f6-129">Toutefois, vous ne pouvez pas créer un objet à partir de `shape` , car il ne possède pas les fonctionnalités de la fonction `area` et est marqué `MustInherit` .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="2c1f6-130">Étant donné qu’ils sont déclarés comme `shape` , les variables `shape1` et `shape2` sont limitées aux objets des classes dérivées `circle` et `square` .</span><span class="sxs-lookup"><span data-stu-id="2c1f6-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="2c1f6-131">Visual Basic ne vous permet pas d’assigner un autre objet à ces variables, ce qui vous donne un niveau élevé de sécurité de type.</span><span class="sxs-lookup"><span data-stu-id="2c1f6-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="2c1f6-132">Utilisation</span><span class="sxs-lookup"><span data-stu-id="2c1f6-132">Usage</span></span>  
 <span data-ttu-id="2c1f6-133">Le `MustInherit` modificateur peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="2c1f6-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="2c1f6-134">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="2c1f6-134">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c1f6-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c1f6-135">See also</span></span>

- [<span data-ttu-id="2c1f6-136">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="2c1f6-136">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="2c1f6-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="2c1f6-137">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="2c1f6-138">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2c1f6-138">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="2c1f6-139">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="2c1f6-139">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
