---
title: 'Procédure : Créer une chaîne de connexion EntityConnection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 86ba3956797ff603dd944bfc8df1990df8f23001
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556432"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a>Procédure : Créer une chaîne de connexion EntityConnection
Cette rubrique fournit un exemple de génération d'un objet <xref:System.Data.EntityClient.EntityConnection>.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1. Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a> Exemple  
 L'exemple ci-dessous initialise l'objet <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> pour le fournisseur sous-jacent, puis initialise l'objet <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> avant de le passer au constructeur de l'objet <xref:System.Data.EntityClient.EntityConnection>.  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a>Voir aussi

- [Comment : utiliser EntityConnection avec un contexte d'objet](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))
- [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md)
