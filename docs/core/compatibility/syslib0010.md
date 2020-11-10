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
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010 : API de communication à distance non prises en charge

[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) est une technologie héritée, et l’infrastructure existe uniquement dans .NET Framework. Les API liées à la communication à distance suivantes sont marquées comme obsolètes, à partir de .NET 5,0. Leur utilisation dans le code génère un avertissement `SYSLIB0010` au moment de la compilation.

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a>Solutions de contournement

Envisagez d’utiliser des services REST WCF ou HTTP pour communiquer avec des objets dans d’autres applications ou sur plusieurs ordinateurs. Pour plus d’informations, consultez [.NET Framework technologies indisponibles sur .net Core](../porting/net-framework-tech-unavailable.md).

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
