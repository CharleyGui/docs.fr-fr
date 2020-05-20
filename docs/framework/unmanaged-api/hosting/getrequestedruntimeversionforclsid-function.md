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
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617137"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="c5379-102">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="c5379-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="c5379-103">Obtient les informations de version de common language runtime (CLR) appropriées pour la classe avec le spécifié `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="c5379-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="c5379-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c5379-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5379-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5379-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5379-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5379-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="c5379-107">dans  `CLSID`Du composant.</span><span class="sxs-lookup"><span data-stu-id="c5379-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c5379-108">à  Mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="c5379-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c5379-109">dans  Taille, en caractères larges, de la `pVersion` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c5379-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c5379-110">à Longueur, en octets, de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="c5379-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="c5379-111">dans  L’une des valeurs CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="c5379-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="c5379-112">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="c5379-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="c5379-113">CLSID_RESOLUTION_DEFAULT : (0x0) spécifie que le comportement d’interopérabilité par défaut doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="c5379-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="c5379-114">CLSID_RESOLUTION_REGISTERED : (0x1) spécifie que la recherche doit être effectuée dans le registre et que la stratégie de shim doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="c5379-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5379-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5379-115">Return Value</span></span>  
  
|<span data-ttu-id="c5379-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5379-116">HRESULT</span></span>|<span data-ttu-id="c5379-117">Description</span><span class="sxs-lookup"><span data-stu-id="c5379-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5379-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5379-118">S_OK</span></span>|<span data-ttu-id="c5379-119">La fonction a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="c5379-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="c5379-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c5379-120">E_INVALIDARG</span></span>|<span data-ttu-id="c5379-121">Le type ou le format de l’un des paramètres n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c5379-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="c5379-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c5379-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c5379-123">La `pVersion` mémoire tampon n’est pas assez grande pour contenir la chaîne de version entière.</span><span class="sxs-lookup"><span data-stu-id="c5379-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="c5379-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="c5379-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="c5379-125">Aucune classe n’est inscrite avec le spécifié `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="c5379-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="c5379-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c5379-126">E_POINTER</span></span>|<span data-ttu-id="c5379-127">`dwLength`a la valeur null ou `cchBuffer` est suffisamment grand pour contenir la chaîne de version, mais `pVersion` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c5379-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5379-128">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="c5379-128">Requirements</span></span>  
 <span data-ttu-id="c5379-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5379-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5379-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5379-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5379-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5379-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5379-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5379-132">See also</span></span>

- [<span data-ttu-id="c5379-133">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c5379-133">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
