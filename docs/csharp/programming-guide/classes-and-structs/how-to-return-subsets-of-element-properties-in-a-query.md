---
title: "Procédure : Retourner des sous-ensembles de propriétés d'éléments dans une requête - Guide de programmation C#"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: da4ecb11c51f42c2297b6d40ed9a963590b3f441
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599987"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Procédure : Retourner des sous-ensembles de propriétés d'éléments dans une requête (Guide de programmation C#)
Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s’appliquent :  
  
- Vous souhaitez retourner uniquement certaines propriétés de chaque élément source.  
  
- Vous n’avez pas besoin de stocker les résultats de requête en dehors de la portée de la méthode dans laquelle la requête est exécutée.  
  
 Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, vous pouvez utiliser l’opérateur point dans la clause `select`. Par exemple, pour retourner uniquement l’`ID` de chaque `student`, écrivez la clause `select` de la façon suivante :  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un type anonyme pour retourner uniquement un sous-ensemble des propriétés de chaque élément source qui répond à la condition spécifiée.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Notez que le type anonyme utilise les noms de l’élément source pour ses propriétés si aucun nom n’est spécifié. Pour attribuer de nouveaux noms aux propriétés du type anonyme, écrivez l’instruction `select` de la façon suivante :  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Si vous effectuez cette opération dans l’exemple précédent, l’instruction `Console.WriteLine` doit également changer :  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans Visual Studio. Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], et il comporte une référence à System.Core.dll et une directive `using` pour System.Linq. Si un ou plusieurs de ces éléments sont manquants dans le projet, vous pouvez les ajouter manuellement.   
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
