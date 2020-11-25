---
title: CreateAssemblyNameObject, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 995f1064c2f40005c4a19ef034d7edfd668b5d51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704160"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="d594a-102">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="d594a-102">CreateAssemblyNameObject Function</span></span>

<span data-ttu-id="d594a-103">Obtient un pointeur d’interface vers une instance de [IAssemblyName](iassemblyname-interface.md) qui représente l’identité unique de l’assembly avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="d594a-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d594a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d594a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d594a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d594a-105">Parameters</span></span>  

 `ppAssemblyNameObj`  
 <span data-ttu-id="d594a-106">à Retourné `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="d594a-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d594a-107">dans Nom de l’assembly pour lequel la nouvelle instance doit être créée `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="d594a-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d594a-108">dans Indicateurs à passer au constructeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d594a-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d594a-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="d594a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d594a-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="d594a-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d594a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d594a-111">Requirements</span></span>  

 <span data-ttu-id="d594a-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d594a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d594a-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d594a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d594a-114">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d594a-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d594a-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d594a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d594a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d594a-116">See also</span></span>

- [<span data-ttu-id="d594a-117">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="d594a-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="d594a-118">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="d594a-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
