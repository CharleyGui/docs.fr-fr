---
title: Manipulations de chaînes de base dans .NET
description: Consultez un exemple qui appelle plusieurs méthodes de chaîne.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: cc04f0c874b732668b4813f8325bd7060927f22a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889125"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="7df15-103">Guide pratique pour effectuer des manipulations de chaînes de base dans .NET</span><span class="sxs-lookup"><span data-stu-id="7df15-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="7df15-104">L’exemple suivant utilise certaines des méthodes décrites dans les rubriques [Opérations de chaînes de base](basic-string-operations.md) pour construire une classe qui effectue des manipulations de chaînes éventuellement comme dans une application réelle.</span><span class="sxs-lookup"><span data-stu-id="7df15-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="7df15-105">La classe `MailToData` stocke le nom et l’adresse d’une personne dans des propriétés séparées et fournit un moyen de combiner les champs `City`, `State` et `Zip` dans une seule chaîne à montrer à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7df15-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="7df15-106">De plus, la classe permet à l’utilisateur d’entrer la ville, l’état et le code postal dans une chaîne unique ; l’application analyse automatiquement la chaîne unique et entre les informations appropriées dans la propriété correspondante.</span><span class="sxs-lookup"><span data-stu-id="7df15-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="7df15-107">Pour plus de simplicité, cet exemple utilise une application console avec une interface de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7df15-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7df15-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="7df15-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="7df15-109">Lorsque le code précédent est exécuté, l’utilisateur est invité à entrer son nom et son adresse.</span><span class="sxs-lookup"><span data-stu-id="7df15-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="7df15-110">L’application place les informations dans les propriétés appropriées et les montre à l’utilisateur, en créant une chaîne unique qui affiche la ville, l’état et le code postal.</span><span class="sxs-lookup"><span data-stu-id="7df15-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df15-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7df15-111">See also</span></span>

- [<span data-ttu-id="7df15-112">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="7df15-112">Basic String Operations</span></span>](basic-string-operations.md)
