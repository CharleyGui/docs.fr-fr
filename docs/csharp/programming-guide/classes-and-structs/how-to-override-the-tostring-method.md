---
title: Comment substituer le Guide de programmation de C# la méthode ToString
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 3d5b63609ea61764d4042d534c40d8032fb82841
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970476"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Comment substituer la méthode ToString (C# Guide de programmation)

En C#, chaque classe ou struct hérite implicitement de la classe <xref:System.Object>. Ainsi, chaque objet en C# obtient la méthode <xref:System.Object.ToString%2A>, qui retourne une représentation sous forme de chaîne de cet objet. Par exemple, toutes les variables de type `int` ont une méthode `ToString`, ce qui leur permet de retourner leur contenu sous forme de chaîne :  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Quand vous créez une classe ou un struct personnalisé, vous devez substituer la méthode <xref:System.Object.ToString%2A> pour fournir des informations sur votre type au code client.  
  
 Pour plus d’informations sur l’utilisation de chaînes de format et d’autres types de mise en forme personnalisée avec la méthode `ToString`, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Quand vous choisissez les informations à fournir par l’intermédiaire de cette méthode, déterminez si votre classe ou struct sera utilisé par du code non fiable. Veillez à ne pas fournir d’informations susceptibles d’être exploitées par du code malveillant.  
  
Pour substituer la méthode `ToString` dans votre classe ou struct :
  
1. Déclarez une méthode `ToString` avec les modificateurs et le type de retour suivants :  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Implémentez la méthode pour qu’elle retourne une chaîne.  
  
     L’exemple suivant retourne le nom de la classe en plus des données propres à une instance particulière de la classe.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Vous pouvez tester la méthode `ToString` comme illustré dans l’exemple de code suivant :  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IFormattable>
- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Chaînes](../strings/index.md)
- [string](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Mise en forme des types](../../../standard/base-types/formatting-types.md)
