---
title: Impossible de convertir le type anonyme en arborescence de l'expression, car elle contient un champ qui sert à initialiser un autre champ
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: 045061f403b301d460bc85d161c1d6dee9c7d9f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602400"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="f254d-102">Impossible de convertir le type anonyme en arborescence de l'expression, car elle contient un champ qui sert à initialiser un autre champ</span><span class="sxs-lookup"><span data-stu-id="f254d-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="f254d-103">Le compilateur n’accepte pas de conversion d’un anonyme en une arborescence d’expression lorsqu’une propriété du type anonyme est utilisée pour initialiser une autre propriété du type anonyme.</span><span class="sxs-lookup"><span data-stu-id="f254d-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="f254d-104">Par exemple, dans le code suivant, `Prop1` est déclarée dans la liste d’initialisation et ensuite utilisée comme valeur initiale pour `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="f254d-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f254d-105">**ID d’erreur :** BC36548</span><span class="sxs-lookup"><span data-stu-id="f254d-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f254d-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f254d-106">To correct this error</span></span>  
  
- <span data-ttu-id="f254d-107">Affectez la valeur initiale pour `Prop1` à une variable locale.</span><span class="sxs-lookup"><span data-stu-id="f254d-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="f254d-108">Assignez cette variable à la fois aux `Prop1` et `Prop2`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f254d-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f254d-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f254d-109">See also</span></span>

- [<span data-ttu-id="f254d-110">Types anonymes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f254d-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f254d-111">Arborescences d’expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f254d-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="f254d-112">Guide pratique pour Utiliser des arborescences d’Expression pour générer des requêtes dynamiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f254d-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
