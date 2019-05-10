---
title: Dépannage des tableaux (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 69d5294eacc59718adb1b0a226594d2cf69273f5
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913463"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="695b3-102">Dépannage des tableaux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="695b3-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="695b3-103">Cette page répertorie certains problèmes courants qui peuvent se produire lorsque vous travaillez avec des tableaux.</span><span class="sxs-lookup"><span data-stu-id="695b3-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="695b3-104">Déclaration et initialisation d’un tableau d’erreurs de compilation</span><span class="sxs-lookup"><span data-stu-id="695b3-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="695b3-105">Erreurs de compilation peuvent se produire à partir de la méconnaissance des relations entre les règles de déclaration, la création et initialisation des tableaux.</span><span class="sxs-lookup"><span data-stu-id="695b3-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="695b3-106">Les causes les plus courantes d’erreurs sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="695b3-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="695b3-107">En fournissant un [nouvel opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) clause après avoir spécifié les longueurs de dimensions dans la déclaration de variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="695b3-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="695b3-108">Les lignes de code suivantes illustrent des déclarations non valides de ce type.</span><span class="sxs-lookup"><span data-stu-id="695b3-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="695b3-109">Spécification de longueurs de dimensions plus longtemps que le tableau de niveau supérieur d’un tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="695b3-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="695b3-110">La ligne de code suivant montre une déclaration non valide de ce type.</span><span class="sxs-lookup"><span data-stu-id="695b3-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="695b3-111">En omettant le `New` mot clé lorsque vous spécifiez les valeurs d’élément.</span><span class="sxs-lookup"><span data-stu-id="695b3-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="695b3-112">La ligne de code suivant montre une déclaration non valide de ce type.</span><span class="sxs-lookup"><span data-stu-id="695b3-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="695b3-113">En fournissant un `New` clause sans accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="695b3-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="695b3-114">Les lignes de code suivantes illustrent des déclarations non valides de ce type.</span><span class="sxs-lookup"><span data-stu-id="695b3-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="695b3-115">L’accès à un tableau hors limites</span><span class="sxs-lookup"><span data-stu-id="695b3-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="695b3-116">Le processus d’initialisation d’un tableau assigne une limite supérieure et inférieure à chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="695b3-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="695b3-117">Chaque accès à un élément du tableau doit spécifier un index valide, ou un indice, pour chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="695b3-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="695b3-118">Si un index est inférieur à sa limite inférieure ou au-dessus de sa limite supérieure, une <xref:System.IndexOutOfRangeException> résultats de l’exception.</span><span class="sxs-lookup"><span data-stu-id="695b3-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="695b3-119">Le compilateur ne peut pas détecter une telle erreur, donc une erreur se produit au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="695b3-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="695b3-120">Détermination des limites</span><span class="sxs-lookup"><span data-stu-id="695b3-120">Determining Bounds</span></span>  
 <span data-ttu-id="695b3-121">Si un autre composant passe un tableau à votre code, par exemple en tant qu’argument de procédure, vous ne connaissez pas la taille de ce tableau ou les longueurs de ses dimensions.</span><span class="sxs-lookup"><span data-stu-id="695b3-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="695b3-122">Vous devez toujours déterminer la limite supérieure de chaque dimension d’un tableau avant de tenter d’accéder aux éléments.</span><span class="sxs-lookup"><span data-stu-id="695b3-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="695b3-123">Si le groupe a été créé par des moyens autres que Visual Basic `New` clause, la limite inférieure peut avoir une valeur différente de 0, et il est plus sûre déterminer ce inférieure.</span><span class="sxs-lookup"><span data-stu-id="695b3-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="695b3-124">Spécification de la Dimension</span><span class="sxs-lookup"><span data-stu-id="695b3-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="695b3-125">Lorsque vous déterminez les limites d’un tableau multidimensionnel, veillez à vous spécifiez comment la dimension.</span><span class="sxs-lookup"><span data-stu-id="695b3-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="695b3-126">Le `dimension` paramètres de le <xref:System.Array.GetLowerBound%2A> et <xref:System.Array.GetUpperBound%2A> méthodes sont basés sur 0, lors de la `Rank` paramètres de Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> et <xref:Microsoft.VisualBasic.Information.UBound%2A> fonctions sont de base 1.</span><span class="sxs-lookup"><span data-stu-id="695b3-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695b3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="695b3-127">See also</span></span>

- [<span data-ttu-id="695b3-128">Tableaux</span><span class="sxs-lookup"><span data-stu-id="695b3-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="695b3-129">Guide pratique pour Initialiser une Variable tableau en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="695b3-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
