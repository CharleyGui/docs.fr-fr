---
title: Comment retourner des sous-ensembles de propriétés d’élément dans un C# Guide de programmation de requêtes
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714856"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Comment retourner des sous-ensembles de propriétés d’éléments dans uneC# requête (Guide de programmation)
Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s’appliquent :  
  
- Vous souhaitez retourner uniquement certaines propriétés de chaque élément source.  
  
- Vous n’avez pas besoin de stocker les résultats de requête en dehors de la portée de la méthode dans laquelle la requête est exécutée.  
  
 Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, vous pouvez utiliser l’opérateur point dans la clause `select`. Par exemple, pour retourner uniquement l’`ID` de chaque `student`, écrivez la clause `select` de la façon suivante :  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un type anonyme pour retourner uniquement un sous-ensemble des propriétés de chaque élément source qui répond à la condition spécifiée.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Notez que le type anonyme utilise les noms de l’élément source pour ses propriétés si aucun nom n’est spécifié. Pour attribuer de nouveaux noms aux propriétés du type anonyme, écrivez l’instruction `select` de la façon suivante :  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Si vous effectuez cette opération dans l’exemple précédent, l’instruction `Console.WriteLine` doit également changer :  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
Pour exécuter ce code, copiez et collez la classe dans une application console C# avec une directive `using` pour System.Linq.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Types anonymes](./anonymous-types.md)
- [LINQ en C#](../../linq/index.md)
