---
title: 'Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 27e756d8e44580d9205cc075367bce5a45536c69
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854684"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand
Cette rubrique indique comment exécuter une procédure stockée paramétrable à l'aide de la classe <xref:System.Data.EntityClient.EntityCommand>.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1. Ajoutez le [modèle School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d'informations, voir [Procédure : Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Importez la procédure stockée `GetStudentGrades` et spécifiez des entités `CourseGrade` comme type de retour. Pour plus d’informations sur l’importation d’une procédure stockée, consultez [procédure : Importez une](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))procédure stockée.  
  
## <a name="example"></a>Exemples  
 Le code suivant exécute la procédure stockée `GetStudentGrades` dans laquelle `StudentId` est un paramètre requis. Les résultats sont alors lus par un <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md)
