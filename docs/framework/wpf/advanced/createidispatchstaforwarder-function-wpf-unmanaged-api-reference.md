---
title: CreateIDispatchSTAForwarder Function - WPF non gestiond API référence
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174717"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)
Cette API prend en charge l’infrastructure de la Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure de la Windows Presentation Foundation (WPF) pour la gestion des fils et des fenêtres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Paramètres  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 pDispatchDelegate  
 Un pointeur `IDispatch` à une interface.  
  
 ppForwarder  
 Un pointeur à `IDispatch` l’adresse d’une interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plates-formes:** Voir [.NET Framework System Requirements](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 Dans le cadre .NET 3.0 et 3.5: PresentationHostDLL.dll  
  
 Dans le cadre .NET 4 et plus tard: PresentationHost_v0400.dll  
  
 **Version cadre .NET:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les API non managées WPF](wpf-unmanaged-api-reference.md)
