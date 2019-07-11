---
title: WritePropertyValue (fonction) (référence des API non managées)
description: La fonction WritePropertyValue écrit les octets à une propriété.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47120ff9de9e6e4802c5aea990841b235cd6c74c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783066"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="b6bfc-103">WritePropertyValue (fonction)</span><span class="sxs-lookup"><span data-stu-id="b6bfc-103">WritePropertyValue function</span></span>
<span data-ttu-id="b6bfc-104">Écrit un nombre spécifié d’octets dans une propriété identifiée par un descripteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b6bfc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6bfc-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="b6bfc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6bfc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b6bfc-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b6bfc-108">[in] Un pointeur vers un [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="b6bfc-109">[in] Entier qui contient le handle qui identifie cette propriété.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="b6bfc-110">Le handle peut être récupéré en appelant le [GetPropertyHandle](getpropertyhandle.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="b6bfc-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="b6bfc-111">[in] Le nombre d’octets écrits dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="b6bfc-112">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="b6bfc-113">[out] Pointeur vers le tableau d’octets qui contient les données.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6bfc-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6bfc-114">Return value</span></span>

<span data-ttu-id="b6bfc-115">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="b6bfc-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b6bfc-116">Constante</span><span class="sxs-lookup"><span data-stu-id="b6bfc-116">Constant</span></span>  |<span data-ttu-id="b6bfc-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="b6bfc-117">Value</span></span>  |<span data-ttu-id="b6bfc-118">Description</span><span class="sxs-lookup"><span data-stu-id="b6bfc-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b6bfc-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b6bfc-119">0x80041008</span></span> | <span data-ttu-id="b6bfc-120">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="b6bfc-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="b6bfc-121">0x80041005</span></span> | <span data-ttu-id="b6bfc-122">Une incompatibilité de type s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b6bfc-123">0</span><span class="sxs-lookup"><span data-stu-id="b6bfc-123">0</span></span> | <span data-ttu-id="b6bfc-124">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b6bfc-125">Notes</span><span class="sxs-lookup"><span data-stu-id="b6bfc-125">Remarks</span></span>

<span data-ttu-id="b6bfc-126">Cette fonction encapsule un appel à la [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) (méthode).</span><span class="sxs-lookup"><span data-stu-id="b6bfc-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="b6bfc-127">Utilisez cette fonction pour définir la chaîne et tous les autres non -`DWORD` ou non-`QWORD` données.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="b6bfc-128">Pour les valeurs de propriété sans chaînes, `lNumBytes` doit être la taille des données correctes du type de propriété spécifié.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="b6bfc-129">Pour les valeurs de propriété de chaîne, `lNumBytes` doit être la longueur de la chaîne spécifiée en octets et la chaîne lui-même doit être de même longueur en octets et être suivie d’un caractère de fin de la valeur null.</span><span class="sxs-lookup"><span data-stu-id="b6bfc-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6bfc-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b6bfc-130">Requirements</span></span>  
<span data-ttu-id="b6bfc-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6bfc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6bfc-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b6bfc-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b6bfc-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b6bfc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bfc-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6bfc-134">See also</span></span>

- [<span data-ttu-id="b6bfc-135">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="b6bfc-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
