---
title: LoadLibraryShim, fonction
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: d5e9ba0023b6516eb6190f32bc65b2b8b6af79f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727560"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="c2186-102">LoadLibraryShim, fonction</span><span class="sxs-lookup"><span data-stu-id="c2186-102">LoadLibraryShim Function</span></span>

<span data-ttu-id="c2186-103">Charge une version spécifiée d’une DLL qui est incluse dans le package redistribuable .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2186-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="c2186-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c2186-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="c2186-105">Utilisez la méthode [ICLRRuntimeInfo :: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="c2186-105">Use the [ICLRRuntimeInfo::LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2186-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2186-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2186-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2186-107">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="c2186-108">dans Chaîne se terminant par zéro qui représente le nom de la DLL à charger à partir de la bibliothèque de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2186-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="c2186-109">dans Chaîne se terminant par zéro qui représente la version de la DLL à charger.</span><span class="sxs-lookup"><span data-stu-id="c2186-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="c2186-110">Si `szVersion` a la valeur null, la version sélectionnée pour le chargement est la version la plus récente de la DLL spécifiée inférieure à la version 4.</span><span class="sxs-lookup"><span data-stu-id="c2186-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="c2186-111">Autrement dit, toutes les versions égales ou supérieures à la version 4 sont ignorées si `szVersion` a la valeur null, et si aucune version antérieure à la version 4 n’est installée, le chargement de la DLL échoue.</span><span class="sxs-lookup"><span data-stu-id="c2186-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="c2186-112">Cela permet de s’assurer que l’installation du .NET Framework 4 n’affecte pas les applications ou les composants préexistants.</span><span class="sxs-lookup"><span data-stu-id="c2186-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="c2186-113">Consultez l’entrée [in-proc SxS and Migration démarrage rapide](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) dans le blog de l’équipe CLR.</span><span class="sxs-lookup"><span data-stu-id="c2186-113">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c2186-114">Réservé à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="c2186-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="c2186-115">à Pointeur vers le handle du module.</span><span class="sxs-lookup"><span data-stu-id="c2186-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2186-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c2186-116">Return Value</span></span>  

 <span data-ttu-id="c2186-117">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="c2186-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c2186-118">Code de retour</span><span class="sxs-lookup"><span data-stu-id="c2186-118">Return code</span></span>|<span data-ttu-id="c2186-119">Description</span><span class="sxs-lookup"><span data-stu-id="c2186-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c2186-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2186-120">S_OK</span></span>|<span data-ttu-id="c2186-121">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="c2186-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="c2186-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="c2186-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="c2186-123">Le chargement `szDllName` requiert le chargement du Common Language Runtime (CLR) et la version nécessaire du CLR ne peut pas être chargée.</span><span class="sxs-lookup"><span data-stu-id="c2186-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2186-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="c2186-124">Remarks</span></span>  

 <span data-ttu-id="c2186-125">Cette fonction est utilisée pour charger les dll incluses dans le package redistribuable .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2186-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="c2186-126">Il ne charge pas les dll générées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c2186-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2186-127">À partir de la version .NET Framework 2,0, le chargement de Fusion.dll entraîne le chargement du CLR.</span><span class="sxs-lookup"><span data-stu-id="c2186-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="c2186-128">Cela est dû au fait que les fonctions de Fusion.dll sont désormais des wrappers dont les implémentations sont fournies par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="c2186-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2186-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c2186-129">Requirements</span></span>  

 <span data-ttu-id="c2186-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2186-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2186-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c2186-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2186-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2186-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2186-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2186-133">See also</span></span>

- [<span data-ttu-id="c2186-134">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c2186-134">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
