---
title: 'Comment : effectuer une recherche dans une chaîne-Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700060"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="e2803-102">Procédure : effectuer une recherche dans une chaîne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2803-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="e2803-103">Cet article montre un exemple de recherche dans une chaîne dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e2803-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="e2803-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2803-104">Example</span></span>

<span data-ttu-id="e2803-105">Cet exemple appelle la méthode <xref:System.String.IndexOf%2A> sur un objet <xref:System.String> pour signaler l’index de la première occurrence d’une sous-chaîne :</span><span class="sxs-lookup"><span data-stu-id="e2803-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="e2803-106">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e2803-106">Robust programming</span></span>

<span data-ttu-id="e2803-107">La méthode <xref:System.String.IndexOf%2A> retourne l’emplacement du premier caractère de la première occurrence de la sous-chaîne.</span><span class="sxs-lookup"><span data-stu-id="e2803-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="e2803-108">L’index est basé sur 0, ce qui signifie que le premier caractère d’une chaîne a un index égal à 0.</span><span class="sxs-lookup"><span data-stu-id="e2803-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="e2803-109">Si <xref:System.String.IndexOf%2A> ne trouve pas la sous-chaîne, elle retourne-1.</span><span class="sxs-lookup"><span data-stu-id="e2803-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="e2803-110">La méthode <xref:System.String.IndexOf%2A> est sensible à la casse et utilise la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="e2803-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="e2803-111">Pour un contrôle optimal des erreurs, vous souhaiterez peut-être encadrer la recherche de chaîne dans le bloc `Try` d’un bloc [try... Catch... Finalisation](../../../language-reference/statements/try-catch-finally-statement.md) de la construction de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="e2803-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2803-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2803-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="e2803-113">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="e2803-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="e2803-114">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2803-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="e2803-115">Chaînes</span><span class="sxs-lookup"><span data-stu-id="e2803-115">Strings</span></span>](index.md)
