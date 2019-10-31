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
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134473"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream, méthode

Crée un flux de donnée avec le nom et le format spécifiés.

## <a name="syntax"></a>Syntaxe

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

## <a name="parameters"></a>Paramètres

`dwFlags`\
dans Indicateurs définis dans fusion. idl.

`pszStreamName`\
dans Nom du flux à créer.

`dwFormat`\
dans Format du fichier à diffuser en continu.

`dwFormatFlags`\
dans Indicateurs spécifiques au format définis dans fusion. idl.

`ppIStream`\
à Pointeur vers l’adresse de l’instance [IStream](/windows/desktop/api/objidl/nn-objidl-istream) retournée.

`puliMaxSize`\
[in, facultatif] Taille maximale du flux référencé par `ppIStream`.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** Fusion. h

**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [IAssemblyCacheItem, interface](iassemblycacheitem-interface.md)
