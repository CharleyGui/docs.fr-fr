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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca125932ede48aa43bc51e3d5a7851fb7762547
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490318"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="5ac84-102">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="5ac84-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="5ac84-103">Obtient les informations de version du common language runtime (CLR) approprié pour la classe avec la valeur `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="5ac84-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="5ac84-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5ac84-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac84-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ac84-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ac84-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ac84-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="5ac84-107">[in]  Le `CLSID` du composant.</span><span class="sxs-lookup"><span data-stu-id="5ac84-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="5ac84-108">[out]  Une mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="5ac84-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5ac84-109">[in]  La taille, en caractères larges, de la `pVersion` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5ac84-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="5ac84-110">[out] La longueur, en octets, de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="5ac84-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="5ac84-111">[in]  Une des valeurs CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="5ac84-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="5ac84-112">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="5ac84-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="5ac84-113">CLSID_RESOLUTION_DEFAULT : (0 x 0) Spécifie que le comportement d’interopérabilité par défaut doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="5ac84-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="5ac84-114">CLSID_RESOLUTION_REGISTERED : (0 x 1) Spécifie que le Registre doit être recherché et stratégie de shim doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="5ac84-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ac84-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5ac84-115">Return Value</span></span>  
  
|<span data-ttu-id="5ac84-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ac84-116">HRESULT</span></span>|<span data-ttu-id="5ac84-117">Description</span><span class="sxs-lookup"><span data-stu-id="5ac84-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ac84-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ac84-118">S_OK</span></span>|<span data-ttu-id="5ac84-119">La fonction a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5ac84-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="5ac84-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5ac84-120">E_INVALIDARG</span></span>|<span data-ttu-id="5ac84-121">L’un des paramètres a un type non valide ou le format.</span><span class="sxs-lookup"><span data-stu-id="5ac84-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="5ac84-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5ac84-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5ac84-123">Le `pVersion` mémoire tampon n’est pas assez grand pour contenir la chaîne de version entière.</span><span class="sxs-lookup"><span data-stu-id="5ac84-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="5ac84-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="5ac84-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="5ac84-125">Aucune classe n’est enregistrée avec la valeur `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="5ac84-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="5ac84-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5ac84-126">E_POINTER</span></span>|<span data-ttu-id="5ac84-127">`dwLength` a la valeur null, ou `cchBuffer` est suffisamment grande pour contenir la chaîne de version, mais `pVersion` est null.</span><span class="sxs-lookup"><span data-stu-id="5ac84-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ac84-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ac84-128">Requirements</span></span>  
 <span data-ttu-id="5ac84-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac84-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac84-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ac84-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ac84-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac84-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac84-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ac84-132">See also</span></span>

- [<span data-ttu-id="5ac84-133">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="5ac84-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
