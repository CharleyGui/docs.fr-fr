---
title: Fonction GetTypeLibInfo
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: 4f05eb2e6ef31cf1993a623c38bb177f7e3c297e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935649"
---
# <a name="gettypelibinfo-function"></a>Fonction GetTypeLibInfo
Retourne des informations sur la bibliothèque de types spécifiée en examinant sa structure [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `szFile`  
 dans Nom de fichier de la bibliothèque de types.  
  
 `pTypeLibID`  
 à GUID de la bibliothèque de types.  
  
 `pTypeLibLCID`  
 à ID de localisation de la bibliothèque de types.  
  
 `pTypeLibPlatform`  
 à Indicateur [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) qui identifie le système d’exploitation cible de la bibliothèque de types. Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 à Numéro de version principale de la bibliothèque de types. Par exemple, pour la version *x. y*, le numéro de version principale est *x*.  
  
 `pTypeLibMinorVer`  
 à Numéro de version mineure de la bibliothèque de types. Par exemple, pour la version *x. y*, le numéro de version mineure est *y*.  
  
## <a name="remarks"></a>Notes  
 La fonction `GetTypeLibInfo` est appelée par [Tlbexp. exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md). Cet outil génère une bibliothèque de types qui décrit les types dans un assembly common language runtime (CLR).  
  
 Si un paramètre a la valeur null, la fonction retourne une `HRESULT` de `E_POINTER`. Sinon, il retourne `S_OK`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** TlbRef. h  
  
 **Bibliothèque :** TlbRef. lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’assistance Tlbexp](index.md)
- [LoadTypeLibEx fonction)](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
