---
title: AVERTISSEMENT SYSLIB0008
description: En savoir plus sur le obsoletion qui génère des SYSLIB0008 d’avertissement au moment de la compilation.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2b573f4b28cdf79107395f5cb38a4226d0ccc11e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596491"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a>SYSLIB0008 : CreatePdbGenerator n’est pas pris en charge

L' <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API est marquée comme obsolète, à partir de .net 5,0. L’utilisation de cette API génère un avertissement `SYSLIB0008` au moment de la compilation.

## <a name="suppress-the-warning"></a>Supprimer l’avertissement

Si vous ne pouvez pas modifier votre code, vous pouvez supprimer l’avertissement à l’aide d’une `#pragma` directive ou d’un `<NoWarn>` paramètre de projet. Pour obtenir des exemples, consultez [supprimer des avertissements](../syslib-obsoletions.md#suppress-warnings).
