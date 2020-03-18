---
title: Tableaux multidimensionnels - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715040"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="7464a-102">Tableaux multidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7464a-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="7464a-103">Les tableaux peuvent avoir plusieurs dimensions.</span><span class="sxs-lookup"><span data-stu-id="7464a-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="7464a-104">Par exemple, la déclaration suivante crée un tableau à deux dimensions composé de quatre lignes et deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="7464a-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="7464a-105">La déclaration suivante crée un tableau de trois dimensions, 4, 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="7464a-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="7464a-106">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="7464a-106">Array Initialization</span></span>

 <span data-ttu-id="7464a-107">Vous pouvez initialiser le tableau au moment de la déclaration, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7464a-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="7464a-108">Vous pouvez aussi initialiser le tableau sans spécifier de rang.</span><span class="sxs-lookup"><span data-stu-id="7464a-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="7464a-109">Si vous choisissez de déclarer une variable de tableau sans initialisation, vous devez utiliser l’opérateur `new` pour assigner un tableau à la variable.</span><span class="sxs-lookup"><span data-stu-id="7464a-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="7464a-110">L’utilisation de `new` est illustrée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7464a-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="7464a-111">L’exemple suivant assigne une valeur à un élément de tableau particulier.</span><span class="sxs-lookup"><span data-stu-id="7464a-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="7464a-112">De la même manière, l’exemple suivant obtient la valeur d’un élément de tableau particulier et l’affecte à la variable `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="7464a-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="7464a-113">L’exemple de code suivant initialise les éléments de tableau avec les valeurs par défaut (sauf pour les tableaux en escalier).</span><span class="sxs-lookup"><span data-stu-id="7464a-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="7464a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7464a-114">See also</span></span>

- [<span data-ttu-id="7464a-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7464a-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7464a-116">Tableaux</span><span class="sxs-lookup"><span data-stu-id="7464a-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="7464a-117">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="7464a-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="7464a-118">Arrays déchiquetés</span><span class="sxs-lookup"><span data-stu-id="7464a-118">Jagged Arrays</span></span>](./jagged-arrays.md)
