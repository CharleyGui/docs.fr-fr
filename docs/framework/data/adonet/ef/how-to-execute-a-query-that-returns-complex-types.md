---
title: 'Procédure : Exécuter une requête qui retourne des types complexes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 01958637cedcd6d502d51e9f0821ff3a9faae840
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545322"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="db430-102">Procédure : Exécuter une requête qui retourne des types complexes</span><span class="sxs-lookup"><span data-stu-id="db430-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="db430-103">Cette rubrique indique comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] qui retourne des objets de type d'entité qui contiennent une propriété d'un type complexe.</span><span class="sxs-lookup"><span data-stu-id="db430-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="db430-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="db430-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="db430-105">Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="db430-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="db430-106">Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db430-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="db430-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="db430-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="db430-108">Double-cliquez sur le fichier. edmx pour afficher le modèle dans la [fenêtre Explorateur de modèles](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) de l’Entity designer.</span><span class="sxs-lookup"><span data-stu-id="db430-108">Double click the .edmx file to display the model in the [Model Browser window](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="db430-109">Sur la surface de Entity Designer, sélectionnez `Email` les `Phone` Propriétés et du `Contact` type d’entité, puis cliquez avec le bouton droit et sélectionnez **Refactoriser dans un nouveau type complexe**.</span><span class="sxs-lookup"><span data-stu-id="db430-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="db430-110">Un nouveau type complexe avec les `Email` Propriétés et sélectionnées `Phone` est ajouté à l' **Explorateur de modèles**.</span><span class="sxs-lookup"><span data-stu-id="db430-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="db430-111">Un nom par défaut est attribué au type complexe : renommez le type `EmailPhone` en dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="db430-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="db430-112">Une nouvelle propriété `ComplexProperty` est également ajoutée au type d'entité `Contact`.</span><span class="sxs-lookup"><span data-stu-id="db430-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="db430-113">Renommez la propriété en `EmailPhoneComplexType.`.</span><span class="sxs-lookup"><span data-stu-id="db430-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="db430-114">Pour plus d’informations sur la création et la modification de types complexes à l’aide de l’Assistant Entity Data Model, consultez [Comment : Refactoriser des propriétés existantes dans une propriété de type complexe](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) et [Comment : créer et modifier des types complexes](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db430-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db430-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="db430-115">Example</span></span>  
 <span data-ttu-id="db430-116">L’exemple suivant exécute une requête qui retourne une collection d' `Contact` objets et affiche deux propriétés des `Contact` objets : `ContactID` et les valeurs du `EmailPhoneComplexType` type complexe.</span><span class="sxs-lookup"><span data-stu-id="db430-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
