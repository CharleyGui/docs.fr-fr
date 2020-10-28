---
title: Récupération des informations stockées dans les attributs
description: Apprenez à récupérer des informations stockées dans des attributs, par exemple pour une instance d’attribut, de nombreuses instances pour la même portée, & de nombreuses instances pour différentes étendues.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
ms.openlocfilehash: 710f3e3d1051bad4a61e59e330204d622b9fd683
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889203"
---
# <a name="retrieving-information-stored-in-attributes"></a>Récupération des informations stockées dans les attributs
La récupération d’un attribut personnalisé est un processus simple. Tout d’abord, déclarez une instance de l’attribut que vous souhaitez récupérer. Ensuite, utilisez la méthode <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> pour initialiser le nouvel attribut à la valeur de l’attribut que vous souhaitez récupérer. Une fois le nouvel attribut initialisé, vous utilisez simplement ses propriétés pour obtenir les valeurs.  
  
> [!IMPORTANT]
> Cette rubrique explique comment récupérer des attributs pour le code chargé dans le contexte d'exécution. Pour récupérer les attributs du code chargé dans le contexte de réflexion uniquement, vous devez utiliser la classe <xref:System.Reflection.CustomAttributeData>, comme indiqué dans [Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Cette section décrit les méthodes suivantes pour récupérer des attributs :  
  
- [Récupération d’une seule instance d’un attribut](#cpconretrievingsingleinstanceofattribute)  
  
- [Récupération de plusieurs instances d’un attribut appliqué à la même étendue](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Récupération de plusieurs instances d’un attribut appliqué à différentes portées](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Récupération d’une seule instance d’un attribut  
 Dans l’exemple suivant, la méthode `DeveloperAttribute` (décrite dans la section précédente) est appliquée à la classe `MainApp` au niveau de la classe. La méthode `GetAttribute` utilise **GetCustomAttribute** pour récupérer les valeurs stockées dans `DeveloperAttribute` au niveau de la classe avant de les afficher dans la console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Lorsqu’il est exécuté, ce programme affiche le texte suivant.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Si l’attribut est introuvable, la méthode **GetCustomAttribute** initialise `MyAttribute` à une valeur null. Cet exemple recherche une telle instance dans `MyAttribute` et avertit l’utilisateur si aucun attribut n’est trouvé. Si aucune valeur `DeveloperAttribute` n’est trouvée dans l’étendue de la classe, le message suivant s’affiche dans la console.  
  
```console  
The attribute was not found.
```  
  
 Cet exemple suppose que l’attribut est défini dans l’espace de noms actuel. N’oubliez pas d’importer l’espace de noms dans lequel se trouve la définition de l’attribut si celle-ci ne figure pas dans l’espace de noms actuel.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Récupération de plusieurs instances d’un attribut appliqué à la même étendue  
 Dans l’exemple précédent, la classe à inspecter et l’attribut spécifique à rechercher sont transmis à <xref:System.Attribute.GetCustomAttribute%2A>. Ce code fonctionne correctement uniquement si une instance d’un attribut est appliquée au niveau de la classe. Toutefois, si plusieurs instances d’un attribut sont appliquées au niveau de la même classe, la méthode **GetCustomAttribute** ne récupère pas toutes les informations. Dans les cas où plusieurs instances du même attribut sont appliquées à la même étendue, vous pouvez utiliser <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> pour placer toutes les instances d’un attribut dans un tableau. Par exemple, si deux instances de `DeveloperAttribute` sont appliquées au niveau de la même classe, la méthode `GetAttribute` peut être modifiée pour afficher les informations trouvées dans les deux attributs. N’oubliez pas que pour appliquer plusieurs attributs au même niveau, l’attribut doit être défini avec la propriété **AllowMultiple** définie sur **true** dans <xref:System.AttributeUsageAttribute>.  
  
 L’exemple de code suivant montre comment utiliser la méthode **GetCustomAttributes** pour créer un tableau qui référence toutes les instances de `DeveloperAttribute` dans une classe donnée. Les valeurs de tous les attributs sont ensuite affichées dans la console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Si aucun attribut n’est trouvé, ce code avertit l’utilisateur. Sinon, les informations contenues dans les deux instances de `DeveloperAttribute` s’affichent.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Récupération de plusieurs instances d’un attribut appliqué à différentes étendues  
 Les méthodes <xref:System.Attribute.GetCustomAttributes%2A> et <xref:System.Attribute.GetCustomAttribute%2A> ne recherchent pas une classe entière et retournent toutes les instances d’un attribut dans cette classe. Elles recherchent plutôt une seule méthode spécifiée ou un membre à la fois. Si vous utilisez une classe avec le même attribut appliqué à chaque membre et que vous souhaitez récupérer les valeurs de tous les attributs appliqués à ces membres, vous devez fournir chaque méthode ou membre individuellement à **GetCustomAttributes** et à **GetCustomAttribute** .  
  
 L’exemple de code suivant prend une classe en tant que paramètre et recherche l’attribut `DeveloperAttribute` (défini précédemment) au niveau de la classe et dans chaque méthode individuelle de cette classe.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Si aucune instance de l’attribut `DeveloperAttribute` n’est trouvée au niveau de la méthode ou de la classe, la méthode `GetAttribute` avertit l’utilisateur qu’aucun attribut n’a été trouvé puis affiche le nom de la méthode ou classe qui ne contient pas cet attribut. Si un attribut est trouvé, les champs `Name`, `Level` et `Reviewed` apparaissent dans la console.  
  
 Vous pouvez utiliser les membres de la classe <xref:System.Type> pour obtenir les méthodes individuelles et les membres de la classe transmise. Cet exemple interroge d’abord l’objet **Type** pour obtenir des informations sur les attributs au niveau de la classe. Puis il utilise <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> pour placer des instances de toutes les méthodes dans un tableau d’objets <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> pour récupérer des informations sur les attributs au niveau de la méthode. Vous pouvez également utiliser la méthode <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> pour vérifier les attributs au niveau de la propriété, ou <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> pour vérifier les attributs au niveau du constructeur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Attributs](index.md)
