---
title: ICLRMetaHost::RequestRuntimeLoadedNotification, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
ms.openlocfilehash: 6813f72f9d27aeff90f797a6ca9370b22e03e6f0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703694"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="aad4f-102">ICLRMetaHost::RequestRuntimeLoadedNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="aad4f-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="aad4f-103">Fournit une fonction de rappel dont l’appel est garanti quand une version de common language runtime (CLR) est chargée pour la première fois, mais qu’elle n’a pas encore démarré.</span><span class="sxs-lookup"><span data-stu-id="aad4f-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="aad4f-104">Cette méthode remplace la fonction [LockClrVersion](lockclrversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="aad4f-104">This method supersedes the [LockClrVersion](lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad4f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad4f-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aad4f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aad4f-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="aad4f-107">dans Fonction de rappel qui est appelée lorsqu’un nouveau Runtime a été chargé.</span><span class="sxs-lookup"><span data-stu-id="aad4f-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aad4f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aad4f-108">Return Value</span></span>  
 <span data-ttu-id="aad4f-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="aad4f-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aad4f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aad4f-110">HRESULT</span></span>|<span data-ttu-id="aad4f-111">Description</span><span class="sxs-lookup"><span data-stu-id="aad4f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aad4f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="aad4f-112">S_OK</span></span>|<span data-ttu-id="aad4f-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="aad4f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="aad4f-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="aad4f-114">E_POINTER</span></span>|<span data-ttu-id="aad4f-115">`pCallbackFunction` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="aad4f-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aad4f-116">Notes</span><span class="sxs-lookup"><span data-stu-id="aad4f-116">Remarks</span></span>  
 <span data-ttu-id="aad4f-117">Le rappel fonctionne de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="aad4f-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="aad4f-118">Le rappel est appelé uniquement lorsqu’un Runtime est chargé pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="aad4f-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="aad4f-119">Le rappel n’est pas appelé pour les charges réentrantes du même Runtime.</span><span class="sxs-lookup"><span data-stu-id="aad4f-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="aad4f-120">Pour les chargements de Runtime non réentrants, les appels à la fonction de rappel sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="aad4f-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="aad4f-121">La fonction de rappel a le prototype suivant :</span><span class="sxs-lookup"><span data-stu-id="aad4f-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="aad4f-122">Les prototypes de fonction de rappel sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="aad4f-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="aad4f-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="aad4f-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="aad4f-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="aad4f-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="aad4f-125">Si l’hôte envisage de charger ou de faire en sorte qu’un autre Runtime soit chargé de manière réentrante, les `pfnCallbackThreadSet` `pfnCallbackThreadUnset` paramètres et fournis dans la fonction de rappel doivent être utilisés de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="aad4f-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="aad4f-126">`pfnCallbackThreadSet`doit être appelé par le thread qui peut provoquer un chargement du runtime avant une tentative de chargement.</span><span class="sxs-lookup"><span data-stu-id="aad4f-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="aad4f-127">`pfnCallbackThreadUnset`doit être appelé lorsque le thread n’entraîne plus de charge d’exécution de ce type (et avant de retourner le rappel initial).</span><span class="sxs-lookup"><span data-stu-id="aad4f-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="aad4f-128">`pfnCallbackThreadSet`et `pfnCallbackThreadUnset` sont tous deux non réentrants.</span><span class="sxs-lookup"><span data-stu-id="aad4f-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aad4f-129">Les applications hôtes ne doivent pas appeler `pfnCallbackThreadSet` et `pfnCallbackThreadUnset` en dehors de la portée du `pCallbackFunction` paramètre.</span><span class="sxs-lookup"><span data-stu-id="aad4f-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad4f-130">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="aad4f-130">Requirements</span></span>  
 <span data-ttu-id="aad4f-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad4f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad4f-132">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="aad4f-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aad4f-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aad4f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aad4f-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad4f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad4f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aad4f-135">See also</span></span>

- [<span data-ttu-id="aad4f-136">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="aad4f-136">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="aad4f-137">Hébergement</span><span class="sxs-lookup"><span data-stu-id="aad4f-137">Hosting</span></span>](index.md)
