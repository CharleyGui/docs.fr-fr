---
title: IMetaDataTables::GetUserString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501142"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="660c1-102">IMetaDataTables::GetUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="660c1-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="660c1-103">Obtient la chaîne codée en dur à l’index spécifié dans la colonne de chaîne de l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="660c1-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="660c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="660c1-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="660c1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="660c1-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="660c1-106">dans Valeur d’index à partir de laquelle la chaîne codée en dur sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="660c1-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="660c1-107">à Pointeur vers la taille de `ppData` .</span><span class="sxs-lookup"><span data-stu-id="660c1-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="660c1-108">à Pointeur vers un pointeur vers la chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="660c1-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="660c1-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="660c1-109">Requirements</span></span>

<span data-ttu-id="660c1-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="660c1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="660c1-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="660c1-111">**Header:** Cor.h</span></span>

<span data-ttu-id="660c1-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="660c1-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="660c1-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="660c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="660c1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="660c1-114">See also</span></span>

- [<span data-ttu-id="660c1-115">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="660c1-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="660c1-116">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="660c1-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
