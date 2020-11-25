---
title: CorDebugRegister, énumération
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 85df98e83396c9439c28dd41a3ffa02b820c9c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726052"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister, énumération

Spécifie les registres associés à une architecture de processeur donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|Registre de pointeur d'instruction sur un processeur.|  
|`REGISTER_STACK_POINTER`|Registre de pointeur de pile sur un processeur.|  
|`REGISTER_FRAME_POINTER`|Registre de pointeur de trame sur un processeur.|  
|`REGISTER_X86_EIP`|Registre de pointeur d'instruction sur le processeur x86.|  
|`REGISTER_X86_ESP`|Registre de pointeur de pile sur le processeur x86.|  
|`REGISTER_X86_EBP`|Registre de pointeur de base sur le processeur x86.|  
|`REGISTER_X86_EAX`|Registre de données A sur le processeur x86.|  
|`REGISTER_X86_ECX`|Registre de données C sur le processeur x86.|  
|`REGISTER_X86_EDX`|Registre de données D sur le processeur x86.|  
|`REGISTER_X86_EBX`|Registre de données B sur le processeur x86.|  
|`REGISTER_X86_ESI`|Registre d'index source sur le processeur x86.|  
|`REGISTER_X86_EDI`|Registre d'index de destination sur le processeur x86.|  
|`REGISTER_X86_FPSTACK_0`|Registre de pile 0 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_1`|Registre de pile n° 1 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_2`|Registre de pile n° 2 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_3`|Registre de pile n° 3 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_4`|Registre de pile n° 4 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_5`|Registre de pile n° 5 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_6`|Registre de pile n° 6 sur le processeur à virgule flottante x86.|  
|`REGISTER_X86_FPSTACK_7`|Registre de pile n° 7 sur le processeur à virgule flottante x86.|  
|`REGISTER_AMD64_RIP`|Registre de pointeur d'instruction sur le processeur AMD64.|  
|`REGISTER_AMD64_RSP`|Registre de pointeur de pile sur le processeur AMD64.|  
|`REGISTER_AMD64_RBP`|Registre de pointeur de base sur le processeur AMD64.|  
|`REGISTER_AMD64_RAX`|Registre de données A sur le processeur AMD64.|  
|`REGISTER_AMD64_RCX`|Registre de données C sur le processeur AMD64.|  
|`REGISTER_AMD64_RDX`|Registre de données D sur le processeur AMD64.|  
|`REGISTER_AMD64_RBX`|Registre de données B sur le processeur AMD64.|  
|`REGISTER_AMD64_RSI`|Registre d'index source sur le processeur AMD64.|  
|`REGISTER_AMD64_RDI`|Registre d'index de destination sur le processeur AMD64.|  
|`REGISTER_AMD64_R8`|Registre de données n° 8 sur le processeur AMD64.|  
|`REGISTER_AMD64_R9`|Registre de données n° 9 sur le processeur AMD64.|  
|`REGISTER_AMD64_R10`|Registre de données n° 10 sur le processeur AMD64.|  
|`REGISTER_AMD64_R11`|Registre de données n° 11 sur le processeur AMD64.|  
|`REGISTER_AMD64_R12`|Registre de données n° 12 sur le processeur AMD64.|  
|`REGISTER_AMD64_R13`|Registre de données n° 13 sur le processeur AMD64.|  
|`REGISTER_AMD64_R14`|Registre de données n° 14 sur le processeur AMD64.|  
|`REGISTER_AMD64_R15`|Registre de données n° 15 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM0`|Registre multimédia n° 0 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM1`|Registre multimédia n° 1 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM2`|Registre multimédia n° 2 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM3`|Registre multimédia n° 3 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM4`|Registre multimédia n° 4 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM5`|Registre multimédia n° 5 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM6`|Registre multimédia n° 6 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM7`|Registre multimédia n° 7 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM8`|Registre multimédia n° 8 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM9`|Registre multimédia n° 9 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM10`|Registre multimédia n° 10 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM11`|Registre multimédia n° 11 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM12`|Registre multimédia n° 12 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM13`|Registre multimédia n° 13 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM14`|Registre multimédia n° 14 sur le processeur AMD64.|  
|`REGISTER_AMD64_XMM15`|Registre multimédia n° 15 sur le processeur AMD64.|  
|`REGISTER_IA64_BSP`|Registre de pointeur de pile sur le processeur IA-64.|  
|`REGISTER_IA64_R0`|Registre de données n° 0 sur le processeur IA-64.|  
|`REGISTER_IA64_F0`|Registre de données en virgule flottante n° 0 sur le processeur IA-64.|  
|`REGISTER_ARM_PC`|Registre de compteur de programme (R15) sur le processeur ARM.|  
|`REGISTER_ARM_SP`|Registre de pointeur de pile (R13) sur le processeur ARM.|  
|`REGISTER_ARM_R0`|Registre de données R0 sur le processeur ARM.|  
|`REGISTER_ARM_R1`|Registre de données R1 sur le processeur ARM.|  
|`REGISTER_ARM_R2`|Registre de données R2 sur le processeur ARM.|  
|`REGISTER_ARM_R3`|Registre de données R3 sur le processeur ARM.|  
|`REGISTER_ARM_R4`|Registre R4 sur le processeur ARM.|  
|`REGISTER_ARM_R5`|Registre R5 sur le processeur ARM.|  
|`REGISTER_ARM_R6`|Registre R6 sur le processeur ARM.|  
|`REGISTER_ARM_R7`|Registre R7 (le pointeur de trame THUMB) sur le processeur ARM.|  
|`REGISTER_ARM_R8`|Registre R8 sur le processeur ARM.|  
|`REGISTER_ARM_R9`|Registre R9 sur le processeur ARM.|  
|`REGISTER_ARM_R10`|Registre R10 sur le processeur ARM.|  
|`REGISTER_ARM_R11`|Pointeur de trame sur le processeur ARM.|  
|`REGISTER_ARM_R12`|Registre R12 sur le processeur ARM.|  
|`REGISTER_ARM_LR`|Registre de lien (R14) sur le processeur ARM.|  
  
## <a name="remarks"></a>Remarques  

 Il existe 128 registres de données d'utilisation générale et 128 registres de données en virgule flottante sur le processeur IA-64, mais seules les valeurs `REGISTER_IA64_R0` et `REGISTER_IA64_F0` sont spécifiées. Les autres valeurs peuvent être déterminées comme suit :  
  
- Ajoutez le numéro de registre à `REGISTER_IA64_R0` pour les valeurs allant de `REGISTER_IA64_R1` à `REGISTER_IA64_R127`, qui correspondent aux registres de données n° 1 à 127 sur le processeur IA-64.  
  
- Ajoutez le numéro de registre à `REGISTER_IA64_F0` pour les valeurs allant de `REGISTER_IA64_F1` à `REGISTER_IA64_F127`, qui correspondent aux registres de données en virgule flottante n° 1 à 127 sur le processeur IA-64.  
  
 Par exemple, si vous devez spécifier le registre de données n° 83 sur le processeur IA-64, utilisez `REGISTER_IA64_R0` + 83.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
