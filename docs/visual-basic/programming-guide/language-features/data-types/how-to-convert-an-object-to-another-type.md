---
title: 'Comment : convertir un objet en un autre type'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 19708d03b0514f4572c2baa53e05781e5949766b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350071"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="d196f-102">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d196f-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="d196f-103">Vous convertissez une variable `Object` en un autre type de données à l’aide d’un mot clé de conversion tel que [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="d196f-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d196f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d196f-104">Example</span></span>  
 <span data-ttu-id="d196f-105">L’exemple suivant convertit une variable `Object` en `Integer` et un `String`.</span><span class="sxs-lookup"><span data-stu-id="d196f-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="d196f-106">Si vous savez que le contenu d’une variable de `Object` est d’un type de données particulier, il est préférable de convertir la variable en ce type de données.</span><span class="sxs-lookup"><span data-stu-id="d196f-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="d196f-107">Si vous continuez à utiliser la variable `Object`, vous devez effectuer une *conversion boxing* et *unboxing* (pour un type valeur) ou une *liaison tardive* (pour un type référence).</span><span class="sxs-lookup"><span data-stu-id="d196f-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="d196f-108">Ces opérations prennent toutes une durée d’exécution supplémentaire et ralentissent vos performances.</span><span class="sxs-lookup"><span data-stu-id="d196f-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d196f-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d196f-109">Compiling the Code</span></span>  
 <span data-ttu-id="d196f-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="d196f-110">This example requires:</span></span>  
  
- <span data-ttu-id="d196f-111">une référence à l'espace de noms <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d196f-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d196f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d196f-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="d196f-113">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d196f-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="d196f-114">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="d196f-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="d196f-115">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="d196f-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d196f-116">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="d196f-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="d196f-117">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="d196f-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="d196f-118">Structures</span><span class="sxs-lookup"><span data-stu-id="d196f-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="d196f-119">Types de données</span><span class="sxs-lookup"><span data-stu-id="d196f-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d196f-120">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="d196f-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
