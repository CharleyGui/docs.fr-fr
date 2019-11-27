---
title: 'Comment : accéder aux caractères dans les chaînes'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352462"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="9885f-102">Comment : accéder aux caractères dans les chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9885f-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="9885f-103">Cet exemple montre comment utiliser la propriété <xref:System.String.Chars%2A> pour accéder au caractère à l’emplacement spécifié dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9885f-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9885f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9885f-104">Example</span></span>  
 <span data-ttu-id="9885f-105">Il est parfois utile d’avoir des données sur les caractères de votre chaîne et les positions de ces caractères dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="9885f-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="9885f-106">Vous pouvez considérer une chaîne comme un tableau de caractères (instances`Char`); vous pouvez récupérer un caractère particulier en référençant l’index de ce caractère via la propriété <xref:System.String.Chars%2A>.</span><span class="sxs-lookup"><span data-stu-id="9885f-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="9885f-107">Le paramètre `index` de la propriété <xref:System.String.Chars%2A> est de base zéro.</span><span class="sxs-lookup"><span data-stu-id="9885f-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9885f-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="9885f-108">Robust Programming</span></span>  
 <span data-ttu-id="9885f-109">La propriété <xref:System.String.Chars%2A> retourne le caractère à la position spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9885f-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="9885f-110">Toutefois, certains caractères Unicode peuvent être représentés par plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="9885f-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="9885f-111">Pour plus d’informations sur l’utilisation des caractères Unicode, consultez [Comment : convertir une chaîne en tableau de caractères](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="9885f-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="9885f-112">La propriété <xref:System.String.Chars%2A> lève une exception <xref:System.IndexOutOfRangeException> si le paramètre `index` est supérieur ou égal à la longueur de la chaîne, ou s’il est inférieur à zéro</span><span class="sxs-lookup"><span data-stu-id="9885f-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9885f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9885f-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="9885f-114">Guide pratique : convertir une chaîne en tableau de caractères</span><span class="sxs-lookup"><span data-stu-id="9885f-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="9885f-115">Conversion entre chaînes et d’autres types de données en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9885f-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="9885f-116">Chaînes</span><span class="sxs-lookup"><span data-stu-id="9885f-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
