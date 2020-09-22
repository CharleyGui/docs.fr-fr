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
ms.openlocfilehash: 0595356fb75fc0ac73a49622d71fe1d28fa7b648
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865905"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="3dce3-102">Of, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dce3-102">Of Clause (Visual Basic)</span></span>

<span data-ttu-id="3dce3-103">Introduit une `Of` clause qui identifie un *paramètre de type* sur une classe, une structure, une interface, un délégué ou une procédure *générique* .</span><span class="sxs-lookup"><span data-stu-id="3dce3-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="3dce3-104">Pour plus d’informations sur les types génériques, consultez [types génériques dans Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="3dce3-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="3dce3-105">Utilisation du mot clé of</span><span class="sxs-lookup"><span data-stu-id="3dce3-105">Using the Of Keyword</span></span>  

 <span data-ttu-id="3dce3-106">L’exemple de code suivant utilise le `Of` mot clé pour définir le plan d’une classe qui accepte deux paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="3dce3-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="3dce3-107">Il *limite* le `keyType` paramètre par l' <xref:System.IComparable> interface, ce qui signifie que le code de consommation doit fournir un argument de type qui implémente <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="3dce3-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="3dce3-108">Cela est nécessaire pour que la `add` procédure puisse appeler la <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="3dce3-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3dce3-109">Pour plus d’informations sur les contraintes, consultez [Type List](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="3dce3-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="3dce3-110">Si vous terminez la définition de classe précédente, vous pouvez construire diverses `dictionary` classes à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="3dce3-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="3dce3-111">Les types que vous fournissez à `entryType` et `keyType` déterminent le type d’entrée que contient la classe et le type de clé qu’elle associe à chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="3dce3-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="3dce3-112">En raison de la contrainte, vous devez fournir à `keyType` un type qui implémente <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="3dce3-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="3dce3-113">L’exemple de code suivant crée un objet qui contient des `String` entrées et associe une `Integer` clé à chacune d’entre elles.</span><span class="sxs-lookup"><span data-stu-id="3dce3-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="3dce3-114">`Integer` implémente <xref:System.IComparable> et, par conséquent, satisfait la contrainte sur `keyType` .</span><span class="sxs-lookup"><span data-stu-id="3dce3-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="3dce3-115">Le mot clé `Of` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="3dce3-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3dce3-116">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="3dce3-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="3dce3-117">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="3dce3-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="3dce3-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="3dce3-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="3dce3-119">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="3dce3-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="3dce3-120">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="3dce3-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="3dce3-121">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="3dce3-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3dce3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dce3-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="3dce3-123">Type List</span><span class="sxs-lookup"><span data-stu-id="3dce3-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="3dce3-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3dce3-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="3dce3-125">Dans</span><span class="sxs-lookup"><span data-stu-id="3dce3-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="3dce3-126">Sortie</span><span class="sxs-lookup"><span data-stu-id="3dce3-126">Out</span></span>](../modifiers/out-generic-modifier.md)
