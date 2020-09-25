---
title: "Opérations de personnalisation : Vue d'ensemble"
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d4d375716e3199afcbbb9bbd8b8b04867ca0e5fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173521"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="f87bc-102">Opérations de personnalisation : Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f87bc-102">Customizing Operations: Overview</span></span>

<span data-ttu-id="f87bc-103">Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour les opérations d'insertion, de mise à jour et de suppression selon le mappage.</span><span class="sxs-lookup"><span data-stu-id="f87bc-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="f87bc-104">Dans la pratique cependant, vous souhaiterez généralement ajouter votre propre logique métier pour des raisons de sécurité, de validation, etc.</span><span class="sxs-lookup"><span data-stu-id="f87bc-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f87bc-105">les techniques de personnalisation de ces opérations sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f87bc-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="f87bc-106">Options de chargement</span><span class="sxs-lookup"><span data-stu-id="f87bc-106">Loading Options</span></span>  

 <span data-ttu-id="f87bc-107">Dans vos requêtes, vous pouvez déterminer quelle quantité de données liées à votre cible principale est récupérée lorsque vous vous connectez à la base de données.</span><span class="sxs-lookup"><span data-stu-id="f87bc-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="f87bc-108">Cette fonctionnalité est implémentée en grande partie à l'aide de <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="f87bc-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="f87bc-109">Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="f87bc-109">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="f87bc-110">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="f87bc-110">Partial Methods</span></span>  

 <span data-ttu-id="f87bc-111">Dans son mappage par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des méthodes partielles qui vous permettent d'implémenter votre logique métier.</span><span class="sxs-lookup"><span data-stu-id="f87bc-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="f87bc-112">Pour plus d’informations, consultez [Ajout d’une logique métier à l’aide de méthodes partielles](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f87bc-112">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="f87bc-113">Procédures stockées et fonctions définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f87bc-113">Stored Procedures and User-Defined Functions</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f87bc-114">prend en charge l’utilisation de procédures stockées et de fonctions définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f87bc-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="f87bc-115">Les procédures stockées sont couramment utilisées pour personnaliser des opérations.</span><span class="sxs-lookup"><span data-stu-id="f87bc-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="f87bc-116">Pour plus d’informations, consultez [Procédures stockées](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f87bc-116">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87bc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f87bc-117">See also</span></span>

- [<span data-ttu-id="f87bc-118">Personnalisation des opérations d'insertion, de mise à jour et de suppression</span><span class="sxs-lookup"><span data-stu-id="f87bc-118">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
