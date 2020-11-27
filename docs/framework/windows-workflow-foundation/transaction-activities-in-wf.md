---
title: Activités de transaction dans WF
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: c40799f7f0456a13ab975a766a36e9425a2144df
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293336"
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="77cc5-102">Activités de transaction dans WF</span><span class="sxs-lookup"><span data-stu-id="77cc5-102">Transaction Activities in WF</span></span>

<span data-ttu-id="77cc5-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] a plusieurs activités fournies par le système pour modéliser les transactions, la compensation et l’annulation.</span><span class="sxs-lookup"><span data-stu-id="77cc5-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="77cc5-104">Ces modèles de programmation permettent au workflow de poursuivre la progression vers l'avant dans le cas de modifications de logique métier et de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="77cc5-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="77cc5-105">Pour plus d’informations sur les transactions, la compensation et l’annulation, consultez [transactions](workflow-transactions.md), [compensation](compensation.md)et [annulation](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="77cc5-105">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="77cc5-106">Activités de transaction</span><span class="sxs-lookup"><span data-stu-id="77cc5-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="77cc5-107">Associe la logique d’annulation, sous la forme d’une activité, à un chemin d’accès principal d’exécution, également exprimé sous la forme d’une activité.</span><span class="sxs-lookup"><span data-stu-id="77cc5-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="77cc5-108">Prend en charge la compensation de ses activités enfants.</span><span class="sxs-lookup"><span data-stu-id="77cc5-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="77cc5-109">Appelle explicitement le gestionnaire de compensation d'un <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="77cc5-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="77cc5-110">Appelle explicitement le gestionnaire de confirmation d'un <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="77cc5-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="77cc5-111">Délimite une limite de transaction.</span><span class="sxs-lookup"><span data-stu-id="77cc5-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="77cc5-112">Définit la durée de vie d’une transaction créée par un message reçu.</span><span class="sxs-lookup"><span data-stu-id="77cc5-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="77cc5-113">La transaction peut être transmise dans le workflow sur le message de départ ou peut être créée par un répartiteur lorsque le message est reçu.</span><span class="sxs-lookup"><span data-stu-id="77cc5-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="77cc5-114">**Remarque :**  Le <xref:System.ServiceModel.Activities.TransactedReceiveScope> se trouve dans la section **messagerie** de la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="77cc5-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
