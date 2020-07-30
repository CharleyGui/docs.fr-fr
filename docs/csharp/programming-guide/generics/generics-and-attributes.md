---
title: Génériques et attributs - Guide de programmation C#
description: En savoir plus sur l’application d’attributs aux types génériques. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299875"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Génériques et attributs (Guide de programmation C#)
Les attributs peuvent être appliqués aux types génériques de la même manière qu’aux types non génériques. Pour plus d’informations sur l’application des attributs, consultez [Attributs](../concepts/attributes/index.md).  
  
 Les attributs personnalisés sont uniquement autorisés à référencer des types génériques ouverts, qui sont des types génériques pour lesquels aucun argument de type n’est fourni, et des types génériques construits fermés, qui fournissent des arguments pour tous les paramètres de type.  
  
 Les exemples suivants utilisent cet attribut personnalisé :  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Un attribut peut référencer un type générique ouvert :  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Spécifiez plusieurs paramètres de type à l’aide du nombre approprié de virgules. Dans cet exemple, `GenericClass2` a deux paramètres de type :  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Un attribut peut référencer un type générique construit fermé :  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Un attribut qui référence un paramètre de type générique entraîne une erreur de compilation :  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Un type générique ne peut pas hériter d’<xref:System.Attribute> :  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Pour obtenir des informations sur un type générique ou un paramètre de type au moment de l’exécution, vous pouvez utiliser les méthodes de <xref:System.Reflection>. Pour plus d’informations, consultez [Génériques et réflexion](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Génériques](./index.md)
- [Attributs](../../../standard/attributes/index.md)
