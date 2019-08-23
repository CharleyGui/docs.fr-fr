---
title: Personnalisation des opérations d'insertion, de mise à jour et de suppression
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: f75f4b4caf6b72076a83bde2f2c659aab4c9707d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912563"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="a0e7b-102">Personnalisation des opérations d'insertion, de mise à jour et de suppression</span><span class="sxs-lookup"><span data-stu-id="a0e7b-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="a0e7b-103">Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour implémenter les opérations d'insertion, de lecture, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="a0e7b-104">Dans la pratique toutefois, vous personnalisez généralement votre application en fonction de vos besoins professionnels.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0e7b-105">Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour personnaliser les actions d’insertion, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="a0e7b-106">Cette section de rubriques décrit les techniques que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit pour personnaliser les opérations d'insertion, de lecture, de mise à jour et de suppression dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0e7b-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a0e7b-107">In This Section</span></span>  
 [<span data-ttu-id="a0e7b-108">Personnalisation des opérations: Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="a0e7b-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="a0e7b-109">Décrit les différentes techniques fournies par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour personnaliser les opérations d'insertion, de lecture, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="a0e7b-110">Opérations d’insertion, de mise à jour et de suppression</span><span class="sxs-lookup"><span data-stu-id="a0e7b-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="a0e7b-111">Décrit les processus par défaut de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour manipuler des données de base de données.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="a0e7b-112">Responsabilités du développeur en matière de substitution du comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="a0e7b-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="a0e7b-113">Décrit le rôle du développeur dans l’implémentation des exigences non appliquées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0e7b-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="a0e7b-114">Ajout d’une logique métier à l’aide de méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="a0e7b-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="a0e7b-115">Explique comment utiliser des méthodes partielles pour substituer des méthodes générées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a0e7b-115">Describes how to use partial methods to override autogenerated methods.</span></span>
