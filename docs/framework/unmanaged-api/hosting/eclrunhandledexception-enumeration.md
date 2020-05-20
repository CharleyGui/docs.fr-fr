---
title: EClrUnhandledException, énumération
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 63b07dda2293d3e05bd3c8fcdc45f20a498ea54c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616305"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="53ca3-102">EClrUnhandledException, énumération</span><span class="sxs-lookup"><span data-stu-id="53ca3-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="53ca3-103">Décrit les options disponibles pour gérer les exceptions qui ne sont pas gérées dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53ca3-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ca3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53ca3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="53ca3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="53ca3-105">Members</span></span>  
  
|<span data-ttu-id="53ca3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="53ca3-106">Member</span></span>|<span data-ttu-id="53ca3-107">Description</span><span class="sxs-lookup"><span data-stu-id="53ca3-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="53ca3-108">Spécifie que le comportement par défaut se produit.</span><span class="sxs-lookup"><span data-stu-id="53ca3-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="53ca3-109">Le processus est détruit.</span><span class="sxs-lookup"><span data-stu-id="53ca3-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="53ca3-110">Spécifie que le common language runtime (CLR) ignore les exceptions non gérées et laisse l’hôte déterminer toute action supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="53ca3-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53ca3-111">Notes</span><span class="sxs-lookup"><span data-stu-id="53ca3-111">Remarks</span></span>  
 <span data-ttu-id="53ca3-112">Pour spécifier que le CLR se comporte comme des versions antérieures, utilisez le `eHostDeterminedPolicy` membre.</span><span class="sxs-lookup"><span data-stu-id="53ca3-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ca3-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="53ca3-113">Requirements</span></span>  
 <span data-ttu-id="53ca3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53ca3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ca3-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="53ca3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53ca3-116">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53ca3-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53ca3-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ca3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ca3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53ca3-118">See also</span></span>

- [<span data-ttu-id="53ca3-119">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="53ca3-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="53ca3-120">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="53ca3-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="53ca3-121">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="53ca3-121">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="53ca3-122">SetUnhandledExceptionPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="53ca3-122">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="53ca3-123">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="53ca3-123">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="53ca3-124">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="53ca3-124">Hosting Enumerations</span></span>](hosting-enumerations.md)
