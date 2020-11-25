---
title: HOST_TYPE, énumération
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: 31640ada28af8e35554b91d5931d427fbaa8dcbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721853"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="c1f59-102">HOST_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="c1f59-102">HOST_TYPE Enumeration</span></span>

<span data-ttu-id="c1f59-103">Contient des valeurs qui spécifient le type d’hôte qui lance une application.</span><span class="sxs-lookup"><span data-stu-id="c1f59-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1f59-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="c1f59-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c1f59-105">Members</span></span>  
  
|<span data-ttu-id="c1f59-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c1f59-106">Member</span></span>|<span data-ttu-id="c1f59-107">Description</span><span class="sxs-lookup"><span data-stu-id="c1f59-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="c1f59-108">Lancez l’application à partir de AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="c1f59-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="c1f59-109">Utilisez cette valeur pour les applications de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="c1f59-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="c1f59-110">Lancez l’application directement.</span><span class="sxs-lookup"><span data-stu-id="c1f59-110">Launch the application directly.</span></span> <span data-ttu-id="c1f59-111">Autrement dit, lancez l’application à partir de son propre fichier. exe.</span><span class="sxs-lookup"><span data-stu-id="c1f59-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="c1f59-112">Utilisez cette valeur pour les applications de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="c1f59-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="c1f59-113">Identique à HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="c1f59-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1f59-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1f59-114">Requirements</span></span>  

 <span data-ttu-id="c1f59-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1f59-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f59-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c1f59-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1f59-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1f59-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1f59-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f59-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f59-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1f59-119">See also</span></span>

- [<span data-ttu-id="c1f59-120">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c1f59-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
