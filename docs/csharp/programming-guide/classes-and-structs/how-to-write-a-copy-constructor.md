---
title: Comment écrire un constructeur de copie (Guide de programmation C#)
description: Découvrez comment écrire un constructeur de copie en C# qui accepte une instance de la classe et retourne une nouvelle instance avec les valeurs de l’entrée.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 85899d2de05312be921199387cc1155fa8e9d2f1
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098981"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="ce521-103">Comment écrire un constructeur de copie (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ce521-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="ce521-104">C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.</span><span class="sxs-lookup"><span data-stu-id="ce521-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce521-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce521-105">Example</span></span>  

 <span data-ttu-id="ce521-106">Dans l’exemple suivant, la `Person`[classe](../../language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="ce521-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="ce521-107">Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="ce521-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="ce521-108">Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="ce521-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="ce521-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce521-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="ce521-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ce521-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce521-111">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="ce521-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="ce521-112">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="ce521-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="ce521-113">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="ce521-113">Finalizers</span></span>](./destructors.md)
