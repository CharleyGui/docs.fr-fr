---
title: Noms de contrats de données
description: Découvrez les règles de nom de membre et de contrat de données et le comportement par défaut de l’infrastructure WCF, qui prennent en charge la communication à l’aide de contrats de données équivalents.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 3bb0aca2a1207a98b45fe8b6d43930e9b2acc5ec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286699"
---
# <a name="data-contract-names"></a>Noms de contrats de données

Il arrive parfois qu'un client et un service ne partagent pas les mêmes types. Ils peuvent toujours se transmettre des données tant que les contrats de données sont équivalents des deux côtés. L' [équivalence des contrats de données](data-contract-equivalence.md) est basée sur le contrat de données et les noms des membres de données, et un mécanisme est donc fourni pour mapper des types et des membres à ces noms. Cette rubrique explique les règles de dénomination des contrats de données, ainsi que le comportement par défaut de l’infrastructure Windows Communication Foundation (WCF) lors de la création de noms.

## <a name="basic-rules"></a>Règles de base

Les règles de base concernant l'attribution de noms aux contrats de données sont les suivantes :

- Un nom de contrat de données complet se compose d'un espace de noms et d'un nom.

- Les membres de données incluent uniquement des noms, mais pas d'espace de noms.

- Lors du traitement de contrats de données, l’infrastructure WCF est sensible à la casse pour les espaces de noms et les noms des contrats de données et des données membres.

## <a name="data-contract-namespaces"></a>Espaces de noms de contrat de données

Un espace de noms de contrat de données prend la forme d'un URI (Uniform Resource Identifier). L'URI peut être absolu ou relatif. Par défaut, les contrats de données d'un type spécifique sont affectés d'un espace de noms provenant de l'espace de noms CLR (Common Language Runtime) de ce type.

Par défaut, tout espace de noms CLR donné (au format *CLR. Namespace*) est mappé à l’espace de noms `http://schemas.datacontract.org/2004/07/Clr.Namespace` . Pour substituer cette valeur par défaut, appliquez l'attribut <xref:System.Runtime.Serialization.ContractNamespaceAttribute> à l'ensemble du module ou de l'assembly. Ou bien, pour contrôler l'espace de noms de contrat de données pour chaque type, définissez la propriété <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> de <xref:System.Runtime.Serialization.DataContractAttribute>.

> [!NOTE]
> L' `http://schemas.microsoft.com/2003/10/Serialization` espace de noms est réservé et ne peut pas être utilisé en tant qu’espace de noms de contrat de données.

> [!NOTE]
> Vous ne pouvez pas substituer l'espace de noms par défaut dans les types de contrats de données contenant des déclarations `delegate`.

## <a name="data-contract-names"></a>Noms de contrats de données

Le nom par défaut d'un contrat de données d'un type donné correspond au nom de ce type. Pour substituer la valeur par défaut, affectez un autre nom à la propriété <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> de <xref:System.Runtime.Serialization.DataContractAttribute>. Les règles spéciales pour les types génériques sont décrites dans « Noms de contrat de données pour les types génériques », un peu plus loin dans cette rubrique.

## <a name="data-member-names"></a>Noms de membre de données

Le nom par défaut d'un membre de données pour une propriété ou un champ donné correspond au nom de cette propriété ou de ce champ. Pour substituer la valeur par défaut, affectez une autre valeur à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> de <xref:System.Runtime.Serialization.DataMemberAttribute>.

### <a name="examples"></a>Exemples

L'exemple suivant indique comment vous pouvez substituer le comportement d'attribution de noms par défaut des contrats de données et des membres de données.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Noms de contrat de données pour les types génériques

Il existe des règles spéciales pour déterminer des noms de contrat de données pour les types génériques. Elles permettent d'éviter les conflits de noms de contrat de données entre deux génériques fermés du même type générique.

Par défaut, le nom de contrat de données d’un type générique est le nom du type, suivi de la chaîne « of », suivi des noms de contrat de données des paramètres génériques, suivi d’un *hachage* calculé à l’aide des espaces de noms de contrat de données des paramètres génériques. Un hachage est le résultat d'une fonction mathématique qui agit comme une « empreinte digitale » et identifie de manière unique une portion de données. Lorsque tous les paramètres génériques sont des types primitifs, le hachage est omis.

Par exemple, considérez les types illustrés dans l'exemple suivant.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

Dans cet exemple, le type `Drawing<Square,RegularRedBrush>` a le nom de contrat de données "DrawingOfSquareRedBrush5HWGAU6h", où "5HWGAU6h" est un hachage des espaces de noms "urn:shapes" et "urn:default". Le type `Drawing<Square,SpecialRedBrush>` a le nom de contrat de données "DrawingOfSquareRedBrushjpB5LgQ_S", où "jpB5LgQ_S" est un hachage des espaces de noms "urn:shapes" et "urn:special". Notez que si le hachage n'est pas utilisé, les deux noms sont identiques, et donc une collision de nom se produit.

## <a name="customizing-data-contract-names-for-generic-types"></a>Personnalisation des noms de contrat de données pour les types génériques

Il arrive parfois que les noms de contrat de données générés pour les types génériques, comme décrit précédemment, soient inacceptables. Par exemple, peut-être savez-vous déjà qu'il n'y aura pas de conflit de noms et souhaitez supprimer le hachage. Dans ce cas, vous pouvez utiliser la <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> propriété pour spécifier une autre façon de générer des noms. Vous pouvez utiliser des nombres dans les accolades à l'intérieur de la propriété `Name` pour faire référence aux noms de contrat de données des paramètres génériques. (0 fait référence au premier paramètre, 1 fait référence au deuxième, et ainsi de suite.) Vous pouvez utiliser un signe dièse (#) à l’intérieur des accolades pour faire référence au hachage. Vous pouvez utiliser chacune de ces références à plusieurs reprises ou ne pas les utiliser du tout.

Par exemple, le type `Drawing` générique précédent aurait pu être déclaré comme indiqué dans l'exemple suivant.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

Dans ce cas, le type `Drawing<Square,RegularRedBrush>` a le nom de contrat de données "Drawing_using_RedBrush_brush_and_Square_shape". Notez que du fait de la présence de "{#}" dans la propriété <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>, le hachage n'est pas une partie du nom, et que par conséquent, le type peut être exposé à des conflits de noms ; par exemple, le type `Drawing<Square,SpecialRedBrush>` aurait exactement le même nom de contrat de données.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Utilisation de contrats de données](using-data-contracts.md)
- [Équivalence de contrats de données](data-contract-equivalence.md)
- [Noms de contrats de données](data-contract-names.md)
- [Contrôle de version des contrats de données](data-contract-versioning.md)
