---
title: Types de méthodes de manipulation de chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: c44f02880858b8a9fc1f0e70c3226623d05baa3a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072468"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="744b7-102">Types de méthodes de manipulation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="744b7-102">Types of String Manipulation Methods in Visual Basic</span></span>

<span data-ttu-id="744b7-103">Il existe différentes façons d’analyser et de manipuler vos chaînes.</span><span class="sxs-lookup"><span data-stu-id="744b7-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="744b7-104">Certaines méthodes font partie du langage de Visual Basic, tandis que d’autres sont inhérentes à la `String` classe.</span><span class="sxs-lookup"><span data-stu-id="744b7-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="744b7-105">Visual Basic langage et le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="744b7-105">Visual Basic Language and the .NET Framework</span></span>  

 <span data-ttu-id="744b7-106">Les méthodes de Visual Basic sont utilisées comme fonctions inhérentes du langage.</span><span class="sxs-lookup"><span data-stu-id="744b7-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="744b7-107">Elles peuvent être utilisées sans qualification dans votre code.</span><span class="sxs-lookup"><span data-stu-id="744b7-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="744b7-108">L’exemple suivant illustre l’utilisation classique d’une commande de manipulation de chaînes Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="744b7-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="744b7-109">Dans cet exemple, la `Mid` fonction effectue une opération directe sur `aString` et assigne la valeur à `bString` .</span><span class="sxs-lookup"><span data-stu-id="744b7-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="744b7-110">Pour obtenir la liste des Visual Basic méthodes de manipulation de chaînes, consultez Résumé de la [manipulation de chaînes](../../../language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="744b7-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="744b7-111">Méthodes partagées et méthodes d’instance</span><span class="sxs-lookup"><span data-stu-id="744b7-111">Shared Methods and Instance Methods</span></span>  

 <span data-ttu-id="744b7-112">Vous pouvez également manipuler des chaînes avec les méthodes de la `String` classe.</span><span class="sxs-lookup"><span data-stu-id="744b7-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="744b7-113">Il existe deux types de méthodes dans `String` : les méthodes *partagées* et les méthodes d' *instance* .</span><span class="sxs-lookup"><span data-stu-id="744b7-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="744b7-114">Méthodes partagées</span><span class="sxs-lookup"><span data-stu-id="744b7-114">Shared Methods</span></span>  

 <span data-ttu-id="744b7-115">Une méthode partagée est une méthode qui provient de la `String` classe elle-même et qui ne requiert pas l’utilisation d’une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="744b7-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="744b7-116">Ces méthodes peuvent être qualifiées avec le nom de la classe ( `String` ) plutôt qu’avec une instance de la `String` classe.</span><span class="sxs-lookup"><span data-stu-id="744b7-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="744b7-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="744b7-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="744b7-118">Dans l’exemple précédent, la <xref:System.String.Copy%2A?displayProperty=nameWithType> méthode est une méthode statique qui agit sur une expression à laquelle elle est donnée et assigne la valeur résultante à `bString` .</span><span class="sxs-lookup"><span data-stu-id="744b7-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="744b7-119">Méthodes d’instance</span><span class="sxs-lookup"><span data-stu-id="744b7-119">Instance Methods</span></span>  

 <span data-ttu-id="744b7-120">En revanche, les méthodes d’instance proviennent d’une instance particulière de `String` et doivent être qualifiées avec le nom de l’instance.</span><span class="sxs-lookup"><span data-stu-id="744b7-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="744b7-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="744b7-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="744b7-122">Dans cet exemple, la <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode est une méthode de l’instance de `String` (autrement dit, `aString` ).</span><span class="sxs-lookup"><span data-stu-id="744b7-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="744b7-123">Il effectue une opération sur `aString` et assigne cette valeur à `bString` .</span><span class="sxs-lookup"><span data-stu-id="744b7-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="744b7-124">Pour plus d’informations, consultez la documentation de la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="744b7-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744b7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="744b7-125">See also</span></span>

- [<span data-ttu-id="744b7-126">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="744b7-126">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
