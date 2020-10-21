---
title: AVERTISSEMENT SYSLIB0012
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0012.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2ed93b6eefbaa861faca319f0cc9bf19ac741f3b
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333263"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="46fe8-103">SYSLIB0012 : assembly. CodeBase et assembly. EscapedCodeBase sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="46fe8-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="46fe8-104">Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="46fe8-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="46fe8-105">Leur utilisation dans le code génère un avertissement `SYSLIB0012` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="46fe8-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

<span data-ttu-id="46fe8-106">Solution de contournement</span><span class="sxs-lookup"><span data-stu-id="46fe8-106">Workaround</span></span>

<span data-ttu-id="46fe8-107">Utilisez plutôt <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46fe8-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>
