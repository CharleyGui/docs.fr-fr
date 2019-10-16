---
title: Fonctions spatiales
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: eba384e77389f82006479f165178e80fcac244b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319298"
---
# <a name="spatial-functions"></a><span data-ttu-id="288f9-102">Fonctions spatiales</span><span class="sxs-lookup"><span data-stu-id="288f9-102">Spatial Functions</span></span>
<span data-ttu-id="288f9-103">Il n'existe aucun format littéral pour les types spatiaux.</span><span class="sxs-lookup"><span data-stu-id="288f9-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="288f9-104">Toutefois, vous pouvez utiliser des fonctions canoniques Entity Framework que vous appelez à l'aide de chaînes au format texte connu.</span><span class="sxs-lookup"><span data-stu-id="288f9-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="288f9-105">Par exemple, l'appel de fonction suivant crée un point géométrique :</span><span class="sxs-lookup"><span data-stu-id="288f9-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="288f9-106">Les méthodes <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> ont toutes les méthodes de Entity Framework canoniques spatiales.</span><span class="sxs-lookup"><span data-stu-id="288f9-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="288f9-107">Cliquez sur une méthode qui vous intéresse pour afficher les paramètres qui doivent être passés à une fonction.</span><span class="sxs-lookup"><span data-stu-id="288f9-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
