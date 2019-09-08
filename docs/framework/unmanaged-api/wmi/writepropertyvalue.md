---
title: Fonction WritePropertyValue (référence des API non managées)
description: La fonction WritePropertyValue écrit des octets dans une propriété.
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
ms.openlocfilehash: a3c42129835f9b30bed493a0992d49d7e2a458e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798176"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="23bf3-103">WritePropertyValue fonction)</span><span class="sxs-lookup"><span data-stu-id="23bf3-103">WritePropertyValue function</span></span>
<span data-ttu-id="23bf3-104">Écrit un nombre spécifié d’octets dans une propriété identifiée par un descripteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="23bf3-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="23bf3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23bf3-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="23bf3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23bf3-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="23bf3-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="23bf3-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="23bf3-108">dans Pointeur vers une instance [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="23bf3-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="23bf3-109">dans Entier qui contient le handle qui identifie cette propriété.</span><span class="sxs-lookup"><span data-stu-id="23bf3-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="23bf3-110">Le descripteur peut être récupéré en appelant la fonction [GetPropertyHandle](getpropertyhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="23bf3-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="23bf3-111">dans Nombre d’octets écrits dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="23bf3-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="23bf3-112">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="23bf3-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="23bf3-113">à Pointeur vers le tableau d’octets qui contient les données.</span><span class="sxs-lookup"><span data-stu-id="23bf3-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="23bf3-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="23bf3-114">Return value</span></span>

<span data-ttu-id="23bf3-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="23bf3-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="23bf3-116">Constante</span><span class="sxs-lookup"><span data-stu-id="23bf3-116">Constant</span></span>  |<span data-ttu-id="23bf3-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="23bf3-117">Value</span></span>  |<span data-ttu-id="23bf3-118">Description</span><span class="sxs-lookup"><span data-stu-id="23bf3-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="23bf3-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="23bf3-119">0x80041008</span></span> | <span data-ttu-id="23bf3-120">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="23bf3-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="23bf3-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="23bf3-121">0x80041005</span></span> | <span data-ttu-id="23bf3-122">Une incompatibilité de type s’est produite.</span><span class="sxs-lookup"><span data-stu-id="23bf3-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="23bf3-123">0</span><span class="sxs-lookup"><span data-stu-id="23bf3-123">0</span></span> | <span data-ttu-id="23bf3-124">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="23bf3-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="23bf3-125">Notes</span><span class="sxs-lookup"><span data-stu-id="23bf3-125">Remarks</span></span>

<span data-ttu-id="23bf3-126">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .</span><span class="sxs-lookup"><span data-stu-id="23bf3-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="23bf3-127">Utilisez cette fonction pour définir la chaîne et toutes les autres`DWORD` `QWORD` données non ou non.</span><span class="sxs-lookup"><span data-stu-id="23bf3-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="23bf3-128">Pour les valeurs de propriété qui `lNumBytes` ne sont pas de type chaîne, doit être la bonne taille de données du type de propriété spécifié.</span><span class="sxs-lookup"><span data-stu-id="23bf3-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="23bf3-129">Pour les valeurs de propriété `lNumBytes` de type chaîne, doit correspondre à la longueur de la chaîne spécifiée en octets, et la chaîne elle-même doit être de longueur égale en octets et être suivie d’un caractère de fin null.</span><span class="sxs-lookup"><span data-stu-id="23bf3-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="23bf3-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="23bf3-130">Requirements</span></span>  
<span data-ttu-id="23bf3-131">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23bf3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23bf3-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="23bf3-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="23bf3-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="23bf3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bf3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23bf3-134">See also</span></span>

- [<span data-ttu-id="23bf3-135">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="23bf3-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
