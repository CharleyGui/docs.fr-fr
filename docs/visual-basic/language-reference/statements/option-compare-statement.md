---
title: Option Compare, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 1ffe3e45a296d02364f488540d987d85133013bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404380"
---
# <a name="option-compare-statement"></a><span data-ttu-id="9c8fa-102">Option Compare, instruction</span><span class="sxs-lookup"><span data-stu-id="9c8fa-102">Option Compare Statement</span></span>
<span data-ttu-id="9c8fa-103">Déclare la méthode de comparaison par défaut à utiliser lors de la comparaison de données de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c8fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c8fa-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="9c8fa-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="9c8fa-105">Parts</span></span>  
  
|<span data-ttu-id="9c8fa-106">Terme</span><span class="sxs-lookup"><span data-stu-id="9c8fa-106">Term</span></span>|<span data-ttu-id="9c8fa-107">Définition</span><span class="sxs-lookup"><span data-stu-id="9c8fa-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="9c8fa-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-108">Optional.</span></span> <span data-ttu-id="9c8fa-109">Se traduit par des comparaisons de chaînes basées sur un ordre de tri dérivé des représentations binaires internes des caractères.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="9c8fa-110">Ce type de comparaison est utile surtout si les chaînes peuvent contenir des caractères qui ne doivent ne pas être interprétées comme du texte.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="9c8fa-111">Dans ce cas, il convient de ne pas fausser les comparaisons avec des équivalences alphabétiques comme, par exemple, quand la casse n'est pas respectée.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="9c8fa-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-112">Optional.</span></span> <span data-ttu-id="9c8fa-113">Se traduit par des comparaisons de chaînes basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="9c8fa-114">Ce type de comparaison est utile si vos chaînes contiennent toutes des caractères de texte et si vous voulez les comparer en prenant en compte les équivalences alphabétiques, c'est-à-dire des lettres très proches ou de casse différente.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="9c8fa-115">Par exemple, vous pouvez faire en sorte que les caractères `A` et `a` soient considérés comme identiques et que les caractères `Ä` et `ä` précèdent `B` et `b`.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c8fa-116">Notes</span><span class="sxs-lookup"><span data-stu-id="9c8fa-116">Remarks</span></span>  
 <span data-ttu-id="9c8fa-117">Si elle est utilisée, l'instruction `Option Compare` doit apparaître dans un fichier avant toute autre instruction de code source.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="9c8fa-118">L'instruction `Option Compare` permet de spécifier la méthode de comparaison de chaînes (`Binary` ou `Text`).</span><span class="sxs-lookup"><span data-stu-id="9c8fa-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="9c8fa-119">La méthode de comparaison de texte par défaut est `Binary`.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="9c8fa-120">Une comparaison de type `Binary` permet de comparer la valeur Unicode numérique de chaque caractère dans chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="9c8fa-121">Une comparaison de type `Text` permet de comparer chaque caractère Unicode selon sa signification lexicale dans la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="9c8fa-122">Dans Microsoft Windows, l'ordre de tri est déterminé par la page de code.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="9c8fa-123">Pour plus d’informations, consultez [Pages de codes](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="9c8fa-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="9c8fa-124">Dans l'exemple suivant, les caractères de la page de codes Anglais/Européen (ANSI 1252) sont triés à l'aide de `Option Compare Binary`, qui génère un ordre de tri binaire standard.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="9c8fa-125">Quand les mêmes caractères d'une même page de codes sont triés à l'aide de `Option Compare Text`, l'ordre de tri de texte suivant est généré.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="9c8fa-126">En l'absence d'instruction Option Compare</span><span class="sxs-lookup"><span data-stu-id="9c8fa-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="9c8fa-127">Si le code source ne contient pas d' `Option Compare` instruction, le paramètre **option compare** sur la [page compiler, concepteur de projets (Visual Basic),](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="9c8fa-128">Si vous utilisez le compilateur de ligne de commande, le paramètre spécifié par l’option [de compilateur-optioncompare](../../reference/command-line-compiler/optioncompare.md) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="9c8fa-129">Pour définir Option Compare dans l'IDE</span><span class="sxs-lookup"><span data-stu-id="9c8fa-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="9c8fa-130">Dans **Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="9c8fa-131">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="9c8fa-132">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="9c8fa-133">Définissez la valeur dans la zone **option compare** .</span><span class="sxs-lookup"><span data-stu-id="9c8fa-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="9c8fa-134">Lorsque vous créez un projet, le paramètre **option compare** de l’onglet **compiler** est défini sur le paramètre **option compare** dans la boîte de dialogue **options** .</span><span class="sxs-lookup"><span data-stu-id="9c8fa-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="9c8fa-135">Pour modifier ce paramètre, dans le menu **Outils** , cliquez sur **options**.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="9c8fa-136">Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="9c8fa-137">Le paramètre par défaut initial dans les **valeurs par défaut VB** est **binaire**.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="9c8fa-138">Pour définir Option Compare sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="9c8fa-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="9c8fa-139">Incluez l’option de compilateur [-optioncompare](../../reference/command-line-compiler/optioncompare.md) dans la commande **vbc** .</span><span class="sxs-lookup"><span data-stu-id="9c8fa-139">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c8fa-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c8fa-140">Example</span></span>  
 <span data-ttu-id="9c8fa-141">L'exemple suivant utilise l'instruction `Option Compare` pour définir la comparaison binaire comme méthode de comparaison de chaînes par défaut.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="9c8fa-142">Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Binary` et placez-la en haut du fichier source.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="9c8fa-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c8fa-143">Example</span></span>  
 <span data-ttu-id="9c8fa-144">L'exemple suivant utilise l'instruction `Option Compare` pour définir l'ordre de tri de texte sans respect de la casse comme méthode de comparaison de chaînes par défaut.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="9c8fa-145">Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Text` et placez-la en haut du fichier source.</span><span class="sxs-lookup"><span data-stu-id="9c8fa-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="9c8fa-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c8fa-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="9c8fa-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="9c8fa-147">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="9c8fa-148">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="9c8fa-148">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="9c8fa-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c8fa-149">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="9c8fa-150">Like, opérateur</span><span class="sxs-lookup"><span data-stu-id="9c8fa-150">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="9c8fa-151">Fonctions de chaîne</span><span class="sxs-lookup"><span data-stu-id="9c8fa-151">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="9c8fa-152">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="9c8fa-152">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="9c8fa-153">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="9c8fa-153">Option Strict Statement</span></span>](option-strict-statement.md)
