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
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="daf67-103">SYSLIB0012 : assembly. CodeBase et assembly. EscapedCodeBase sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="daf67-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="daf67-104">Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="daf67-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="daf67-105">Leur utilisation dans le code génère un avertissement `SYSLIB0012` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="daf67-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="daf67-106">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="daf67-106">Workarounds</span></span>

<span data-ttu-id="daf67-107">Utilisez plutôt <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf67-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
