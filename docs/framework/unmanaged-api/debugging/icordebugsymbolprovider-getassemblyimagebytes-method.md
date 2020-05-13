---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: a555acb9e23098b0a0f70924032771b1ae18e88e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376117"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode
Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `rva`  
 [in] Adresse virtuelle relative (RVA) dans un assembly fusionné.  
  
 `length`  
 Nombre d'octets à lire à partir de l'assembly fusionné.  
  
 `ppMemoryBuffer`  
 Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) qui contient des informations sur la mémoire tampon avec les métadonnées de l’assembly fusionné.  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugSymbolProvider, interface](icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
