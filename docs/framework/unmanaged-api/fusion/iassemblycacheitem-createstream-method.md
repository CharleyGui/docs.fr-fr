---
title: IAssemblyCacheItem::CreateStream, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af7dc4e1694b66fc4a5ce37e515c71e9fa3db49
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796729"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="87be4-102">IAssemblyCacheItem::CreateStream, méthode</span><span class="sxs-lookup"><span data-stu-id="87be4-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="87be4-103">Crée un flux de donnée avec le nom et le format spécifiés.</span><span class="sxs-lookup"><span data-stu-id="87be4-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="87be4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87be4-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="87be4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87be4-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="87be4-106">dans Indicateurs définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="87be4-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="87be4-107">dans Nom du flux à créer.</span><span class="sxs-lookup"><span data-stu-id="87be4-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="87be4-108">dans Format du fichier à diffuser en continu.</span><span class="sxs-lookup"><span data-stu-id="87be4-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="87be4-109">dans Indicateurs spécifiques au format définis dans fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="87be4-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="87be4-110">à Pointeur vers l’adresse de l’instance [IStream](/windows/desktop/api/objidl/nn-objidl-istream) retournée.</span><span class="sxs-lookup"><span data-stu-id="87be4-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="87be4-111">[in, facultatif] Taille maximale du flux référencé par `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="87be4-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="87be4-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="87be4-112">Requirements</span></span>

<span data-ttu-id="87be4-113">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87be4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="87be4-114">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="87be4-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="87be4-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87be4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="87be4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87be4-116">See also</span></span>

- [<span data-ttu-id="87be4-117">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="87be4-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
