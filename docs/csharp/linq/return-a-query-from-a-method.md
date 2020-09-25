---
title: Retourner une requête à partir d’une méthode
description: Comment retourner une requête.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 646e771d637aa242231e3fe216d4a856bb156649
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203330"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Comment retourner une requête à partir d’une méthode (Guide de programmation C#)

Cet exemple montre comment retourner une requête à partir d’une méthode en tant que valeur de retour et en tant que paramètre `out`.  
  
 Les objets de requête sont composables, ce qui signifie que vous pouvez retourner une requête à partir d’une méthode. Les objets qui représentent des requêtes ne stockent pas la collection résultante, mais plutôt les étapes pour générer les résultats lorsque cela est nécessaire. L’avantage de retourner des objets de requête à partir de méthodes est qu’il est possible de les composer ou modifier encore. Par conséquent, toute valeur de retour ou paramètre `out` d’une méthode qui retourne une requête doit également avoir ce type. Si une méthode matérialise une requête en un type <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concret, elle est considérée comme retournant les résultats de la requête plutôt que la requête elle-même. Une variable de requête retournée à partir d’une méthode peut encore être composée ou modifiée.  
  
## <a name="example"></a>Exemple  

 Dans l’exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out`. Notez que, dans les deux cas, une requête est retournée et non pas les résultats d’une requête.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query)](index.md)
