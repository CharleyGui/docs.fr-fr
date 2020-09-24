---
title: Appels de méthodes locaux
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 25aded1aa961e182e8d2d472fca4c5a84b501af1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166168"
---
# <a name="local-method-calls"></a><span data-ttu-id="cf8ba-102">Appels de méthodes locaux</span><span class="sxs-lookup"><span data-stu-id="cf8ba-102">Local Method Calls</span></span>

<span data-ttu-id="cf8ba-103">Un appel de méthode local est un appel exécuté dans le modèle objet.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="cf8ba-104">Un appel de méthode distant est un appel que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit en SQL et est transmis au moteur de base de données pour l'exécution.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="cf8ba-105">Les appels de méthode locaux sont nécessaires lorsque [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne peut pas traduire l’appel en SQL.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="cf8ba-106">Sinon, une exception <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="cf8ba-107">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="cf8ba-107">Example 1</span></span>  

 <span data-ttu-id="cf8ba-108">Dans l'exemple suivant, une classe `Order` est mappée à la table Orders dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="cf8ba-109">Une méthode d'instance locale a été ajoutée à la classe.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="cf8ba-110">Dans Query1, le constructeur de la classe `Order` est exécuté localement.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="cf8ba-111">Dans Query2, si [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a essayé de traduire `LocalInstanceMethod()` en SQL, la tentative échoue et une exception <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="cf8ba-112">Toutefois, comme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit le support pour les appels de méthode locaux, Query2 ne lèvera pas d'exception.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cf8ba-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf8ba-113">See also</span></span>

- [<span data-ttu-id="cf8ba-114">Informations générales</span><span class="sxs-lookup"><span data-stu-id="cf8ba-114">Background Information</span></span>](background-information.md)
