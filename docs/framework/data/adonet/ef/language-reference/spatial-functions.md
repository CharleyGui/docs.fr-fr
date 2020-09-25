---
title: Fonctions spatiales
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7d0979b5166c847244cbeec97acf4fa4f745a259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169581"
---
# <a name="spatial-functions"></a>Fonctions spatiales

Il n'existe aucun format littéral pour les types spatiaux. Toutefois, vous pouvez utiliser des fonctions canoniques Entity Framework que vous appelez à l'aide de chaînes au format texte connu. Par exemple, l'appel de fonction suivant crée un point géométrique :  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 Les <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> méthodes ont toutes les méthodes de Entity Framework canoniques spatiales. Cliquez sur une méthode qui vous intéresse pour afficher les paramètres qui doivent être passés à une fonction.
