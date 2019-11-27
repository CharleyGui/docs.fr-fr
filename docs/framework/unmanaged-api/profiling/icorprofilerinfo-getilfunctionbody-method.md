---
title: ICorProfilerInfo::GetILFunctionBody, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: a7ec50c91ce02958d0d44643d4f79da1680532aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450354"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="86c5f-102">ICorProfilerInfo::GetILFunctionBody, méthode</span><span class="sxs-lookup"><span data-stu-id="86c5f-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="86c5f-103">Obtient un pointeur vers le corps d’une méthode dans le code MSIL (Microsoft Intermediate Language), en commençant à son en-tête.</span><span class="sxs-lookup"><span data-stu-id="86c5f-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86c5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86c5f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86c5f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="86c5f-106">dans ID du module dans lequel la fonction réside.</span><span class="sxs-lookup"><span data-stu-id="86c5f-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="86c5f-107">dans Jeton de métadonnées pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="86c5f-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="86c5f-108">à Pointeur vers l’en-tête de la méthode.</span><span class="sxs-lookup"><span data-stu-id="86c5f-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="86c5f-109">à Entier qui spécifie la taille de la méthode.</span><span class="sxs-lookup"><span data-stu-id="86c5f-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c5f-110">Notes</span><span class="sxs-lookup"><span data-stu-id="86c5f-110">Remarks</span></span>  
 <span data-ttu-id="86c5f-111">Une méthode est délimitée par le module dans lequel elle réside.</span><span class="sxs-lookup"><span data-stu-id="86c5f-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="86c5f-112">Étant donné que la méthode `GetILFunctionBody` est conçue pour permettre à un outil d’accéder au code MSIL avant qu’elle ait été chargée par le common language runtime (CLR), elle utilise le jeton de métadonnées de la méthode pour Rechercher l’instance souhaitée.</span><span class="sxs-lookup"><span data-stu-id="86c5f-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="86c5f-113">`GetILFunctionBody` pouvez retourner un HRESULT CORPROF_E_FUNCTION_NOT_IL si le `methodId` pointe vers une méthode sans code MSIL (par exemple, une méthode abstraite ou une méthode d’appel de code non managé (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="86c5f-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c5f-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="86c5f-114">Requirements</span></span>  
 <span data-ttu-id="86c5f-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c5f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c5f-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86c5f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86c5f-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86c5f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86c5f-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c5f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c5f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86c5f-119">See also</span></span>

- [<span data-ttu-id="86c5f-120">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="86c5f-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
