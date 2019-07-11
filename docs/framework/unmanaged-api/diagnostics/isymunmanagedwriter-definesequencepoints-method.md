---
title: ISymUnmanagedWriter::DefineSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f07685351425a4685ac4a0c8e1b8e3c198b14187
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777298"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints, méthode
Définit un groupe de points de séquence dans la méthode actuelle. Chaque ligne de début et de la colonne de départ définit le début d’une instruction dans une méthode. Chaque ligne de fin et la colonne de fin définissent la fin d’une instruction dans une méthode. Les tableaux doivent être triés dans l’ordre croissant des offsets. L’offset est toujours mesuré depuis le début de la méthode, en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `document`  
 [in] L’objet de document pour lequel les points de séquence sont définies.  
  
 `spCount`  
 [in] Un `ULONG32` qui indique la taille de la `offsets`, `lines`, `columns`, `endLines`, et `endColumns` mémoires tampons.  
  
 `offsets`  
 [in] Le décalage des points de séquence mesuré à partir du début de la méthode.  
  
 `lines`  
 [in] Les numéros de ligne de début des points de séquence.  
  
 `columns`  
 [in] Les numéros de colonne de départ des points de séquence.  
  
 `endLines`  
 [in] Les numéros de ligne de fin des points de séquence. Ce paramètre est optionnel.  
  
 `endColumns`  
 [in] Les numéros de colonne de fin des points de séquence. Ce paramètre est optionnel.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
