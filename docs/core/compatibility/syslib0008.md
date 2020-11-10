---
title: AVERTISSEMENT SYSLIB0008
description: En savoir plus sur le obsoletion qui génère des SYSLIB0008 d’avertissement au moment de la compilation.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440593"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a><span data-ttu-id="79fd4-103">SYSLIB0008 : CreatePdbGenerator n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="79fd4-103">SYSLIB0008: CreatePdbGenerator is not supported</span></span>

<span data-ttu-id="79fd4-104">L' <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API est marquée comme obsolète, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="79fd4-104">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API is marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="79fd4-105">L’utilisation de cette API génère un avertissement `SYSLIB0008` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="79fd4-105">Using this API generates warning `SYSLIB0008` at compile time.</span></span>

## <a name="suppress-the-warning"></a><span data-ttu-id="79fd4-106">Supprimer l’avertissement</span><span class="sxs-lookup"><span data-stu-id="79fd4-106">Suppress the warning</span></span>

<span data-ttu-id="79fd4-107">Si vous ne pouvez pas modifier votre code, vous pouvez supprimer l’avertissement à l’aide d’une `#pragma` directive ou d’un `<NoWarn>` paramètre de projet.</span><span class="sxs-lookup"><span data-stu-id="79fd4-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="79fd4-108">Pour obtenir des exemples, consultez [supprimer des avertissements](syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="79fd4-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
