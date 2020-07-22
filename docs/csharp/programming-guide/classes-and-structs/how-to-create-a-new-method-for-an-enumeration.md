---
title: Comment créer une nouvelle méthode pour une énumération-Guide de programmation C#
description: Découvrez comment utiliser des méthodes d’extension pour ajouter des fonctionnalités à une énumération en C#. Cet exemple montre une méthode d’extension appelée passing pour un enum appelé grades.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864486"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="1a16f-104">Comment créer une nouvelle méthode pour une énumération (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1a16f-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="1a16f-105">Vous pouvez utiliser des méthodes d’extension pour ajouter des fonctionnalités propres à un type enum particulier.</span><span class="sxs-lookup"><span data-stu-id="1a16f-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a16f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a16f-106">Example</span></span>  
 <span data-ttu-id="1a16f-107">Dans l’exemple suivant, l’énumération `Grades` représente les notes qu’un étudiant peut obtenir dans une classe.</span><span class="sxs-lookup"><span data-stu-id="1a16f-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="1a16f-108">Une méthode d’extension nommée `Passing` est ajoutée au type `Grades` pour que chaque instance de ce type « sache » maintenant si elle représente une note au-dessus de la moyenne.</span><span class="sxs-lookup"><span data-stu-id="1a16f-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="1a16f-109">Notez que la classe `Extensions` contient également une variable statique qui est mise à jour de manière dynamique, et que la valeur de retour de la méthode d’extension reflète la valeur actuelle de cette variable.</span><span class="sxs-lookup"><span data-stu-id="1a16f-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="1a16f-110">Cela démontre que, dans les coulisses, les méthodes d’extension sont appelées directement sur la classe statique dans laquelle elles sont définies.</span><span class="sxs-lookup"><span data-stu-id="1a16f-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a16f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a16f-111">See also</span></span>

- [<span data-ttu-id="1a16f-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1a16f-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a16f-113">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="1a16f-113">Extension Methods</span></span>](./extension-methods.md)
