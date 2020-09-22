---
title: ReDim (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 17bc806f2e92c61f1dd7425de40b1a68f926a583
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872029"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="abbf5-102">ReDim, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abbf5-102">ReDim Statement (Visual Basic)</span></span>

<span data-ttu-id="abbf5-103">Réalloue l'espace de stockage d'une variable tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abbf5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abbf5-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="abbf5-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="abbf5-105">Parts</span></span>  
  
|<span data-ttu-id="abbf5-106">Terme</span><span class="sxs-lookup"><span data-stu-id="abbf5-106">Term</span></span>|<span data-ttu-id="abbf5-107">Définition</span><span class="sxs-lookup"><span data-stu-id="abbf5-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="abbf5-108">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="abbf5-108">Optional.</span></span> <span data-ttu-id="abbf5-109">Modificateur utilisé pour conserver les données du tableau existant quand vous modifiez la taille de la dernière dimension uniquement.</span><span class="sxs-lookup"><span data-stu-id="abbf5-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="abbf5-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="abbf5-110">Required.</span></span> <span data-ttu-id="abbf5-111">Nom de la variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-111">Name of the array variable.</span></span> <span data-ttu-id="abbf5-112">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="abbf5-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="abbf5-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="abbf5-113">Required.</span></span> <span data-ttu-id="abbf5-114">Liste des limites de chaque dimension du tableau redéfini.</span><span class="sxs-lookup"><span data-stu-id="abbf5-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abbf5-115">Notes</span><span class="sxs-lookup"><span data-stu-id="abbf5-115">Remarks</span></span>  

 <span data-ttu-id="abbf5-116">Vous pouvez utiliser l'instruction `ReDim` pour modifier la taille d'une ou plusieurs dimensions d'un tableau qui a déjà été déclaré.</span><span class="sxs-lookup"><span data-stu-id="abbf5-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="abbf5-117">Si vous possédez un grand tableau et que vous n'avez plus besoin de certains de ses éléments, `ReDim` peut libérer de la mémoire en réduisant la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="abbf5-118">En revanche, si votre tableau a besoin d'éléments supplémentaires, `ReDim` peut les ajouter.</span><span class="sxs-lookup"><span data-stu-id="abbf5-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="abbf5-119">L'instruction `ReDim` est destinée uniquement aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="abbf5-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="abbf5-120">Il n'est pas valide sur les scalaires (variables contenant une seule valeur), les collections ou les structures.</span><span class="sxs-lookup"><span data-stu-id="abbf5-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="abbf5-121">Notez que si vous déclarez une variable de type `Array`, l'instruction `ReDim` ne dispose pas d'informations de type suffisantes pour créer le tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="abbf5-122">Vous pouvez utiliser `ReDim` uniquement au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="abbf5-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="abbf5-123">Par conséquent, le contexte de déclaration pour la variable doit être une procédure ; il ne peut pas être un fichier source, un espace de noms, une interface, une classe, une structure, un module ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="abbf5-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="abbf5-124">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="abbf5-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="abbf5-125">Règles</span><span class="sxs-lookup"><span data-stu-id="abbf5-125">Rules</span></span>  
  
- <span data-ttu-id="abbf5-126">**Variables multiples.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-126">**Multiple Variables.**</span></span> <span data-ttu-id="abbf5-127">Vous pouvez redimensionner plusieurs variables de tableau dans la même instruction de déclaration et spécifier les `name` `boundlist` parties et pour chaque variable.</span><span class="sxs-lookup"><span data-stu-id="abbf5-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="abbf5-128">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="abbf5-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="abbf5-129">**Limites du tableau.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-129">**Array Bounds.**</span></span> <span data-ttu-id="abbf5-130">Chaque entrée dans `boundlist` peut spécifier les limites inférieure et supérieure de cette dimension.</span><span class="sxs-lookup"><span data-stu-id="abbf5-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="abbf5-131">La limite inférieure est toujours 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="abbf5-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="abbf5-132">La limite supérieure est la valeur d'index la plus élevée possible pour cette dimension, pas la longueur de la dimension (qui est la limite supérieure plus un).</span><span class="sxs-lookup"><span data-stu-id="abbf5-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="abbf5-133">L'index pour chaque dimension varie de 0 à sa valeur liée supérieure.</span><span class="sxs-lookup"><span data-stu-id="abbf5-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="abbf5-134">Le nombre de dimensions dans `boundlist` doit correspondre au nombre de dimensions (rang) d'origine du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="abbf5-135">**Types de données.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-135">**Data Types.**</span></span> <span data-ttu-id="abbf5-136">L' `ReDim` instruction ne peut pas modifier le type de données d’une variable tableau ou de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="abbf5-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="abbf5-137">**D’initialisation.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-137">**Initialization.**</span></span> <span data-ttu-id="abbf5-138">L' `ReDim` instruction ne peut pas fournir de nouvelles valeurs d’initialisation pour les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="abbf5-139">**Moteurs.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-139">**Rank.**</span></span> <span data-ttu-id="abbf5-140">L' `ReDim` instruction ne peut pas modifier le rang (nombre de dimensions) du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="abbf5-141">**Redimensionnement avec Preserve.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="abbf5-142">Si vous utilisez `Preserve` , vous pouvez redimensionner uniquement la dernière dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="abbf5-143">Pour chaque autre dimension, vous devez spécifier la limite du tableau existant.</span><span class="sxs-lookup"><span data-stu-id="abbf5-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="abbf5-144">Par exemple, si votre tableau ne comporte qu'une seule dimension, vous pouvez la redimensionner tout en conservant le contenu du tableau, car vous modifiez la dernière et seule dimension.</span><span class="sxs-lookup"><span data-stu-id="abbf5-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="abbf5-145">Toutefois, si votre tableau comporte deux dimensions ou plus, vous pouvez modifier la taille de la dernière dimension seulement si vous utilisez `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="abbf5-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="abbf5-146">**Sous.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-146">**Properties.**</span></span> <span data-ttu-id="abbf5-147">Vous pouvez utiliser `ReDim` sur une propriété qui contient un tableau de valeurs.</span><span class="sxs-lookup"><span data-stu-id="abbf5-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="abbf5-148">Comportement</span><span class="sxs-lookup"><span data-stu-id="abbf5-148">Behavior</span></span>  
  
- <span data-ttu-id="abbf5-149">**Remplacement de tableau.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-149">**Array Replacement.**</span></span> <span data-ttu-id="abbf5-150">`ReDim` libère le tableau existant et crée un nouveau tableau avec le même rang.</span><span class="sxs-lookup"><span data-stu-id="abbf5-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="abbf5-151">Le nouveau tableau remplace le tableau libéré dans la variable tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="abbf5-152">**Initialisation sans Preserve.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="abbf5-153">Si vous ne spécifiez pas `Preserve` , `ReDim` Initialise les éléments du nouveau tableau en utilisant la valeur par défaut pour leur type de données.</span><span class="sxs-lookup"><span data-stu-id="abbf5-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="abbf5-154">**Initialisation avec Preserve.**</span><span class="sxs-lookup"><span data-stu-id="abbf5-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="abbf5-155">Si vous spécifiez `Preserve` , Visual Basic copie les éléments du tableau existant dans le nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abbf5-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="abbf5-156">Example</span></span>  

 <span data-ttu-id="abbf5-157">L'exemple suivant augmente la taille de la dernière dimension d'un tableau dynamique sans perte de données existantes dans le tableau, puis réduit la taille avec une perte de données partielle.</span><span class="sxs-lookup"><span data-stu-id="abbf5-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="abbf5-158">Enfin, il réduit la taille à sa valeur d'origine et réinitialise tous les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="abbf5-159">L'instruction `Dim` crée un tableau à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="abbf5-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="abbf5-160">Étant donné que chaque dimension est déclarée avec une limite de 10, l'index de tableau pour chaque dimension peut aller de 0 à 10.</span><span class="sxs-lookup"><span data-stu-id="abbf5-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="abbf5-161">Dans la discussion suivante, les trois dimensions sont appelées « couche », « ligne » et « colonne ».</span><span class="sxs-lookup"><span data-stu-id="abbf5-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="abbf5-162">La première instruction `ReDim` crée un tableau qui remplace le tableau existant dans la variable `intArray`.</span><span class="sxs-lookup"><span data-stu-id="abbf5-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="abbf5-163">`ReDim` copie tous les éléments du tableau existant dans le nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="abbf5-164">Elle ajoute également 10 colonnes supplémentaires à la fin de chaque ligne dans chaque couche et initialise les éléments de ces nouvelles colonnes à 0 (la valeur par défaut d'`Integer`, qui est le type d'élément du tableau).</span><span class="sxs-lookup"><span data-stu-id="abbf5-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="abbf5-165">La deuxième instruction `ReDim` crée un autre tableau et copie tous les éléments adaptés.</span><span class="sxs-lookup"><span data-stu-id="abbf5-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="abbf5-166">Toutefois, les cinq colonnes sont perdus à la fin de chaque ligne dans chaque couche.</span><span class="sxs-lookup"><span data-stu-id="abbf5-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="abbf5-167">Cela n'est pas un problème si vous avez fini d'utiliser ces colonnes.</span><span class="sxs-lookup"><span data-stu-id="abbf5-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="abbf5-168">La réduction de la taille d'un grand tableau peut libérer de la mémoire dont vous n'avez plus besoin.</span><span class="sxs-lookup"><span data-stu-id="abbf5-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="abbf5-169">La troisième instruction `ReDim` crée un autre tableau et supprime cinq autres colonnes de la fin de chaque ligne dans chaque couche.</span><span class="sxs-lookup"><span data-stu-id="abbf5-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="abbf5-170">Cette fois-ci, elle ne copie pas les éléments existants.</span><span class="sxs-lookup"><span data-stu-id="abbf5-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="abbf5-171">Cette instruction rétablit la taille d'origine du tableau.</span><span class="sxs-lookup"><span data-stu-id="abbf5-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="abbf5-172">Étant donné que l'instruction n'inclut pas le modificateur `Preserve`, elle définit tous les éléments de tableau à leurs valeurs par défaut d'origine.</span><span class="sxs-lookup"><span data-stu-id="abbf5-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="abbf5-173">Pour obtenir des exemples supplémentaires, consultez [tableaux](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="abbf5-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbf5-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abbf5-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="abbf5-175">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="abbf5-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="abbf5-176">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="abbf5-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="abbf5-177">Erase (instruction)</span><span class="sxs-lookup"><span data-stu-id="abbf5-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="abbf5-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="abbf5-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="abbf5-179">Tableaux</span><span class="sxs-lookup"><span data-stu-id="abbf5-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
