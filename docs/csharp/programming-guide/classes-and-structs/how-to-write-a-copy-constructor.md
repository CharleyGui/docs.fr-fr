---
title: 'Procédure : Écrire un constructeur de copie - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596605"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="4f4e8-102">Procédure : Écrire un constructeur de copie (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4f4e8-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="4f4e8-103">C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.</span><span class="sxs-lookup"><span data-stu-id="4f4e8-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f4e8-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="4f4e8-104">Example</span></span>  
 <span data-ttu-id="4f4e8-105">Dans l’exemple suivant, la `Person`[classe](../../language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="4f4e8-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="4f4e8-106">Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="4f4e8-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="4f4e8-107">Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="4f4e8-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="4f4e8-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f4e8-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="4f4e8-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4f4e8-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4f4e8-110">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="4f4e8-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="4f4e8-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="4f4e8-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="4f4e8-112">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="4f4e8-112">Finalizers</span></span>](./destructors.md)
