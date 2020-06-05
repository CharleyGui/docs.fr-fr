---
title: Types de données composites
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394296"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="5f497-102">Types de données composites (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f497-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="5f497-103">En plus des types de données élémentaires fournis par Visual Basic, vous pouvez également assembler des éléments de types différents pour créer des *types de données composites* , tels que des structures, des tableaux et des classes.</span><span class="sxs-lookup"><span data-stu-id="5f497-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="5f497-104">Vous pouvez générer des types de données composites à partir de types élémentaires et d’autres types composites.</span><span class="sxs-lookup"><span data-stu-id="5f497-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="5f497-105">Par exemple, vous pouvez définir un tableau d’éléments de structure ou une structure avec des membres de tableau.</span><span class="sxs-lookup"><span data-stu-id="5f497-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="5f497-106">Types de données</span><span class="sxs-lookup"><span data-stu-id="5f497-106">Data Types</span></span>  
 <span data-ttu-id="5f497-107">Un type composite est différent du type de données de l’un de ses composants.</span><span class="sxs-lookup"><span data-stu-id="5f497-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="5f497-108">Par exemple, un tableau d' `Integer` éléments n’est pas du `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="5f497-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="5f497-109">Un type de données de tableau est normalement représenté à l’aide du type d’élément, des parenthèses et des virgules, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5f497-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="5f497-110">Par exemple, un tableau unidimensionnel d' `String` éléments est représenté sous `String()` la forme et un tableau à deux dimensions d' `Boolean` éléments est représenté sous la forme `Boolean(,)` .</span><span class="sxs-lookup"><span data-stu-id="5f497-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="5f497-111">Types de structures</span><span class="sxs-lookup"><span data-stu-id="5f497-111">Structure Types</span></span>  
 <span data-ttu-id="5f497-112">Il n’existe pas de type de données unique comprenant toutes les structures.</span><span class="sxs-lookup"><span data-stu-id="5f497-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="5f497-113">Au lieu de cela, chaque définition d’une structure représente un type de données unique, même si deux structures définissent des éléments identiques dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="5f497-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="5f497-114">Toutefois, si vous créez deux instances ou plus de la même structure, Visual Basic les considère comme étant du même type de données.</span><span class="sxs-lookup"><span data-stu-id="5f497-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="5f497-115">Tuples</span><span class="sxs-lookup"><span data-stu-id="5f497-115">Tuples</span></span>

<span data-ttu-id="5f497-116">Un tuple est une structure légère qui contient au moins deux champs dont les types sont prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="5f497-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="5f497-117">Les tuples sont pris en charge à partir de Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="5f497-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="5f497-118">Les tuples sont généralement utilisés pour retourner plusieurs valeurs à partir d’un seul appel de méthode sans avoir à passer d’arguments par référence ou à empaqueter les champs retournés dans une classe ou une structure plus lourde.</span><span class="sxs-lookup"><span data-stu-id="5f497-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="5f497-119">Pour plus d’informations sur les tuples, consultez la rubrique [tuples](tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="5f497-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="5f497-120">Types tableau</span><span class="sxs-lookup"><span data-stu-id="5f497-120">Array Types</span></span>  
 <span data-ttu-id="5f497-121">Il n’existe pas de type de données unique comprenant tous les tableaux.</span><span class="sxs-lookup"><span data-stu-id="5f497-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="5f497-122">Le type de données d’une instance particulière d’un tableau est déterminé par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5f497-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="5f497-123">Le fait qu’il s’agit d’un tableau</span><span class="sxs-lookup"><span data-stu-id="5f497-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="5f497-124">Rang (nombre de dimensions) du tableau</span><span class="sxs-lookup"><span data-stu-id="5f497-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="5f497-125">Type d’élément du tableau</span><span class="sxs-lookup"><span data-stu-id="5f497-125">The element type of the array</span></span>  
  
 <span data-ttu-id="5f497-126">En particulier, la longueur d’une dimension donnée ne fait pas partie du type de données de l’instance.</span><span class="sxs-lookup"><span data-stu-id="5f497-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="5f497-127">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="5f497-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="5f497-128">Dans l’exemple précédent, les variables `arrayA` de tableau et `arrayB` sont considérées comme ayant le même type de données, `Byte()` même si elles sont initialisées à des longueurs différentes.</span><span class="sxs-lookup"><span data-stu-id="5f497-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="5f497-129">`arrayB`Les variables et ne `arrayC` sont pas du même type, car leurs types d’éléments sont différents.</span><span class="sxs-lookup"><span data-stu-id="5f497-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="5f497-130">`arrayC`Les variables et ne `arrayD` sont pas du même type, car leurs rangs sont différents.</span><span class="sxs-lookup"><span data-stu-id="5f497-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="5f497-131">Les variables `arrayD` et `arrayE` ont le même type ( `Short(,)` ), car leurs rangs et leurs types d’éléments sont identiques, même si `arrayD` n’est pas encore initialisé.</span><span class="sxs-lookup"><span data-stu-id="5f497-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="5f497-132">Pour plus d’informations sur les tableaux, consultez [tableaux](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f497-132">For more information on arrays, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="5f497-133">Types de classes</span><span class="sxs-lookup"><span data-stu-id="5f497-133">Class Types</span></span>  
 <span data-ttu-id="5f497-134">Il n’existe pas de type de données unique comprenant toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="5f497-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="5f497-135">Même si une classe peut hériter d’une autre classe, chacun d’eux est un type de données distinct.</span><span class="sxs-lookup"><span data-stu-id="5f497-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="5f497-136">Plusieurs instances de la même classe sont du même type de données.</span><span class="sxs-lookup"><span data-stu-id="5f497-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="5f497-137">Si vous assignez une variable d’instance de classe à une autre, non seulement elles ont le même type de données, mais elles pointent vers la même instance de classe en mémoire.</span><span class="sxs-lookup"><span data-stu-id="5f497-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="5f497-138">Pour plus d’informations sur les classes, consultez [objets et classes](../objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f497-138">For more information on classes, see [Objects and Classes](../objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f497-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f497-139">See also</span></span>

- [<span data-ttu-id="5f497-140">Types de données</span><span class="sxs-lookup"><span data-stu-id="5f497-140">Data Types</span></span>](index.md)
- [<span data-ttu-id="5f497-141">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="5f497-141">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="5f497-142">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f497-142">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="5f497-143">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="5f497-143">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="5f497-144">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f497-144">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5f497-145">Structures</span><span class="sxs-lookup"><span data-stu-id="5f497-145">Structures</span></span>](structures.md)
- [<span data-ttu-id="5f497-146">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="5f497-146">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="5f497-147">Procédure : Stocker plusieurs valeurs dans une variable</span><span class="sxs-lookup"><span data-stu-id="5f497-147">How to: Hold More Than One Value in a Variable</span></span>](how-to-hold-more-than-one-value-in-a-variable.md)
