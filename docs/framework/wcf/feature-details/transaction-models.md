---
title: Modèles de transaction
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: d6c78a5342bf19d19308352cddc241f436bfcb3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745324"
---
# <a name="transaction-models"></a><span data-ttu-id="15b65-102">Modèles de transaction</span><span class="sxs-lookup"><span data-stu-id="15b65-102">Transaction Models</span></span>
<span data-ttu-id="15b65-103">Cette rubrique décrit la relation entre les modèles de programmation de transactions et les composants d'infrastructure que Microsoft fournit.</span><span class="sxs-lookup"><span data-stu-id="15b65-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="15b65-104">Lorsque vous utilisez des transactions dans Windows Communication Foundation (WCF), il est important de comprendre que vous ne choisissez pas entre des modèles transactionnels différents, mais que vous utilisez des couches différentes d’un modèle intégré et cohérent.</span><span class="sxs-lookup"><span data-stu-id="15b65-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="15b65-105">Les sections suivantes décrivent les trois composants principaux d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="15b65-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="15b65-106">Transactions WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="15b65-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="15b65-107">La prise en charge des transactions dans WCF vous permet d’écrire des services transactionnels.</span><span class="sxs-lookup"><span data-stu-id="15b65-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="15b65-108">En outre, grâce à sa prise en charge du protocole WS-AtomicTransaction (WS-AT), les applications peuvent transmettre des transactions aux services Web créés à l’aide de la technologie WCF ou tierce.</span><span class="sxs-lookup"><span data-stu-id="15b65-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="15b65-109">Dans un service ou une application WCF, les fonctionnalités de transaction WCF fournissent des attributs et une configuration pour spécifier de façon déclarative comment et quand l’infrastructure doit créer, transmettre et synchroniser des transactions.</span><span class="sxs-lookup"><span data-stu-id="15b65-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="15b65-110">Transactions System.Transactions</span><span class="sxs-lookup"><span data-stu-id="15b65-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="15b65-111">L’espace de noms <xref:System.Transactions> fournit un modèle de programmation explicite basé sur la classe <xref:System.Transactions.Transaction>, ainsi qu’un modèle de programmation implicite à utilisant la classe <xref:System.Transactions.TransactionScope>, dans lequel l’infrastructure gère automatiquement les transactions.</span><span class="sxs-lookup"><span data-stu-id="15b65-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="15b65-112">Pour plus d’informations sur la création d’une application transactionnelle à l’aide de ces deux modèles, consultez [écriture d’une application transactionnelle](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="15b65-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="15b65-113">Dans un service ou une application WCF, <xref:System.Transactions> fournit le modèle de programmation pour créer des transactions dans une application cliente et pour interagir explicitement avec une transaction, si nécessaire, au sein d’un service.</span><span class="sxs-lookup"><span data-stu-id="15b65-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="15b65-114">Transactions MSDTC</span><span class="sxs-lookup"><span data-stu-id="15b65-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="15b65-115">MSDTC (Microsoft Distributed Transaction Coordinator) est un gestionnaire de transactions qui prend en charge les transactions distribuées.</span><span class="sxs-lookup"><span data-stu-id="15b65-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="15b65-116">Pour plus d’informations, consultez le [Guide de référence du programmeur DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="15b65-116">For more information, see the [DTC Programmer's Reference](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="15b65-117">Dans un service ou une application WCF, MSDTC fournit l’infrastructure pour la coordination des transactions créées au sein d’un client ou d’un service.</span><span class="sxs-lookup"><span data-stu-id="15b65-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
