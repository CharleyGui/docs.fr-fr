---
title: Types de données communs (Référence des API non managées)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
ms.openlocfilehash: 5c00ff6d0947b5d847a9622dce02bd310491818c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673980"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Types de données communs (Référence des API non managées)

Cette rubrique répertorie les types de données simples utilisés par les API non managées pour .NET Framework, qui sont définis par des instructions `typedef` en C/C++. Ces types de données sont généralement des alias pour des types de données primitifs C/C++. Les valeurs de ces types de données sont en général opaques, c'est-à-dire qu'elles sont retournées par une fonction ou une méthode particulière pour pouvoir être passées à d'autres fonctions ou méthodes sans modification.  
  
|Type de données|Définition|Défini dans|Description|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|L'identificateur d'un domaine d'application.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|L'identificateur d'un assembly.|  
|ClassID|`typedef UINT_PTR ClassID;`|corprof.h|L'identificateur d'une classe managée.|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|Clrdata. h|Adresse mémoire 64 bits.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Non disponible|Adresse mémoire 64 bits.|
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|L'identificateur de connexion pour un thread qui est connecté à une instance de Microsoft SQL Server.|  
|ContextID|`typedef UINT_PTR ContextID;`|corprof.h|L'identificateur du contexte associé à un thread managé particulier.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Un handle opaque qui représente des informations sur un frame de pile particulier.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Un handle opaque qui pointe vers un frame de pile. Il est valide seulement pendant le rappel auquel il est passé.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Une adresse en mémoire.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|État de la continuation.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|La valeur d'un registre du processeur.|
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|L'identificateur d'une fonction ou d'une méthode.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Un handle de récupération de mémoire.|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|cordebug.h|Jeton de définition de méthode.|
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Un jeton de métadonnées (une ligne dans une table de métadonnées).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|L'identificateur d'un module d'assembly.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|L'identificateur d'un objet.|  
|PCCOR_SIGNATURE|`typedef SIZE_T PCCOR_SIGNATURE;`|cordebug.h|Pointeur vers une signature de membre ou de métadonnées.|
|ProcessID|`typedef UINT_PTR ProcessID;`|corprof.h|L'identificateur d'un processus managé.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identificateur d'une fonction traitée juste-à-temps.|  
|SIZE_T|`typedef ULONG_PTR SIZE_T;`|CorSym. h|Pointeur vers une adresse mémoire 64 bits.|
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Identificateur d’une instance d' [ICLRTask](./hosting/iclrtask-interface.md) .|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|L'identificateur d'un thread managé.|  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les API non managées](index.md)
