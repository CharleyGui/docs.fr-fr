---
title: API qui s'appuient sur la réflexion
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181090"
---
# <a name="apis-that-rely-on-reflection"></a>API qui s'appuient sur la réflexion
Dans certains cas, l’utilisation de la réflexion dans le code n’est pas évidente, de sorte que la chaîne d’outils .NET Native ne conserve pas les métadonnées nécessaires au moment de l’exécution. Cette rubrique décrit certaines API courantes ou des modèles de programmation courants qui ne sont pas considérés comme faisant partie de l'API de réflexion, mais dont l'exécution s'appuie sur la réflexion. Si vous les utilisez dans votre code source, vous pouvez ajouter des informations les concernant au fichier de directives runtime (.rd.xml) pour que les appels de ces API ne lèvent pas d’exceptions, telles que [MissingMetadataException](missingmetadataexception-class-net-native.md), au moment de l’exécution.  
  
## <a name="typemakegenerictype-method"></a>Méthode Type.MakeGenericType  
 Vous pouvez instancier dynamiquement un type générique `AppClass<T>` en appelant la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> à l'aide d'un code tel que celui-ci :  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Pour que ce code s'exécute correctement, plusieurs éléments de métadonnées sont nécessaires. Le premier est constitué des métadonnées `Browse` pour le type générique non instancié, `AppClass<T>` :  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Il permet à l'appel de méthode <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> de réussir et de retourner un objet <xref:System.Type> valide.  
  
 Toutefois, même quand vous ajoutez des métadonnées pour le type générique non instancié, l’appel de la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> lève une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) :  
  
Impossible d’effectuer cette opération, car les métadonnées pour le type suivant ont été supprimées pour des raisons de performances :  
  
`App1.AppClass`1<System. Int32>».  
  
 Vous pouvez ajouter la directive runtime suivante au fichier de directives runtime pour ajouter des métadonnées `Activate` pour l'instanciation spécifique sur `AppClass<T>` de <xref:System.Int32?displayProperty=nameWithType> :  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 Chaque instanciation de `AppClass<T>` nécessite sa propre directive si elle est créée avec la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> et qu’elle n’est pas utilisée de manière statique.  
  
## <a name="methodinfomakegenericmethod-method"></a>Méthode MethodInfo.MakeGenericMethod  
 Dans le cas d'une classe `Class1` avec une méthode générique `GetMethod<T>(T t)`, `GetMethod` peut être appelée par réflexion à l'aide d'un code tel que celui-ci :  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Pour s'exécuter correctement, ce code nécessite plusieurs éléments de métadonnées :  
  
- Les métadonnées `Browse` pour le type dont vous souhaitez appeler la méthode.  
  
- Les métadonnées `Browse` pour la méthode que vous souhaitez appeler.  S'il s'agit d'une méthode publique, l'ajout de métadonnées `Browse` publiques pour le type conteneur comprend également la méthode.  
  
- Métadonnées dynamiques pour la méthode que vous souhaitez appeler, afin que le délégué d’appel de réflexion ne soit pas supprimé par la chaîne d’outils .NET Native. Si des métadonnées dynamiques sont manquantes pour la méthode, l'exception suivante est levée quand la méthode <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> est appelée :  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Les directives runtime suivantes garantissent que toutes les métadonnées nécessaires sont disponibles :  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 Une directive `MethodInstantiation` est obligatoire pour chaque instanciation différente de la méthode qui est appelée dynamiquement, et l'élément `Arguments` est mis à jour pour refléter chaque argument d'instanciation différent.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Méthodes Array.CreateInstance et Type.MakeTypeArray  
 L'exemple suivant appelle les méthodes <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> et <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> sur un type, `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Si aucune métadonnée de tableau n'est présente, l'erreur suivante se produit :  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 Les métadonnées `Browse` pour le type de tableau sont nécessaires à son instanciation de manière dynamique.  La directive runtime suivante permet l'instanciation dynamique de `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started-with-net-native.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
