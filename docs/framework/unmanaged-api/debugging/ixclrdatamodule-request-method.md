---
title: 'IXCLRDataModule :: Request, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420810"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="2fb39-102">IXCLRDataModule :: Request, méthode</span><span class="sxs-lookup"><span data-stu-id="2fb39-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="2fb39-103">Demandes de remplissage de la mémoire tampon donnée avec les données du module.</span><span class="sxs-lookup"><span data-stu-id="2fb39-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2fb39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fb39-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="2fb39-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fb39-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="2fb39-106">dans Type de demande à envoyer.</span><span class="sxs-lookup"><span data-stu-id="2fb39-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="2fb39-107">[in] taille de la mémoire tampon d’entrée à passer.</span><span class="sxs-lookup"><span data-stu-id="2fb39-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="2fb39-108">[in, size_is (inBufferSize)] Pointeur de mémoire tampon pour les données brutes à envoyer dans la demande.</span><span class="sxs-lookup"><span data-stu-id="2fb39-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="2fb39-109">dans Taille de la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="2fb39-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="2fb39-110">[out, size_is (outBufferSize)] Pointeur de la mémoire tampon à utiliser pour stocker la réponse à la demande.</span><span class="sxs-lookup"><span data-stu-id="2fb39-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fb39-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2fb39-111">Remarks</span></span>

<span data-ttu-id="2fb39-112">La méthode fournie fait partie de l' `IXCLRDataModule` interface et correspond à l’emplacement 37th de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="2fb39-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2fb39-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="2fb39-113">Requirements</span></span>

<span data-ttu-id="2fb39-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fb39-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="2fb39-115">**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb39-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb39-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fb39-116">See also</span></span>

- [<span data-ttu-id="2fb39-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="2fb39-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="2fb39-118">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="2fb39-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
