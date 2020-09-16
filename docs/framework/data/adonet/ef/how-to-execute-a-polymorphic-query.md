---
title: 'Procédure : Exécuter une requête polymorphe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: ad6fd7bf6a23f4cd1591a17b25042fd76ff1d08d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545335"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Procédure : Exécuter une requête polymorphe

Cette rubrique montre comment exécuter une requête polymorphe [!INCLUDE[esql](../../../../../includes/esql-md.md)] à l’aide de l’opérateur [OfType](./language-reference/oftype-entity-sql.md) .

### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple

1. Ajoutez le [modèle School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Modifiez le modèle conceptuel pour avoir un héritage TPH (table par hiérarchie) en suivant les étapes décrites dans [procédure pas à pas : mappage de l’héritage-TPH (table par hiérarchie](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))).

## <a name="example"></a> Exemple

L’exemple ci-dessous utilise un opérateur OFTYPE pour obtenir et afficher une collection d’éléments `OnsiteCourses` uniquement, à partir d’une collection de `Courses`.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Voir aussi

- [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md)
- [Langage d'Entity SQL](./language-reference/entity-sql-language.md)
