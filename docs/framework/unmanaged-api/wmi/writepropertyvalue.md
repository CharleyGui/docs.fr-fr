---
title: Fonction WritePropertyValue (Référence API non gestion)
description: La fonction WritePropertyValue écrit des octets à une propriété.
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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174834"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="a4d57-103">WritePropertyValue, fonction</span><span class="sxs-lookup"><span data-stu-id="a4d57-103">WritePropertyValue function</span></span>
<span data-ttu-id="a4d57-104">Écrit un nombre spécifié d’octets dans une propriété identifiée par un descripteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="a4d57-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a4d57-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4d57-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="a4d57-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4d57-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a4d57-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="a4d57-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a4d57-108">[dans] Un pointeur à une instance [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)</span><span class="sxs-lookup"><span data-stu-id="a4d57-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="a4d57-109">[dans] Un intégrier qui contient la poignée qui identifie cette propriété.</span><span class="sxs-lookup"><span data-stu-id="a4d57-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="a4d57-110">Le manche peut être récupéré en appelant la fonction [GetPropertyHandle.](getpropertyhandle.md)</span><span class="sxs-lookup"><span data-stu-id="a4d57-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="a4d57-111">[dans] Le nombre d’octets écrits à la propriété.</span><span class="sxs-lookup"><span data-stu-id="a4d57-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="a4d57-112">Consultez la section [Remarques](#remarks) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="a4d57-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="a4d57-113">`pHandle`[out] Un pointeur vers le tableau d’en-avant qui contient les données.</span><span class="sxs-lookup"><span data-stu-id="a4d57-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="a4d57-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="a4d57-114">Return value</span></span>

<span data-ttu-id="a4d57-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="a4d57-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a4d57-116">Constant</span><span class="sxs-lookup"><span data-stu-id="a4d57-116">Constant</span></span>  |<span data-ttu-id="a4d57-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="a4d57-117">Value</span></span>  |<span data-ttu-id="a4d57-118">Description</span><span class="sxs-lookup"><span data-stu-id="a4d57-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a4d57-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a4d57-119">0x80041008</span></span> | <span data-ttu-id="a4d57-120">Un paramètre n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="a4d57-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="a4d57-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="a4d57-121">0x80041005</span></span> | <span data-ttu-id="a4d57-122">Une incompatibilité de type est survenue.</span><span class="sxs-lookup"><span data-stu-id="a4d57-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a4d57-123">0</span><span class="sxs-lookup"><span data-stu-id="a4d57-123">0</span></span> | <span data-ttu-id="a4d57-124">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="a4d57-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a4d57-125">Notes </span><span class="sxs-lookup"><span data-stu-id="a4d57-125">Remarks</span></span>

<span data-ttu-id="a4d57-126">Cette fonction enveloppe un appel à [l’IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) méthode.</span><span class="sxs-lookup"><span data-stu-id="a4d57-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="a4d57-127">Utilisez cette fonction pour définir la`DWORD` chaîne`QWORD` et toutes les autres données non ou non.</span><span class="sxs-lookup"><span data-stu-id="a4d57-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="a4d57-128">Pour les valeurs des `lNumBytes` propriétés noncordes, doit être la bonne taille de données du type de propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a4d57-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="a4d57-129">Pour les valeurs `lNumBytes` de propriété de chaîne, doit être la longueur de la chaîne spécifiée dans les octets, et la chaîne elle-même doit être d’une longueur égale dans les octets et être suivie avec un caractère de terminaison nulle.</span><span class="sxs-lookup"><span data-stu-id="a4d57-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4d57-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a4d57-130">Requirements</span></span>  
<span data-ttu-id="a4d57-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d57-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d57-132">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a4d57-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a4d57-133">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d57-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d57-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4d57-134">See also</span></span>

- [<span data-ttu-id="a4d57-135">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="a4d57-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
