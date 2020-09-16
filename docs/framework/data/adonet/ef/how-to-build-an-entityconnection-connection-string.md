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
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="aafc3-102">Procédure : Créer une chaîne de connexion EntityConnection</span><span class="sxs-lookup"><span data-stu-id="aafc3-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="aafc3-103">Cette rubrique fournit un exemple de génération d'un objet <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="aafc3-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="aafc3-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="aafc3-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="aafc3-105">Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="aafc3-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="aafc3-106">Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="aafc3-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="aafc3-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="aafc3-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="aafc3-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="aafc3-108">Example</span></span>  
 <span data-ttu-id="aafc3-109">L'exemple ci-dessous initialise l'objet <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> pour le fournisseur sous-jacent, puis initialise l'objet <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> avant de le passer au constructeur de l'objet <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="aafc3-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="aafc3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aafc3-110">See also</span></span>

- <span data-ttu-id="aafc3-111">[Comment : utiliser EntityConnection avec un contexte d'objet](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aafc3-111">[How to: Use EntityConnection with an Object Context](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span></span>
- [<span data-ttu-id="aafc3-112">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="aafc3-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
