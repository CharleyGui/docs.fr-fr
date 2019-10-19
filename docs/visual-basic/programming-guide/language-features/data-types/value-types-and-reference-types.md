---
title: Types valeur et types référence
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582643"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="288ad-102">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="288ad-102">Value Types and Reference Types</span></span>
<span data-ttu-id="288ad-103">Il existe deux genres de types dans Visual Basic : les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="288ad-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="288ad-104">Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données.</span><span class="sxs-lookup"><span data-stu-id="288ad-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="288ad-105">Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="288ad-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="288ad-106">Avec les types valeur, chaque variable possède sa propre copie des données, et il n’est pas possible pour les opérations sur une variable d’affecter l’autre (sauf dans le cas du [modificateur ByRef sur les paramètres](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="288ad-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="288ad-107">Types valeur</span><span class="sxs-lookup"><span data-stu-id="288ad-107">Value Types</span></span>  
 <span data-ttu-id="288ad-108">Un type de données est un *type valeur* s’il contient les données dans sa propre allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="288ad-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="288ad-109">Les types valeur sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="288ad-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="288ad-110">Tous les types de données numériques</span><span class="sxs-lookup"><span data-stu-id="288ad-110">All numeric data types</span></span>  
  
- <span data-ttu-id="288ad-111">`Boolean`, `Char`et `Date`</span><span class="sxs-lookup"><span data-stu-id="288ad-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="288ad-112">Toutes les structures, même si leurs membres sont des types référence</span><span class="sxs-lookup"><span data-stu-id="288ad-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="288ad-113">Les énumérations, puisque leur type sous-jacent est toujours `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` ou `ULong`</span><span class="sxs-lookup"><span data-stu-id="288ad-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="288ad-114">Chaque structure est un type valeur, même s’il contient des membres de type référence.</span><span class="sxs-lookup"><span data-stu-id="288ad-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="288ad-115">Pour cette raison, les types de valeur tels que `Char` et `Integer` sont implémentés par les structures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="288ad-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="288ad-116">Vous pouvez déclarer un type valeur à l’aide du mot clé réservé, par exemple, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="288ad-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="288ad-117">Vous pouvez également utiliser le mot clé `New` pour initialiser un type valeur.</span><span class="sxs-lookup"><span data-stu-id="288ad-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="288ad-118">Cela s’avère particulièrement utile si le type a un constructeur qui accepte des paramètres.</span><span class="sxs-lookup"><span data-stu-id="288ad-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="288ad-119">Par exemple, le constructeur <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, qui génère une nouvelle valeur `Decimal` à partir des parties fournies.</span><span class="sxs-lookup"><span data-stu-id="288ad-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="288ad-120">Types référence</span><span class="sxs-lookup"><span data-stu-id="288ad-120">Reference Types</span></span>  
 <span data-ttu-id="288ad-121">Un *type référence* stocke une référence à ses données.</span><span class="sxs-lookup"><span data-stu-id="288ad-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="288ad-122">Les types de référence incluent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="288ad-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="288ad-123">Tous les tableaux, même si leurs éléments sont des types valeur</span><span class="sxs-lookup"><span data-stu-id="288ad-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="288ad-124">Les types de classe, tels que <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="288ad-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="288ad-125">Délégués</span><span class="sxs-lookup"><span data-stu-id="288ad-125">Delegates</span></span>  
  
 <span data-ttu-id="288ad-126">Une classe est un *type référence*.</span><span class="sxs-lookup"><span data-stu-id="288ad-126">A class is a *reference type*.</span></span> <span data-ttu-id="288ad-127">Notez que chaque tableau est un type référence, même si ses membres sont des types valeur.</span><span class="sxs-lookup"><span data-stu-id="288ad-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="288ad-128">Étant donné que chaque type référence représente une classe .NET Framework sous-jacente, vous devez utiliser le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) quand vous l’initialisez.</span><span class="sxs-lookup"><span data-stu-id="288ad-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="288ad-129">L’instruction suivante initialise un tableau.</span><span class="sxs-lookup"><span data-stu-id="288ad-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="288ad-130">Éléments qui ne sont pas des types</span><span class="sxs-lookup"><span data-stu-id="288ad-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="288ad-131">Les éléments de programmation suivants ne sont pas qualifiés de types, car vous ne pouvez pas en spécifier un comme type de données pour un élément déclaré :</span><span class="sxs-lookup"><span data-stu-id="288ad-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="288ad-132">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="288ad-132">Namespaces</span></span>  
  
- <span data-ttu-id="288ad-133">Modules</span><span class="sxs-lookup"><span data-stu-id="288ad-133">Modules</span></span>  
  
- <span data-ttu-id="288ad-134">événements</span><span class="sxs-lookup"><span data-stu-id="288ad-134">Events</span></span>  
  
- <span data-ttu-id="288ad-135">Propriétés et procédures</span><span class="sxs-lookup"><span data-stu-id="288ad-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="288ad-136">Variables, constantes et champs</span><span class="sxs-lookup"><span data-stu-id="288ad-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="288ad-137">Utilisation du type de données Object</span><span class="sxs-lookup"><span data-stu-id="288ad-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="288ad-138">Vous pouvez assigner un type référence ou un type valeur à une variable du type de données `Object`.</span><span class="sxs-lookup"><span data-stu-id="288ad-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="288ad-139">Une variable `Object` contient toujours une référence aux données, jamais les données elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="288ad-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="288ad-140">Toutefois, si vous assignez un type valeur à une variable `Object`, il se comporte comme s’il contenait ses propres données.</span><span class="sxs-lookup"><span data-stu-id="288ad-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="288ad-141">Pour plus d’informations, consultez [Object Data type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="288ad-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="288ad-142">Vous pouvez déterminer si une variable `Object` agit comme un type référence ou un type valeur en la passant à la méthode <xref:Microsoft.VisualBasic.Information.IsReference%2A> dans la classe <xref:Microsoft.VisualBasic.Information> de l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="288ad-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="288ad-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> retourne `True` si le contenu de la variable `Object` représente un type référence.</span><span class="sxs-lookup"><span data-stu-id="288ad-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="288ad-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="288ad-144">See also</span></span>

- [<span data-ttu-id="288ad-145">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="288ad-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="288ad-146">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="288ad-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="288ad-147">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="288ad-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="288ad-148">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="288ad-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="288ad-149">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="288ad-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="288ad-150">Types de données</span><span class="sxs-lookup"><span data-stu-id="288ad-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
