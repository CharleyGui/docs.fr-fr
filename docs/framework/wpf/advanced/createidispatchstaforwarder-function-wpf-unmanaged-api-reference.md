---
title: Fonction CreateIDispatchSTAForwarder-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738027"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder, fonction (référence des API non managées WPF)
Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion des threads et de Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Parameters  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 pDispatchDelegate  
 Pointeur vers une interface de `IDispatch`.  
  
 ppForwarder  
 Pointeur vers l’adresse d’une interface de `IDispatch`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll  
  
 Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll  
  
 **Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence des API non managées WPF](wpf-unmanaged-api-reference.md)
