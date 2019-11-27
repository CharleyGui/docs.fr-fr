---
title: CorDeclSecurity, énumération
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 98183ed02f8821b7c40852de2d040775d30f2518
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443740"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="60148-102">CorDeclSecurity, énumération</span><span class="sxs-lookup"><span data-stu-id="60148-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="60148-103">Spécifie les actions de sécurité qui peuvent être effectuées à l’aide de la sécurité déclarative.</span><span class="sxs-lookup"><span data-stu-id="60148-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60148-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60148-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="60148-105">Membres</span><span class="sxs-lookup"><span data-stu-id="60148-105">Members</span></span>  
  
|<span data-ttu-id="60148-106">Membre</span><span class="sxs-lookup"><span data-stu-id="60148-106">Member</span></span>|<span data-ttu-id="60148-107">Description</span><span class="sxs-lookup"><span data-stu-id="60148-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="60148-108">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="60148-109">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="60148-110">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="60148-111">Tous les appelants figurant plus haut dans la pile des appels doivent disposer de l’autorisation spécifiée par l’objet d’autorisation actuel.</span><span class="sxs-lookup"><span data-stu-id="60148-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="60148-112">Le code appelant peut accéder à la ressource identifiée par l’objet d’autorisation actuel, même si les appelants situés plus haut dans la pile n’ont pas reçu l’autorisation d’accéder à la ressource</span><span class="sxs-lookup"><span data-stu-id="60148-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="60148-113">La possibilité d’accéder à la ressource spécifiée par l’objet d’autorisation actuel est refusée aux appelants, même s’ils ont reçu l’autorisation d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="60148-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="60148-114">Seules les ressources spécifiées par l’objet d’autorisation sont accessibles, même si le code a reçu l’autorisation d’accéder à d’autres ressources.</span><span class="sxs-lookup"><span data-stu-id="60148-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="60148-115">L’appelant immédiat doit avoir reçu l’autorisation spécifiée pour une période donnée.</span><span class="sxs-lookup"><span data-stu-id="60148-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="60148-116">La classe dérivée qui hérite d’une autre classe ou qui substitue une méthode doit avoir reçu l’autorisation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="60148-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="60148-117">L’appelant peut demander les autorisations minimales requises pour l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="60148-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="60148-118">Cette action ne peut être utilisée que dans la portée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="60148-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="60148-119">L’appelant peut demander des autorisations supplémentaires qui sont facultatives (non requises pour s’exécuter).</span><span class="sxs-lookup"><span data-stu-id="60148-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="60148-120">Cette requête refuse implicitement toutes les autres autorisations qui ne sont pas spécifiquement demandées.</span><span class="sxs-lookup"><span data-stu-id="60148-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="60148-121">Cette action ne peut être utilisée que dans la portée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="60148-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="60148-122">La demande d’autorisation de l’appelant qui peut être utilisée à l’utilisation incorrecte ne sera pas accordée.</span><span class="sxs-lookup"><span data-stu-id="60148-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="60148-123">Cette action ne peut être utilisée que dans la portée de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="60148-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="60148-124">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="60148-125">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="60148-126">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="60148-127">L’appelant immédiat doit avoir reçu l’autorisation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="60148-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="60148-128">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="60148-129">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="60148-130">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="60148-131">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="60148-132">Réservé.</span><span class="sxs-lookup"><span data-stu-id="60148-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60148-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="60148-133">Requirements</span></span>  
 <span data-ttu-id="60148-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60148-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60148-135">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="60148-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="60148-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60148-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60148-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60148-137">See also</span></span>

- [<span data-ttu-id="60148-138">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="60148-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
