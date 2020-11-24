---
title: Fonction CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: 0f62b05ebbd8b27dba160c8281c1d40748c90fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688833"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="9d9d4-102">Fonction CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="9d9d4-102">CreateInstallReferenceEnum Function</span></span>

<span data-ttu-id="9d9d4-103">Obtient un pointeur vers une instance [IInstallReferenceEnum](iinstallreferenceenum-interface.md) qui représente une liste des références d’une application à l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d9d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d9d4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d9d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d9d4-105">Parameters</span></span>  

 `ppRefEnum`  
 <span data-ttu-id="9d9d4-106">à Pointeur retourné `IInstallReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="9d9d4-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="9d9d4-107">dans [IAssemblyName](iassemblyname-interface.md) qui identifie l’assembly pour lequel énumérer les références.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d9d4-108">dans Indicateurs qui influencent le comportement de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="9d9d4-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9d9d4-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d9d4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d9d4-111">Requirements</span></span>  

 <span data-ttu-id="9d9d4-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d9d4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d9d4-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9d9d4-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9d9d4-114">**Bibliothèque :** Fusion.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="9d9d4-115">Utilisez Fusion.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="9d9d4-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d9d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9d4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d9d4-117">See also</span></span>

- [<span data-ttu-id="9d9d4-118">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="9d9d4-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="9d9d4-119">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="9d9d4-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="9d9d4-120">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="9d9d4-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
