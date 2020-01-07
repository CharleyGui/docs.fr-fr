---
title: Comment implémenter explicitement des membres de deux interfaces C# -Guide de programmation
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 720e265cedcf9ad8be00f5e013365129f38749af
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635247"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Comment implémenter explicitement des membres de deux interfacesC# (Guide de programmation)
L’implémentation explicite d’une [interface](../../language-reference/keywords/interface.md) permet également au programmeur d’implémenter deux interfaces qui ont les mêmes noms de membres et donnent à chaque membre d’interface une implémentation distincte. L’exemple suivant affiche les dimensions d’une zone dans les unités de mesure à la fois métriques et britanniques. La [classe](../../language-reference/keywords/class.md) Box implémente deux interfaces, IEnglishDimensions et IMetricDimensions, qui représentent les différents systèmes de mesure. Les deux interfaces ont des noms de membres identiques, Length et Width.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si vous souhaitez utiliser par défaut les unités de mesure britanniques, implémentez les méthodes Length et Width normalement, puis implémentez explicitement les méthodes Length et Width à partir de l’interface IMetricDimensions :  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 Dans ce cas, vous pouvez accéder aux unités de mesure britanniques à partir de l’instance de classe et accéder aux unités métriques à partir de l’instance d’interface :  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Comment implémenter de manière explicite des membres d’interface](./how-to-explicitly-implement-interface-members.md)
