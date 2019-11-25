---
title: Guide pratique pour écrire un constructeur de C# copie-Guide de programmation
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 4ac7ccb55775019eb86d5345797d2fd74d3b9527
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970388"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="93830-102">Comment écrire un constructeur de copie (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="93830-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="93830-103">C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.</span><span class="sxs-lookup"><span data-stu-id="93830-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93830-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="93830-104">Example</span></span>  
 <span data-ttu-id="93830-105">Dans l’exemple suivant, la `Person`[classe](../../language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="93830-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="93830-106">Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="93830-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="93830-107">Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="93830-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="93830-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93830-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="93830-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="93830-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="93830-110">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="93830-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="93830-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="93830-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="93830-112">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="93830-112">Finalizers</span></span>](./destructors.md)
