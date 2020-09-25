---
title: 'Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: ec1ff7cdbdc83bc409b191f0aefe2b50cbad9225
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192163"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand

Cette rubrique indique comment exécuter une procédure stockée paramétrable à l'aide de la classe <xref:System.Data.EntityClient.EntityCommand>.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1. Ajoutez le [modèle School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Importez la procédure stockée `GetStudentGrades` et spécifiez des entités `CourseGrade` comme type de retour. Pour plus d’informations sur l’importation d’une procédure stockée, consultez [procédure : importer une procédure stockée](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).  
  
## <a name="example"></a>Exemple  

 Le code suivant exécute la procédure stockée `GetStudentGrades` dans laquelle `StudentId` est un paramètre requis. Les résultats sont alors lus par un <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md)
