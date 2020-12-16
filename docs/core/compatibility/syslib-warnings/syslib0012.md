---
title: AVERTISSEMENT SYSLIB0012
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0012.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9b3fa94029efb2343e6dbbeb3ae36195f0956523
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596488"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012 : assembly. CodeBase et assembly. EscapedCodeBase sont obsolètes

Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. Leur utilisation dans le code génère un avertissement `SYSLIB0012` au moment de la compilation.

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>Solutions de contournement

Utilisez plutôt <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
