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
ms.openlocfilehash: 98c6ed4657dc69554a9fcca27145f65c621492f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683729"
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
|`ppInterface`|Emplacement qui, en cas de réussite de l’opération, contient un pointeur vers l' `riid` interface.|  
  
## <a name="requirements"></a>Configuration requise  

 **Bibliothèque**: alink.dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
