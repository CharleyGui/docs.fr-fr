---
title: Interroger une collection d’objets (LINQ en C#)
description: Découvrez comment interroger des collections à l’aide de LINQ en C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659810"
---
# <a name="query-a-collection-of-objects"></a>Interroger une collection d’objets

Cet exemple montre comment effectuer une requête simple sur une liste d’objets `Student`. Chaque objet `Student` contient des informations de base sur l’étudiant et une liste qui représente les notes de l’étudiant lors de quatre examens.  
  
Cette application sert de cadre pour de nombreux autres exemples dans cette section qui utilisent la même source de données `students`.  
  
## <a name="example"></a> Exemple

La requête suivante retourne les étudiants qui ont reçu une note supérieure ou égale à 90 lors de leur premier examen.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Cette requête est volontairement simple pour vous permettre de faire des essais. Par exemple, vous pouvez essayer plus de conditions dans la clause `where` ou utiliser une clause `orderby` pour trier les résultats.  
  
## <a name="see-also"></a>Voir aussi

- [Requête intégrée linguistique (LINQ)](index.md)
- [Interpolation de chaîne](../language-reference/tokens/interpolated.md)
