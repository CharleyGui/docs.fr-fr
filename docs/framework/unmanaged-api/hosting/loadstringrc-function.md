---
title: LoadStringRC, fonction
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 66d4c14234c7929af443922f86098b46a4aa6eb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122018"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="f5f6a-102">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="f5f6a-102">LoadStringRC Function</span></span>
<span data-ttu-id="f5f6a-103">Convertit une valeur HRESULT en message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="f5f6a-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f6a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5f6a-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f6a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5f6a-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="f5f6a-107">dans HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="f5f6a-108">à Mémoire tampon qui contient le message d’erreur une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="f5f6a-109">dans Taille de la mémoire tampon du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="f5f6a-110">dans Pas.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5f6a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f5f6a-111">Return Value</span></span>  
 <span data-ttu-id="f5f6a-112">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f5f6a-113">Code de retour</span><span class="sxs-lookup"><span data-stu-id="f5f6a-113">Return code</span></span>|<span data-ttu-id="f5f6a-114">Description</span><span class="sxs-lookup"><span data-stu-id="f5f6a-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f5f6a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5f6a-115">S_OK</span></span>|<span data-ttu-id="f5f6a-116">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="f5f6a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f5f6a-117">E_INVALIDARG</span></span>|<span data-ttu-id="f5f6a-118">`szBuffer` a la valeur null ou `iMax` est égal à zéro (0).</span><span class="sxs-lookup"><span data-stu-id="f5f6a-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5f6a-119">Notes</span><span class="sxs-lookup"><span data-stu-id="f5f6a-119">Remarks</span></span>  
 <span data-ttu-id="f5f6a-120">Si la méthode ne se termine pas correctement, `szBuffer` contient une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f6a-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="f5f6a-121">Requirements</span></span>  
 <span data-ttu-id="f5f6a-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f6a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f6a-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5f6a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5f6a-124">**Bibliothèque :** MSCorEE. dll et mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f5f6a-125">Utilisez MSCorEE. dll au lieu de Mscorwks. dll pour vous assurer que vous ciblez la version correcte du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5f6a-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f5f6a-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f6a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f6a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5f6a-127">See also</span></span>

- [<span data-ttu-id="f5f6a-128">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="f5f6a-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="f5f6a-129">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="f5f6a-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
