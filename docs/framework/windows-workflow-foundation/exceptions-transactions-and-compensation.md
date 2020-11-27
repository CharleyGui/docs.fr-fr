---
title: Exceptions, transactions et compensation
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 2d8574c0f0f6bd3f66214367c1ed15292adc24a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280232"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="83f78-102">Exceptions, transactions et compensation</span><span class="sxs-lookup"><span data-stu-id="83f78-102">Exceptions, Transactions, and Compensation</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="83f78-103">fournit plusieurs mécanismes différents pour gérer les conditions d'erreur d'exécution dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="83f78-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="83f78-104">Les workflows peuvent utiliser une combinaison de gestionnaires d'exceptions, transactions, annulation et compensation pour gérer et effectuer une récupération normale à partir des conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="83f78-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83f78-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="83f78-105">In This Section</span></span>  

 [<span data-ttu-id="83f78-106">Exceptions</span><span class="sxs-lookup"><span data-stu-id="83f78-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="83f78-107">Montre comment utiliser l'activité <xref:System.Activities.Statements.TryCatch> pour gérer des exceptions dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="83f78-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="83f78-108">Transactions</span><span class="sxs-lookup"><span data-stu-id="83f78-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="83f78-109">Montre comment utiliser l’activité <xref:System.Activities.Statements.TransactionScope> pour utiliser des transactions dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="83f78-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="83f78-110">Compensation</span><span class="sxs-lookup"><span data-stu-id="83f78-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="83f78-111">Décrit la compensation dans les workflows et montre comment utiliser des activités de compensation telles que <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate> et <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="83f78-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="83f78-112">Annulation</span><span class="sxs-lookup"><span data-stu-id="83f78-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="83f78-113">Explique comment effectuer la gestion des annulations dans les workflows à l'aide d'activités intégrées ainsi que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="83f78-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="83f78-114">Débogage de workflows</span><span class="sxs-lookup"><span data-stu-id="83f78-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="83f78-115">Décrit comment déboguer des workflows.</span><span class="sxs-lookup"><span data-stu-id="83f78-115">Describes how to debug workflows.</span></span>
