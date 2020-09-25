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
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="b7c0a-102">Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand</span><span class="sxs-lookup"><span data-stu-id="b7c0a-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>

<span data-ttu-id="b7c0a-103">Cette rubrique indique comment exécuter une procédure stockée paramétrable à l'aide de la classe <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="b7c0a-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="b7c0a-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="b7c0a-105">Ajoutez le [modèle School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-105">Add the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="b7c0a-106">Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b7c0a-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b7c0a-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7c0a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="b7c0a-108">Importez la procédure stockée `GetStudentGrades` et spécifiez des entités `CourseGrade` comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="b7c0a-109">Pour plus d’informations sur l’importation d’une procédure stockée, consultez [procédure : importer une procédure stockée](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b7c0a-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7c0a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7c0a-110">Example</span></span>  

 <span data-ttu-id="b7c0a-111">Le code suivant exécute la procédure stockée `GetStudentGrades` dans laquelle `StudentId` est un paramètre requis.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="b7c0a-112">Les résultats sont alors lus par un <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="b7c0a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7c0a-113">See also</span></span>

- [<span data-ttu-id="b7c0a-114">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b7c0a-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
