---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 577502d1cd3d81784cb9b1eb3b249376b8ffa6b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234893"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="55cf4-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="55cf4-102">TransactionFlowBindingElement</span></span>

<span data-ttu-id="55cf4-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="55cf4-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55cf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55cf4-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="55cf4-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="55cf4-105">Methods</span></span>  

 <span data-ttu-id="55cf4-106">La classe TransactionFlowBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="55cf4-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="55cf4-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="55cf4-107">Properties</span></span>  

 <span data-ttu-id="55cf4-108">La classe TransactionFlowBindingElement dispose des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="55cf4-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="55cf4-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="55cf4-109">IssuedTokens</span></span>  

 <span data-ttu-id="55cf4-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="55cf4-110">Data type: string</span></span>  
  
 <span data-ttu-id="55cf4-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="55cf4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55cf4-112">Définit les spécifications d'un en-tête de jetons de sécurité publié (IssuedTokens de WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="55cf4-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="55cf4-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="55cf4-113">TransactionProtocol</span></span>  

 <span data-ttu-id="55cf4-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="55cf4-114">Data type: string</span></span>  
  
 <span data-ttu-id="55cf4-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="55cf4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55cf4-116">Protocole de transactions utilisé par le service pour transférer les transactions.</span><span class="sxs-lookup"><span data-stu-id="55cf4-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="55cf4-117">Transactions</span><span class="sxs-lookup"><span data-stu-id="55cf4-117">Transactions</span></span>  

 <span data-ttu-id="55cf4-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="55cf4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="55cf4-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="55cf4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55cf4-120">Indique si la transaction entrante est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="55cf4-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55cf4-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="55cf4-121">Requirements</span></span>  
  
|<span data-ttu-id="55cf4-122">MOF</span><span class="sxs-lookup"><span data-stu-id="55cf4-122">MOF</span></span>|<span data-ttu-id="55cf4-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="55cf4-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="55cf4-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="55cf4-124">Namespace</span></span>|<span data-ttu-id="55cf4-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="55cf4-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55cf4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55cf4-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
