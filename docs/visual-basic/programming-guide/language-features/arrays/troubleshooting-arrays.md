---
title: Résolution des problèmes de tableaux
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: e0cb1008f4182331b7380db81d7a92a0fd45f2f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086359"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="31d7e-102">Dépannage des tableaux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31d7e-102">Troubleshooting Arrays (Visual Basic)</span></span>

<span data-ttu-id="31d7e-103">Cette page répertorie certains problèmes courants qui peuvent se produire lors de l’utilisation de tableaux.</span><span class="sxs-lookup"><span data-stu-id="31d7e-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="31d7e-104">Erreurs de compilation lors de la déclaration et de l’initialisation d’un tableau</span><span class="sxs-lookup"><span data-stu-id="31d7e-104">Compilation Errors Declaring and Initializing an Array</span></span>  

 <span data-ttu-id="31d7e-105">Les erreurs de compilation peuvent provenir d’une mauvaise compréhension des règles de déclaration, de création et d’initialisation de tableaux.</span><span class="sxs-lookup"><span data-stu-id="31d7e-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="31d7e-106">Les causes les plus courantes des erreurs sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="31d7e-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="31d7e-107">En fournissant une [nouvelle](../../../language-reference/operators/new-operator.md) clause d’opérateur après avoir spécifié des longueurs de dimensions dans la déclaration de variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="31d7e-107">Supplying a [New Operator](../../../language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="31d7e-108">Les lignes de code suivantes affichent des déclarations non valides de ce type.</span><span class="sxs-lookup"><span data-stu-id="31d7e-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="31d7e-109">Spécification des longueurs de dimensions pour plus que le tableau de niveau supérieur d’un tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="31d7e-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="31d7e-110">La ligne de code suivante montre une déclaration non valide de ce type.</span><span class="sxs-lookup"><span data-stu-id="31d7e-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="31d7e-111">Omission du `New` mot clé lors de la spécification des valeurs de l’élément.</span><span class="sxs-lookup"><span data-stu-id="31d7e-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="31d7e-112">La ligne de code suivante montre une déclaration non valide de ce type.</span><span class="sxs-lookup"><span data-stu-id="31d7e-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="31d7e-113">Spécification d’une `New` clause sans accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="31d7e-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="31d7e-114">Les lignes de code suivantes affichent des déclarations non valides de ce type.</span><span class="sxs-lookup"><span data-stu-id="31d7e-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="31d7e-115">Accès à un tableau hors limites</span><span class="sxs-lookup"><span data-stu-id="31d7e-115">Accessing an Array Out of Bounds</span></span>  

 <span data-ttu-id="31d7e-116">Le processus d’initialisation d’un tableau assigne une limite supérieure et une limite inférieure à chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="31d7e-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="31d7e-117">Chaque accès à un élément du tableau doit spécifier un index valide, ou indice, pour chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="31d7e-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="31d7e-118">Si un index est inférieur à sa limite inférieure ou au-dessus de sa limite supérieure, une <xref:System.IndexOutOfRangeException> exception se produit.</span><span class="sxs-lookup"><span data-stu-id="31d7e-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="31d7e-119">Le compilateur ne peut pas détecter une telle erreur, de sorte qu’une erreur se produit au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="31d7e-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="31d7e-120">Détermination des limites</span><span class="sxs-lookup"><span data-stu-id="31d7e-120">Determining Bounds</span></span>  

 <span data-ttu-id="31d7e-121">Si un autre composant passe un tableau à votre code, par exemple en tant qu’argument de procédure, vous ne connaissez pas la taille de ce tableau ni les longueurs de ses dimensions.</span><span class="sxs-lookup"><span data-stu-id="31d7e-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="31d7e-122">Vous devez toujours déterminer la limite supérieure pour chaque dimension d’un tableau avant de tenter d’accéder à tous les éléments.</span><span class="sxs-lookup"><span data-stu-id="31d7e-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="31d7e-123">Si le tableau a été créé par d’autres moyens que la `New` clause Visual Basic, la limite inférieure peut être différente de 0, et il est plus sûr de déterminer également la limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="31d7e-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="31d7e-124">Spécification de la dimension</span><span class="sxs-lookup"><span data-stu-id="31d7e-124">Specifying the Dimension</span></span>  

 <span data-ttu-id="31d7e-125">Lorsque vous déterminez les limites d’un tableau multidimensionnel, prenez soin de la façon dont vous spécifiez la dimension.</span><span class="sxs-lookup"><span data-stu-id="31d7e-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="31d7e-126">Les `dimension` paramètres des <xref:System.Array.GetLowerBound%2A> méthodes et <xref:System.Array.GetUpperBound%2A> sont basés sur 0, tandis que les `Rank` paramètres de la Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> et des <xref:Microsoft.VisualBasic.Information.UBound%2A> fonctions sont de base 1.</span><span class="sxs-lookup"><span data-stu-id="31d7e-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d7e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d7e-127">See also</span></span>

- [<span data-ttu-id="31d7e-128">Tableaux</span><span class="sxs-lookup"><span data-stu-id="31d7e-128">Arrays</span></span>](index.md)
- [<span data-ttu-id="31d7e-129">Comment : initialiser une variable tableau en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31d7e-129">How to: Initialize an Array Variable in Visual Basic</span></span>](how-to-initialize-an-array-variable.md)
