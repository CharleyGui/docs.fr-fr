---
title: 'Procédure : Convertir un objet en un autre type'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: b89e996324d9ec22fc243b59502f3d36fefdee60
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090220"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="0c769-102">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c769-102">How to: Convert an Object to Another Type in Visual Basic</span></span>

<span data-ttu-id="0c769-103">Vous convertissez une `Object` variable en un autre type de données à l’aide d’un mot clé de conversion tel que [CType Function](../../../language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="0c769-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c769-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c769-104">Example</span></span>  

 <span data-ttu-id="0c769-105">L’exemple suivant convertit une `Object` variable en `Integer` et `String` .</span><span class="sxs-lookup"><span data-stu-id="0c769-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="0c769-106">Si vous savez que le contenu d’une `Object` variable est d’un type de données particulier, il est préférable de convertir la variable en ce type de données.</span><span class="sxs-lookup"><span data-stu-id="0c769-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="0c769-107">Si vous continuez à utiliser la `Object` variable, vous devez effectuer une *conversion boxing* et *unboxing* (pour un type valeur) ou une *liaison tardive* (pour un type référence).</span><span class="sxs-lookup"><span data-stu-id="0c769-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="0c769-108">Ces opérations prennent toutes une durée d’exécution supplémentaire et ralentissent vos performances.</span><span class="sxs-lookup"><span data-stu-id="0c769-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="0c769-109">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="0c769-109">Compile the code</span></span>  

 <span data-ttu-id="0c769-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="0c769-110">This example requires:</span></span>  
  
- <span data-ttu-id="0c769-111">une référence à l'espace de noms <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c769-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c769-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c769-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="0c769-113">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c769-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="0c769-114">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="0c769-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="0c769-115">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="0c769-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="0c769-116">Conversions entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="0c769-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="0c769-117">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="0c769-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="0c769-118">Structures</span><span class="sxs-lookup"><span data-stu-id="0c769-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="0c769-119">Data types</span><span class="sxs-lookup"><span data-stu-id="0c769-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="0c769-120">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="0c769-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
