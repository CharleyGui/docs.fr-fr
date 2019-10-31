---
title: GetRequestedRuntimeVersionForCLSID, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: ce0c6307defd93dcf63ac4e9051fc798041475f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127052"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="c5039-102">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="c5039-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="c5039-103">Obtient les informations de version de common language runtime (CLR) appropriées pour la classe avec le `CLSID`spécifié.</span><span class="sxs-lookup"><span data-stu-id="c5039-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="c5039-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c5039-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5039-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5039-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5039-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5039-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="c5039-107">dans  `CLSID` du composant.</span><span class="sxs-lookup"><span data-stu-id="c5039-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c5039-108">à  Mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="c5039-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c5039-109">dans  Taille, en caractères larges, de la mémoire tampon de `pVersion`.</span><span class="sxs-lookup"><span data-stu-id="c5039-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c5039-110">à Longueur, en octets, de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="c5039-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="c5039-111">dans  Une des valeurs CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="c5039-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="c5039-112">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="c5039-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="c5039-113">CLSID_RESOLUTION_DEFAULT : (0x0) spécifie que le comportement d’interopérabilité par défaut doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="c5039-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="c5039-114">CLSID_RESOLUTION_REGISTERED : (0x1) spécifie que la recherche doit être effectuée dans le registre et que la stratégie de shim doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="c5039-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5039-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5039-115">Return Value</span></span>  
  
|<span data-ttu-id="c5039-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5039-116">HRESULT</span></span>|<span data-ttu-id="c5039-117">Description</span><span class="sxs-lookup"><span data-stu-id="c5039-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5039-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5039-118">S_OK</span></span>|<span data-ttu-id="c5039-119">La fonction a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="c5039-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="c5039-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c5039-120">E_INVALIDARG</span></span>|<span data-ttu-id="c5039-121">Le type ou le format de l’un des paramètres n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c5039-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="c5039-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c5039-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c5039-123">La mémoire tampon de `pVersion` n’est pas assez grande pour contenir la chaîne de version entière.</span><span class="sxs-lookup"><span data-stu-id="c5039-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="c5039-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="c5039-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="c5039-125">Aucune classe n’est inscrite avec la `CLSID`spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5039-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="c5039-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c5039-126">E_POINTER</span></span>|<span data-ttu-id="c5039-127">`dwLength` a la valeur null, ou `cchBuffer` est suffisamment grand pour contenir la chaîne de version, mais `pVersion` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c5039-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5039-128">spécifications</span><span class="sxs-lookup"><span data-stu-id="c5039-128">Requirements</span></span>  
 <span data-ttu-id="c5039-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5039-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5039-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5039-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5039-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5039-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5039-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5039-132">See also</span></span>

- [<span data-ttu-id="c5039-133">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="c5039-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
