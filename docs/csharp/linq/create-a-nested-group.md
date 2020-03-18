---
title: Créer un groupe imbriqué (LINQ en C#)
description: Découvrez comment créer un groupe imbriqué dans une expression de requête LINQ en C#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688616"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="6f9b1-103">Créer un groupe imbriqué</span><span class="sxs-lookup"><span data-stu-id="6f9b1-103">Create a nested group</span></span>

<span data-ttu-id="6f9b1-104">L’exemple suivant montre comment créer des groupes imbriqués dans une expression de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="6f9b1-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="6f9b1-105">Chaque groupe créé en fonction de l’année/du niveau d’étude est ensuite encore subdivisé en groupes en fonction des noms des individus.</span><span class="sxs-lookup"><span data-stu-id="6f9b1-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="6f9b1-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="6f9b1-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="6f9b1-107">Cet exemple contient des références aux objets définis dans l’exemple de code qui est présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6f9b1-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="6f9b1-108">Notez que trois boucles `foreach` imbriquées sont nécessaires pour effectuer une itération sur les éléments internes d’un groupe imbriqué.</span><span class="sxs-lookup"><span data-stu-id="6f9b1-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f9b1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f9b1-109">See also</span></span>

- [<span data-ttu-id="6f9b1-110">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6f9b1-110">Language Integrated Query (LINQ)</span></span>](index.md)
