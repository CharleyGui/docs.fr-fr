---
title: ISymUnmanagedWriter::SetUserEntryPoint, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: a1c3506758221c3a2b578d93488a4377c1b86a21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683496"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a>ISymUnmanagedWriter::SetUserEntryPoint, méthode

Spécifie la méthode définie par l’utilisateur qui est le point d’entrée de ce module. Par exemple, ce point d’entrée peut être la méthode main de l’utilisateur au lieu des stubs générés par le compilateur avant main.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a>Paramètres  

 `entryMethod`  
 dans Jeton de métadonnées pour la méthode qui est le point d’entrée de l’utilisateur.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
