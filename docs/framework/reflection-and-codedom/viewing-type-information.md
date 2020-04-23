---
title: Affichage des informations de type
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
ms.openlocfilehash: bf119ff547df59cd369d688fd81ab058893614f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130014"
---
# <a name="viewing-type-information"></a>Affichage des informations de type
La classe <xref:System.Type?displayProperty=nameWithType> est un élément central de la réflexion. Le common language runtime crée l’objet **Type** pour un type chargé quand la réflexion le demande. Vous pouvez utiliser les méthodes, les champs, les propriétés et les classes imbriquées d’un objet **Type** pour connaître toutes les informations le concernant.  
  
 Utilisez <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> pour obtenir les objets **Type** des assemblys n’ayant pas été chargés, en passant le nom du ou des types souhaités. Utilisez <xref:System.Type.GetType%2A?displayProperty=nameWithType> pour obtenir les objets **Type** d’un assembly déjà chargé. Utilisez <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> et <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> pour obtenir les objets **Type** d’un module.  
  
> [!NOTE]
> Si vous souhaitez examiner et manipuler des méthodes et des types génériques, consultez les informations supplémentaires fournies dans [Réflexion et types génériques](reflection-and-generic-types.md) et [Guide pratique pour examiner et instancier des types génériques avec la réflexion](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 L’exemple suivant montre la syntaxe nécessaire pour obtenir l’objet <xref:System.Reflection.Assembly> et le module d’un assembly.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 L’exemple suivant montre comment obtenir les objets **Type** d’un assembly chargé.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Une fois que vous avez obtenu l’objet **Type**, vous pouvez découvrir les informations relatives aux membres de ce type de nombreuses manières. Par exemple, vous pouvez rechercher des informations sur tous les membres du type en appelant la méthode <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>, qui obtient un tableau d’objets <xref:System.Reflection.MemberInfo> décrivant chaque membre du type actuel.  
  
 Vous pouvez également utiliser des méthodes sur la classe **Type** pour récupérer des informations sur un ou plusieurs constructeurs, méthodes, événements, champs ou propriétés que vous spécifiez par nom. Par exemple, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsule un constructeur spécifique de la classe active.  
  
 Si vous avez un **Type**, vous pouvez utiliser la propriété <xref:System.Type.Module%2A?displayProperty=nameWithType> pour obtenir un objet qui encapsule le module contenant ce type. Utilisez la propriété <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> pour localiser un objet qui encapsule l’assembly contenant le module. Vous pouvez obtenir directement l’assembly qui encapsule le type en utilisant la propriété <xref:System.Type.Assembly%2A?displayProperty=nameWithType>.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type et ConstructorInfo  
 L’exemple suivant montre comment lister les constructeurs d’une classe, dans le cas présent, la classe <xref:System.String>.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo et PropertyInfo  
 Obtenez des informations sur les méthodes, propriétés, événements et champs d’un type à l’aide des objets <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo> et <xref:System.Reflection.PropertyInfo>.  
  
 L’exemple suivant utilise **MemberInfo** pour lister le nombre de membres de la classe **System.IO.File** et la propriété <xref:System.Type.IsPublic%2A> pour déterminer la visibilité de la classe.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 L’exemple suivant examine le type du membre spécifié. Il effectue une réflexion sur un membre de la classe **MemberInfo**, puis affiche son type.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 L’exemple suivant utilise toutes les classes d' ** \*informations** de réflexion <xref:System.Reflection.BindingFlags> avec pour répertorier tous les membres (constructeurs, champs, propriétés, événements et méthodes) de la classe spécifiée, en divisant les membres en catégories statiques et d’instance.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [Réflexion et types génériques](reflection-and-generic-types.md)
