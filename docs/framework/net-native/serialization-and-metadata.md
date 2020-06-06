---
title: Sérialisation et métadonnées
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: cc9adf0e6627ef3190e74fea5d4f0f3afd581811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81389229"
---
# <a name="serialization-and-metadata"></a>Sérialisation et métadonnées

Si votre application sérialise et désérialise des objets, vous devrez peut-être ajouter des entrées à votre fichier de directives runtime (.rd.xml) pour que les métadonnées nécessaires soient présentes au moment de l'exécution. Il existe deux catégories de sérialiseurs et chacune nécessite un traitement différent dans votre fichier de directives runtime :  
  
- Sérialiseurs tiers basés sur la réflexion. Ils nécessitent des modifications dans votre fichier de directives runtime et sont décrits dans la section suivante.  
  
- Sérialiseurs non basés sur la réflexion trouvés dans la bibliothèque de classes .NET Framework. Ceux-ci peuvent nécessiter des modifications dans votre fichier de directives runtime et sont décrits dans la section [Sérialiseurs Microsoft](#Microsoft).  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Sérialiseurs tiers

 Les sérialiseurs tiers, y compris Newtonsoft.JSON, sont généralement basés sur la réflexion. Avec un objet BLOB (Binary Large Object) de données sérialisées, les champs de données sont affectés à un type concret en fonction des noms des champs du type cible. L’utilisation de ces bibliothèques entraîne au minimum des exceptions [MissingMetadataException](missingmetadataexception-class-net-native.md) pour chaque objet <xref:System.Type> que vous essayez de sérialiser ou de désérialiser dans une collection `List<Type>`.  
  
 La façon la plus simple de résoudre les problèmes causés par les métadonnées manquantes pour ces sérialiseurs consiste à collecter les types qui seront utilisés dans la sérialisation dans un espace de noms unique (tel que `App.Models`) et à lui appliquer une directive de métadonnées `Serialize` :  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Pour plus d’informations sur la syntaxe utilisée dans l’exemple, consultez [ \<Namespace> élément](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Sérialiseurs Microsoft

 Bien que les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et <xref:System.Xml.Serialization.XmlSerializer> ne reposent pas sur la réflexion, elles nécessitent la génération de code en fonction de l'objet à sérialiser ou à désérialiser. Les constructeurs surchargés pour chaque sérialiseur incluent un paramètre <xref:System.Type> qui spécifie le type à sérialiser ou à désérialiser. La façon dont vous spécifiez ce type dans votre code définit l'action à entreprendre, comme indiqué dans les deux sections suivantes.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof utilisé dans le constructeur

 Si vous appelez un constructeur de ces classes de sérialisation et incluez l’opérateur C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) dans l’appel de méthode, **vous n’avez pas à effectuer d’autres tâches**. Par exemple, dans chacun des appels suivants d'un constructeur de classe de sérialisation, le mot clé `typeof` est utilisé dans le cadre de l'expression passée au constructeur.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Le compilateur .NET Native gère automatiquement ce code.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof utilisé à l'extérieur du constructeur

 Si vous appelez un constructeur de ces classes de sérialisation et que vous utilisez l’opérateur C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) en dehors de l’expression fournie au paramètre du constructeur <xref:System.Type> , comme dans le code suivant, le compilateur .net Native ne peut pas résoudre le type :  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Dans ce cas, vous devez spécifier le type dans le fichier de directives runtime en ajoutant une entrée comme suit :  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 De même, si vous appelez un constructeur tel que <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> et que vous fournissez un tableau d' <xref:System.Type> objets supplémentaires à sérialiser, comme dans le code suivant, le compilateur .net Native ne peut pas résoudre ces types.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
Ajoutez des entrées telles que les suivantes pour chaque type au fichier de directives Runtime :  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
Pour plus d’informations sur la syntaxe utilisée dans l’exemple, consultez [ \<Type> élément](type-element-net-native.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
- [\<Type>Appartient](type-element-net-native.md)
- [\<Namespace>Appartient](namespace-element-net-native.md)
