---
title: AVERTISSEMENT SYSLIB0012
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0012.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dc139d5c5cb6d6a34d161147b350b3324d15117e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440580"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a>SYSLIB0012 : assembly. CodeBase et assembly. EscapedCodeBase sont obsolètes

Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. Leur utilisation dans le code génère un avertissement `SYSLIB0012` au moment de la compilation.

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a>Solutions de contournement

Utilisez plutôt <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
