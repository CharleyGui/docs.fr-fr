---
title: Comment retourner des sous-ensembles de propriétés d’éléments dans une requête (Guide de programmation C#)
description: Découvrez comment utiliser un type anonyme dans une expression de requête en C# pour retourner certaines des propriétés de chaque élément source.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 5784d6a288af374d357346e32535ebe9c1877bcc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512793"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Comment retourner des sous-ensembles de propriétés d’éléments dans une requête (Guide de programmation C#)

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

- [Guide de programmation C#](../index.md)
- [Types anonymes](./anonymous-types.md)
- [LINQ en C#](../../linq/index.md)
