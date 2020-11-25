---
title: ISymUnmanagedVariable, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 93e1f8eb17f06e42ddb243f88c593979fcb28030
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733280"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable, interface

Représente une variable, comme un paramètre, une variable locale ou un champ.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddressField1, méthode](isymunmanagedvariable-getaddressfield1-method.md)|Obtient le premier champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.|  
|[GetAddressField2, méthode](isymunmanagedvariable-getaddressfield2-method.md)|Obtient le deuxième champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.|  
|[GetAddressField3, méthode](isymunmanagedvariable-getaddressfield3-method.md)|Obtient le troisième champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.|  
|[GetAddressKind, méthode](isymunmanagedvariable-getaddresskind-method.md)|Obtient le type d’adresse de cette variable.|  
|[GetAttributes, méthode](isymunmanagedvariable-getattributes-method.md)|Obtient les indicateurs d’attribut pour cette variable.|  
|[GetEndOffset, méthode](isymunmanagedvariable-getendoffset-method.md)|Obtient le décalage de fin de cette variable dans son parent.|  
|[GetName, méthode](isymunmanagedvariable-getname-method.md)|Obtient le nom de cette variable.|  
|[GetSignature, méthode](isymunmanagedvariable-getsignature-method.md)|Obtient la signature de cette variable.|  
|[GetStartOffset, méthode](isymunmanagedvariable-getstartoffset-method.md)|Obtient le décalage de début de cette variable dans son parent.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
