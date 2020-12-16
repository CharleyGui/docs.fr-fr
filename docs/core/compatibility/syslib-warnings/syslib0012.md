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
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="4fc27-103">SYSLIB0012 : assembly. CodeBase et assembly. EscapedCodeBase sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="4fc27-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="4fc27-104">Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="4fc27-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="4fc27-105">Leur utilisation dans le code génère un avertissement `SYSLIB0012` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="4fc27-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="4fc27-106">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="4fc27-106">Workarounds</span></span>

<span data-ttu-id="4fc27-107">Utilisez plutôt <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4fc27-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
