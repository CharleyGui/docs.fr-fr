---
title: CreateALink, fonction
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446556"
---
# <a name="createalink-function"></a>CreateALink, fonction
Crée une instance de l’Assembly Linker et définit un pointeur vers l’interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`riid`|Nom physique de l’une des interfaces de l’éditeur de liens de l’assembly.|  
|`ppInterface`|Emplacement qui, en cas de réussite de l’opération, contient un pointeur vers l’interface `riid`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Bibliothèque**: ALink. dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
