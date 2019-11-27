---
title: Of (clause)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353838"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="d55c7-102">Of, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d55c7-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="d55c7-103">Introduit une clause `Of`, qui identifie un *paramètre de type* sur une classe, une structure, une interface, un délégué ou une procédure *générique* .</span><span class="sxs-lookup"><span data-stu-id="d55c7-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="d55c7-104">Pour plus d’informations sur les types génériques, consultez [types génériques dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="d55c7-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="d55c7-105">Utilisation du mot clé of</span><span class="sxs-lookup"><span data-stu-id="d55c7-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="d55c7-106">L’exemple de code suivant utilise le mot clé `Of` pour définir le plan d’une classe qui accepte deux paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="d55c7-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="d55c7-107">Il *limite* le paramètre `keyType` par l’interface <xref:System.IComparable>, ce qui signifie que le code de consommation doit fournir un argument de type qui implémente <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="d55c7-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="d55c7-108">Cela est nécessaire pour que la procédure `add` puisse appeler la méthode <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d55c7-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d55c7-109">Pour plus d’informations sur les contraintes, consultez [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d55c7-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="d55c7-110">Si vous terminez la définition de classe précédente, vous pouvez construire une variété de `dictionary` classes à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="d55c7-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="d55c7-111">Les types que vous fournissez à `entryType` et `keyType` déterminent le type d’entrée que contient la classe et le type de clé qu’elle associe à chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="d55c7-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="d55c7-112">En raison de la contrainte, vous devez fournir à `keyType` un type qui implémente <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="d55c7-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="d55c7-113">L’exemple de code suivant crée un objet qui contient des entrées `String` et associe une clé `Integer` à chacune d’entre elles.</span><span class="sxs-lookup"><span data-stu-id="d55c7-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="d55c7-114">`Integer` implémente <xref:System.IComparable> et, par conséquent, satisfait la contrainte sur `keyType`.</span><span class="sxs-lookup"><span data-stu-id="d55c7-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="d55c7-115">Le mot clé `Of` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="d55c7-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d55c7-116">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="d55c7-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="d55c7-117">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="d55c7-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="d55c7-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="d55c7-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d55c7-119">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="d55c7-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="d55c7-120">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="d55c7-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="d55c7-121">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="d55c7-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d55c7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d55c7-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="d55c7-123">Liste de types</span><span class="sxs-lookup"><span data-stu-id="d55c7-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="d55c7-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d55c7-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d55c7-125">In</span><span class="sxs-lookup"><span data-stu-id="d55c7-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="d55c7-126">Out</span><span class="sxs-lookup"><span data-stu-id="d55c7-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
