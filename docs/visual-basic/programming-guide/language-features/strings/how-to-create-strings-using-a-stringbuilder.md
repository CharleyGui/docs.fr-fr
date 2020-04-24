---
title: 'Comment : créer des cordes à l’aide d’un StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645324"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="69fae-102">Comment : créer des cordes à l’aide d’un StringBuilder dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69fae-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="69fae-103">Cet exemple construit une longue chaîne à <xref:System.Text.StringBuilder> partir de nombreuses chaînes plus petites en utilisant la classe.</span><span class="sxs-lookup"><span data-stu-id="69fae-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="69fae-104">La <xref:System.Text.StringBuilder> classe est plus `&=` efficace que l’opérateur pour concatenating de nombreuses chaînes.</span><span class="sxs-lookup"><span data-stu-id="69fae-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="69fae-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="69fae-105">Example</span></span>

<span data-ttu-id="69fae-106">L’exemple suivant crée <xref:System.Text.StringBuilder> une instance de la classe, annexe 1 000 cordes à cette instance, puis retourne sa représentation des cordes :</span><span class="sxs-lookup"><span data-stu-id="69fae-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="69fae-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69fae-107">See also</span></span>

- [<span data-ttu-id="69fae-108">Utilisation de la classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="69fae-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="69fae-109">&et opérateur</span><span class="sxs-lookup"><span data-stu-id="69fae-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="69fae-110">Chaînes</span><span class="sxs-lookup"><span data-stu-id="69fae-110">Strings</span></span>](index.md)
- [<span data-ttu-id="69fae-111">Création de chaînes</span><span class="sxs-lookup"><span data-stu-id="69fae-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="69fae-112">Manipulation de chaînes</span><span class="sxs-lookup"><span data-stu-id="69fae-112">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
