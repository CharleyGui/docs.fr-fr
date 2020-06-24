---
title: Types énumération dans les contrats de données
description: Découvrez comment le modèle de contrat de données exprime les énumérations dans le cadre du modèle de programmation WFC.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: ff3184a285e88d47d4545a38a6c74b2f209827fb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247297"
---
# <a name="enumeration-types-in-data-contracts"></a>Types énumération dans les contrats de données
Les énumérations peuvent être exprimées dans le modèle de contrat de données. Cette rubrique décrit plusieurs exemples qui expliquent le modèle de programmation.  
  
## <a name="enumeration-basics"></a>Principes de base de l'énumération  
 Appliquer l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> au type constitue une façon d'utiliser des types énumération dans le modèle de contrat de données. Vous devez appliquer ensuite l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute> à chaque membre qui doit être inclus dans le contrat de données.  
  
 L'exemple suivant illustre deux classes. La première utilise l'énumération et la seconde définit l'énumération.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Une instance de la classe `Car` peut être envoyée ou reçue uniquement si le champ `condition` a l'une des valeurs `New`, `Used` ou `Rental`. Si la `condition` a pour valeur `Broken` ou `Stolen`, une <xref:System.Runtime.Serialization.SerializationException> est levée.  
  
 Vous pouvez utiliser comme d'habitude les propriétés <xref:System.Runtime.Serialization.DataContractAttribute> (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> et <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) pour les contrats de données de l'énumération.  
  
### <a name="enumeration-member-values"></a>Valeurs de membre de l'énumération  
 En général, le contrat de données inclut des noms de membre de l'énumération, pas des valeurs numériques. Toutefois, lorsque vous utilisez le modèle de contrat de données, si le côté réception est un client WCF, le schéma exporté conserve les valeurs numériques. Notez que ce n’est pas le cas lors de l’utilisation de l’utilisation de la [classe XmlSerializer](using-the-xmlserializer-class.md).  
  
 Dans l'exemple précédent, si `condition` a la valeur `Used` et que les données sont sérialisées en XML, le XML résultant est `<condition>Used</condition>` et pas `<condition>1</condition>`. Par conséquent, le contrat de données suivant est équivalent au contrat de données de `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Par exemple, vous pouvez utiliser `CarConditionEnum` côté envoi et `CarConditionWithNumbers` côté réception. Même si le côté envoi utilise la valeur « 1 » pour `Used` et le côté réception la valeur « 20 », la représentation XML est `<condition>Used</condition>` pour les deux côtés.  
  
 Pour qu'il soit inclus dans le contrat de données, vous devez appliquer l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute>. Dans l' .NET Framework, vous pouvez toujours appliquer la valeur spéciale 0 (zéro) à une énumération, qui est également la valeur par défaut pour toute énumération. Cependant, même cette valeur zéro spéciale ne peut pas être sérialisée sauf si elle est marquée avec l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute>.  
  
 Il existe deux exceptions :  
  
- Les énumérations d'indicateur (traitées plus loin dans cette rubrique).  
  
- Les membres de données de l'énumération dont la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false` (auquel cas l'énumération avec la valeur zéro est omise des données sérialisées).  
  
### <a name="customizing-enumeration-member-values"></a>Personnalisation des valeurs de membre de l'énumération  
 Vous pouvez personnaliser la valeur de membre de l'énumération qui forme une partie du contrat de données en utilisant la propriété <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> de l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute>.  
  
 Par exemple, le contrat de données suivant est également équivalent au contrat de données de `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 En cas de sérialisation, la valeur de `PreviouslyOwned` a la représentation XML `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Énumérations simples  
 Vous pouvez également sérialiser des types énumération auxquels l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> n'a pas été appliqué. Ces types énumération sont traités exactement comme indiqué précédemment, sauf que les membres (qui n'ont pas l'attribut <xref:System.NonSerializedAttribute>) sont traités comme si l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute> avait été appliqué. Par exemple, l'énumération suivante contient implicitement un contrat de données équivalent à l'exemple `CarConditionEnum` précédent.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Vous pouvez utiliser des énumérations simples lorsque vous n'avez pas besoin de personnaliser le nom du contrat de données et l'espace de noms de l'énumération, ainsi que les valeurs de membre de l'énumération.  
  
#### <a name="notes-on-simple-enumerations"></a>Note sur les énumérations simples  
 L'application de l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute> aux énumérations simples n'a aucun effet.  
  
 L'application de l'attribut <xref:System.SerializableAttribute> à l'énumération n'a aucun effet.  
  
 Le fait que la classe <xref:System.Runtime.Serialization.DataContractSerializer> honore l'attribut <xref:System.NonSerializedAttribute> appliqué aux membres de l'énumération est différent du comportement de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et de <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Ces deux sérialiseurs ignorent l'attribut <xref:System.NonSerializedAttribute>.  
  
## <a name="flag-enumerations"></a>Énumérations d'indicateurs  
 Vous pouvez appliquer l'attribut <xref:System.FlagsAttribute> aux énumérations. Dans ce cas, une liste de zéro ou plusieurs valeurs d'énumération peut être envoyée ou reçue simultanément.  
  
 Pour cela, appliquez l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à l'énumération d'indicateur, puis marquez tous les membres qui sont à la puissance de deux avec l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute>. Notez que pour utiliser une énumération d'indicateur, la progression doit être une séquence ininterrompue à la puissance de 2 (par exemple, 1, 2, 4, 8, 16, 32, 64).  
  
 Les étapes suivantes s'appliquent à l'envoi de la valeur d'énumération d'un indicateur :  
  
1. Essayez de rechercher un membre de l'énumération (auquel est appliqué l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute>) qui correspond à la valeur numérique. Une fois trouvé, envoyez une liste qui contient seulement ce membre.  
  
2. Essayez de décomposer la valeur numérique en une somme de manière à obtenir des membres de l'énumération (à chacun desquels est appliqué l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute>) qui correspondent à chaque partie de la somme. Envoyez la liste de tous ces membres. Notez que l' *algorithme gourmand* est utilisé pour trouver une telle somme. par conséquent, il n’est pas garanti qu’une telle somme soit trouvée même si elle est présente. Pour éviter ce problème, assurez-vous que les valeurs numériques des membres de l'énumération sont à la puissance de deux.  
  
3. Si les deux étapes précédentes échouent et que la valeur numérique est différente de zéro, levez une <xref:System.Runtime.Serialization.SerializationException>. Si la valeur numérique est égale à zéro, envoyez la liste vide.  
  
### <a name="example"></a>Exemple  
 L'exemple d'énumération suivant peut être utilisé dans une opération d'indicateur.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Les valeurs de l'exemple suivant sont sérialisées comme indiqué.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Using Data Contracts](using-data-contracts.md)
- [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md)
