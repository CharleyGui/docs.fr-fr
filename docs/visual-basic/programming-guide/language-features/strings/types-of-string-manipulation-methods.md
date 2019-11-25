---
title: Types de méthodes de manipulation de chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346271"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="84c66-102">Types de méthodes de manipulation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84c66-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="84c66-103">There are several different ways to analyze and manipulate your strings.</span><span class="sxs-lookup"><span data-stu-id="84c66-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="84c66-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span><span class="sxs-lookup"><span data-stu-id="84c66-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="84c66-105">Visual Basic Language and the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84c66-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="84c66-106">Visual Basic methods are used as inherent functions of the language.</span><span class="sxs-lookup"><span data-stu-id="84c66-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="84c66-107">They may be used without qualification in your code.</span><span class="sxs-lookup"><span data-stu-id="84c66-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="84c66-108">The following example shows typical use of a Visual Basic string-manipulation command:</span><span class="sxs-lookup"><span data-stu-id="84c66-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="84c66-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span><span class="sxs-lookup"><span data-stu-id="84c66-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="84c66-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="84c66-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="84c66-111">Shared Methods and Instance Methods</span><span class="sxs-lookup"><span data-stu-id="84c66-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="84c66-112">You can also manipulate strings with the methods of the `String` class.</span><span class="sxs-lookup"><span data-stu-id="84c66-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="84c66-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span><span class="sxs-lookup"><span data-stu-id="84c66-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="84c66-114">Shared Methods</span><span class="sxs-lookup"><span data-stu-id="84c66-114">Shared Methods</span></span>  
 <span data-ttu-id="84c66-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span><span class="sxs-lookup"><span data-stu-id="84c66-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="84c66-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span><span class="sxs-lookup"><span data-stu-id="84c66-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="84c66-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84c66-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="84c66-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span><span class="sxs-lookup"><span data-stu-id="84c66-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="84c66-119">Instance Methods</span><span class="sxs-lookup"><span data-stu-id="84c66-119">Instance Methods</span></span>  
 <span data-ttu-id="84c66-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span><span class="sxs-lookup"><span data-stu-id="84c66-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="84c66-121">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84c66-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="84c66-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span><span class="sxs-lookup"><span data-stu-id="84c66-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="84c66-123">It performs an operation on `aString` and assigns that value to `bString`.</span><span class="sxs-lookup"><span data-stu-id="84c66-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="84c66-124">For more information, see the documentation for the <xref:System.String> class.</span><span class="sxs-lookup"><span data-stu-id="84c66-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c66-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84c66-125">See also</span></span>

- [<span data-ttu-id="84c66-126">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84c66-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
