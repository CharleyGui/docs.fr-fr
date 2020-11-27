---
title: Guide pratique pour examiner et instancier des types génériques avec la réflexion
description: Consultez Comment examiner et instancier des types génériques avec la réflexion. Utilisez les propriétés IsGenericType, IsGenericParameter et GenericParameterPosition.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: 34efca4a26b0ab3739d19b793237532ec9f4f15e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263436"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Guide pratique pour examiner et instancier des types génériques avec la réflexion

Les informations sur les types génériques s’obtiennent de la même façon que les informations sur les autres types : en examinant un objet <xref:System.Type> qui représente le type générique. La principale différence est qu’un type générique a une liste d’objets <xref:System.Type> représentant ses paramètres de type générique. La première procédure de cette section examine les types génériques.  
  
 Vous pouvez créer un objet <xref:System.Type> qui représente un type construit en liant des arguments de type aux paramètres de type d’une définition de type générique. Ceci est illustrée par la deuxième procédure.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Pour examiner un type générique et ses paramètres de type  
  
1. Obtenez une instance de <xref:System.Type> qui représente le type générique. Dans le code suivant, le type est obtenu à l’aide de l’opérateur C# `typeof` (`GetType` en Visual Basic, `typeid` en Visual C++). Pour découvrir d’autres méthodes d’obtention d’un objet <xref:System.Type>, consultez la rubrique de la classe <xref:System.Type>. Notez que dans le reste de cette procédure, le type est contenu dans un paramètre de méthode nommé `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Utilisez la propriété <xref:System.Type.IsGenericType%2A> pour déterminer si le type est générique, et utilisez la propriété <xref:System.Type.IsGenericTypeDefinition%2A> pour déterminer si le type est une définition de type générique.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Obtenez un tableau qui contient les arguments de type générique, à l’aide de la méthode <xref:System.Type.GetGenericArguments%2A>.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Pour chaque argument de type, déterminez s’il s’agit d’un paramètre de type (par exemple, dans une définition de type générique) ou d’un type qui a été spécifié pour un paramètre de type (par exemple, dans un type construit), à l’aide de la propriété <xref:System.Type.IsGenericParameter%2A>.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. Dans le système de type, un paramètre de type générique est représenté par une instance de <xref:System.Type>, tout comme les types ordinaires. Le code suivant affiche le nom et la position du paramètre d’un objet <xref:System.Type> qui représente un paramètre de type générique. La position di paramètre est ici sans importance. Elle est plus utile quand vous examinez un paramètre de type qui a été utilisé comme argument de type d’un autre type générique.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Déterminez la contrainte de type de base et les contraintes d’interface d’un paramètre de type générique en utilisant la méthode <xref:System.Type.GetGenericParameterConstraints%2A> pour obtenir toutes les contraintes dans un seul tableau. L’ordre des contraintes n’est pas garanti.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Utilisez la propriété <xref:System.Type.GenericParameterAttributes%2A> pour découvrir les contraintes spéciales d’un paramètre de type, telles que l’obligation d’être un type référence. La propriété inclut également des valeurs qui représentent la variance, que vous pouvez masquer comme indiqué dans le code suivant.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Les attributs de contrainte spéciales sont des indicateurs, et l’indicateur (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) qui ne représente aucune contrainte spéciale représente également aucune covariance ou contravariance. Ainsi, pour tester l’une de ces conditions, vous devez utiliser le masque approprié. Dans ce cas, utilisez <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> pour isoler les indicateurs de contraintes spéciales.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Construction d’une instance d’un type générique  

 Un type générique est comme un modèle. Vous ne pouvez pas créer des instances de ce type, sauf si vous spécifiez des types réels pour ses paramètres de type générique. Effectuer cela au moment de l’exécution à l’aide de la réflexion nécessite la méthode <xref:System.Type.MakeGenericType%2A>.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Pour construire une instance d’un type générique  
  
1. Obtenez un objet <xref:System.Type> qui représente le type générique. Le code suivant obtient le type générique <xref:System.Collections.Generic.Dictionary%602> de deux manières différentes : en utilisant la surcharge de méthode <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> avec une chaîne qui décrit le type, et en appelant la méthode <xref:System.Type.GetGenericTypeDefinition%2A> sur le type construit `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` en Visual Basic). La méthode <xref:System.Type.MakeGenericType%2A> nécessite une définition de type générique.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Créez un tableau d’arguments de type pour remplacer les paramètres de type. Le tableau doit contenir le nombre correct d’objets <xref:System.Type>, dans l’ordre où ils apparaissent dans la liste de paramètres de type. Dans ce cas, la clé (premier paramètre de type) est de type <xref:System.String>, et les valeurs dans le dictionnaire sont des instances d’une classe nommée `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Appelez la méthode <xref:System.Type.MakeGenericType%2A> pour lier les arguments de type aux paramètres de type et construire le type.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Utilisez la surcharge de méthode <xref:System.Activator.CreateInstance%28System.Type%29> pour créer un objet du type construit. Le code suivant stocke deux instances de la classe `Example` dans l’objet `Dictionary<String, Example>` obtenu.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a> Exemple  

 L’exemple de code suivant définit une méthode `DisplayGenericType` pour examiner les définitions de type générique et les types construits utilisés dans le code, et pour afficher leurs informations. La méthode `DisplayGenericType` montre comment utiliser les propriétés <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A> et <xref:System.Type.GenericParameterPosition%2A>, et la méthode <xref:System.Type.GetGenericArguments%2A>.  
  
 L’exemple définit également une méthode `DisplayGenericParameter` pour examiner un paramètre de type générique et afficher ses contraintes.  
  
 L’exemple de code définit un ensemble de types de test, notamment un type générique qui illustre des contraintes de paramètre de type, et montre comment afficher des informations sur ces types.  
  
 L’exemple construit un type à partir de la classe <xref:System.Collections.Generic.Dictionary%602> en créant un tableau d’arguments de type et en appelant la méthode <xref:System.Type.MakeGenericType%2A>. Le programme compare l’objet <xref:System.Type> construit à l’aide de <xref:System.Type.MakeGenericType%2A> avec un objet <xref:System.Type> obtenu à l’aide de `typeof` (`GetType` en Visual Basic), et démontre qu’ils sont identiques. De même, le programme utilise la méthode <xref:System.Type.GetGenericTypeDefinition%2A> pour obtenir la définition de type générique du type construit, et la compare à l’objet <xref:System.Type> représentant la classe <xref:System.Collections.Generic.Dictionary%602>.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Réflexion et types génériques](reflection-and-generic-types.md)
- [Affichage des informations de type](viewing-type-information.md)
- [Génériques](../../standard/generics/index.md)
