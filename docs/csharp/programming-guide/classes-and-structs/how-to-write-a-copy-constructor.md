---
title: Comment rédiger un constructeur de copie - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714850"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="9337a-102">Comment écrire un constructeur de copie (Guide de programmation de C)</span><span class="sxs-lookup"><span data-stu-id="9337a-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="9337a-103">C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.</span><span class="sxs-lookup"><span data-stu-id="9337a-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9337a-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9337a-104">Example</span></span>  
 <span data-ttu-id="9337a-105">Dans l’exemple suivant, la `Person`[classe](../../language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="9337a-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="9337a-106">Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="9337a-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="9337a-107">Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="9337a-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="9337a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9337a-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="9337a-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9337a-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9337a-110">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="9337a-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9337a-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9337a-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="9337a-112">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="9337a-112">Finalizers</span></span>](./destructors.md)
