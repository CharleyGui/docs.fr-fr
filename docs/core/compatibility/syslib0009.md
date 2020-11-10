---
title: AVERTISSEMENT SYSLIB0009
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0009.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439974"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a><span data-ttu-id="14265-103">SYSLIB0009 : les méthodes d’authentification et de pré-authentification du AuthenticationManager ne sont pas prises en charge</span><span class="sxs-lookup"><span data-stu-id="14265-103">SYSLIB0009: The AuthenticationManager Authenticate and PreAuthenticate methods are not supported</span></span>

<span data-ttu-id="14265-104">Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="14265-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="14265-105">L’utilisation de ces API génère un avertissement `SYSLIB0009` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="14265-105">Use of these APIs generates warning `SYSLIB0009` at compile time.</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a><span data-ttu-id="14265-106">Supprimer l’avertissement</span><span class="sxs-lookup"><span data-stu-id="14265-106">Suppress the warning</span></span>

<span data-ttu-id="14265-107">Si vous ne pouvez pas modifier votre code, vous pouvez supprimer l’avertissement à l’aide d’une `#pragma` directive ou d’un `<NoWarn>` paramètre de projet.</span><span class="sxs-lookup"><span data-stu-id="14265-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="14265-108">Pour obtenir des exemples, consultez [supprimer des avertissements](syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="14265-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
