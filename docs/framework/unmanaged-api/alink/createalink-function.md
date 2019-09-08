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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787616"
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
|`ppInterface`|Emplacement qui, en cas de réussite de l’opération, `riid` contient un pointeur vers l’interface.|  
  
## <a name="requirements"></a>Configuration requise  
 **Bibliothèque**: ALink. dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
