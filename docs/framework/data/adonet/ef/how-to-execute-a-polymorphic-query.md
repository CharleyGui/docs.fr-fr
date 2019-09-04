---
title: 'Procédure : Exécuter une requête polymorphe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251515"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="8f1fd-102">Procédure : Exécuter une requête polymorphe</span><span class="sxs-lookup"><span data-stu-id="8f1fd-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="8f1fd-103">Cette rubrique montre comment exécuter une [!INCLUDE[esql](../../../../../includes/esql-md.md)] requête polymorphe à l’aide de l’opérateur [OfType](./language-reference/oftype-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="8f1fd-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="8f1fd-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="8f1fd-104">To run the code in this example</span></span>

1. <span data-ttu-id="8f1fd-105">Ajoutez le [modèle School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8f1fd-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="8f1fd-106">Pour plus d'informations, voir [Procédure : Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="8f1fd-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="8f1fd-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f1fd-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="8f1fd-108">Modifiez le modèle conceptuel pour avoir un héritage TPH (table par hiérarchie) en suivant les étapes [décrites dans la procédure pas à pas : Mappage de l’héritage-TPH (table](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))par hiérarchie).</span><span class="sxs-lookup"><span data-stu-id="8f1fd-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="8f1fd-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f1fd-109">Example</span></span>

<span data-ttu-id="8f1fd-110">L’exemple ci-dessous utilise un opérateur OFTYPE pour obtenir et afficher une collection d’éléments `OnsiteCourses` uniquement, à partir d’une collection de `Courses`.</span><span class="sxs-lookup"><span data-stu-id="8f1fd-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="8f1fd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f1fd-111">See also</span></span>

- [<span data-ttu-id="8f1fd-112">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8f1fd-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="8f1fd-113">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8f1fd-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
