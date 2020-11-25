---
title: Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 9386918f3574720d90bda7e8da592fa0c91160e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708242"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)

L’[outil Type Library Exporter](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) charge une bibliothèque de liens dynamiques nommée TlbRef.dll. Cette DLL contient deux fonctions d’assistance et une interface que l’outil exportateur utilise pendant le processus de conversion de l’assembly à la bibliothèque de types.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Fonction GetTypeLibInfo](gettypelibinfo-function.md)  
 Fournit des informations sur la localisation et le système d’exploitation pour une bibliothèque de types.  
  
 [LoadTypeLibWithResolver, fonction](loadtypelibwithresolver-function.md)  
 Charge une bibliothèque de types à l’aide d’une implémentation de l’[interface ITypeLibResolver](itypelibresolver-interface.md) pour résoudre tous les types de bibliothèques référencés.  
  
 [ITypeLibResolver, interface](itypelibresolver-interface.md)  
 Fournit la [méthode ResolveTypeLib](resolvetypelib-method.md), qui retourne le chemin d’accès complet d’une bibliothèque de types.
