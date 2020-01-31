---
title: Fonctions statiques globales de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: c20d8719b63cb40074dc740506ae4a3c0fc3a251
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793779"
---
# <a name="debugging-global-static-functions"></a>Fonctions statiques globales de débogage
Cette section décrit les fonctions statiques globales non managées utilisées par l'API de débogage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [_EFN_GetManagedExcepStack, fonction](efn-getmanagedexcepstack-function.md)  
 Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.  
  
 [_EFN_GetManagedObjectFieldInfo, fonction](efn-getmanagedobjectfieldinfo-function.md)  
 Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.  
  
 [_EFN_GetManagedObjectName, fonction](efn-getmanagedobjectname-function.md)  
 Obtient le nom d'un type à l'aide du pointeur d'objet managé fourni.  
  
 [_EFN_StackTrace, fonction](efn-stacktrace-function.md)  
 Fournit une représentation textuelle d'une trace de pile managée et un tableau d'enregistrements `CONTEXT` pour chaque transition entre du code non managé et du code managé.  
  
 [CLRDataCreateInstance, fonction](clrdatacreateinstance-function.md)  
 Appelé par les services d'accès aux données du Common Language Runtime (CLR) pour créer l'objet d'interface spécifié pour le processus cible spécifié.  
  
 [PFN_CLRDataCreateInstance, pointeur fonction](pfn-clrdatacreateinstance-function-pointer.md)  
 Pointe vers une fonction qui est appelée par les services d'accès aux données du CLR pour créer l'objet d'interface indiqué pour le processus cible spécifié.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses de débogage](debugging-coclasses.md)  
  
 [Interfaces de débogage](debugging-interfaces.md)  
  
 [Énumérations de débogage](debugging-enumerations.md)  
  
 [Structures de débogage](debugging-structures.md)
