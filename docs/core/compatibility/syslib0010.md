---
title: AVERTISSEMENT SYSLIB0010
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0010.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 824423d58802d4a286bfed98422341097985990f
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440606"
---
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="cdf15-103">SYSLIB0010 : API de communication à distance non prises en charge</span><span class="sxs-lookup"><span data-stu-id="cdf15-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="cdf15-104">[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) est une technologie héritée, et l’infrastructure existe uniquement dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdf15-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="cdf15-105">Les API liées à la communication à distance suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="cdf15-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="cdf15-106">Leur utilisation dans le code génère un avertissement `SYSLIB0010` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="cdf15-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="cdf15-107">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="cdf15-107">Workarounds</span></span>

<span data-ttu-id="cdf15-108">Envisagez d’utiliser des services REST WCF ou HTTP pour communiquer avec des objets dans d’autres applications ou sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="cdf15-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="cdf15-109">Pour plus d’informations, consultez [.NET Framework technologies indisponibles sur .net Core](../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="cdf15-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="cdf15-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdf15-110">See also</span></span>

- <span data-ttu-id="cdf15-111">[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="cdf15-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
