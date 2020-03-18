---
title: Comment créer une nouvelle méthode pour un recensement - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705650"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="f0ac8-102">Comment créer une nouvelle méthode de recensement (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="f0ac8-102">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="f0ac8-103">Vous pouvez utiliser des méthodes d’extension pour ajouter des fonctionnalités propres à un type enum particulier.</span><span class="sxs-lookup"><span data-stu-id="f0ac8-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0ac8-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f0ac8-104">Example</span></span>  
 <span data-ttu-id="f0ac8-105">Dans l’exemple suivant, l’énumération `Grades` représente les notes qu’un étudiant peut obtenir dans une classe.</span><span class="sxs-lookup"><span data-stu-id="f0ac8-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="f0ac8-106">Une méthode d’extension nommée `Passing` est ajoutée au type `Grades` pour que chaque instance de ce type « sache » maintenant si elle représente une note au-dessus de la moyenne.</span><span class="sxs-lookup"><span data-stu-id="f0ac8-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="f0ac8-107">Notez que la classe `Extensions` contient également une variable statique qui est mise à jour de manière dynamique, et que la valeur de retour de la méthode d’extension reflète la valeur actuelle de cette variable.</span><span class="sxs-lookup"><span data-stu-id="f0ac8-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="f0ac8-108">Cela démontre que, dans les coulisses, les méthodes d’extension sont appelées directement sur la classe statique dans laquelle elles sont définies.</span><span class="sxs-lookup"><span data-stu-id="f0ac8-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ac8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0ac8-109">See also</span></span>

- [<span data-ttu-id="f0ac8-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f0ac8-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f0ac8-111">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="f0ac8-111">Extension Methods</span></span>](./extension-methods.md)
