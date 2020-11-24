---
title: AVERTISSEMENT SYSLIB0011
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0011.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 99cdd9f5335f71eb9325039891db17972fb48532
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685004"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="8f06b-103">SYSLIB0011 : la sérialisation BinaryFormatter est obsolète</span><span class="sxs-lookup"><span data-stu-id="8f06b-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="8f06b-104">En raison de [failles de sécurité](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) dans <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , les API suivantes sont marquées comme obsolètes, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="8f06b-104">Due to [security vulnerabilities](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="8f06b-105">Leur utilisation dans le code génère un avertissement `SYSLIB0011` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8f06b-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="8f06b-106">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="8f06b-106">Workarounds</span></span>

<span data-ttu-id="8f06b-107">Envisagez d’utiliser ou à la <xref:System.Text.Json.JsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> place de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .</span><span class="sxs-lookup"><span data-stu-id="8f06b-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="8f06b-108">Pour plus d’informations sur les actions recommandées, consultez [résolution des erreurs BinaryFormatter obsoletion et des erreurs de désactivation](https://aka.ms/binaryformatter).</span><span class="sxs-lookup"><span data-stu-id="8f06b-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="8f06b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f06b-109">See also</span></span>

- [<span data-ttu-id="8f06b-110">Résolution des erreurs BinaryFormatter obsoletion et de la désactivation</span><span class="sxs-lookup"><span data-stu-id="8f06b-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](https://aka.ms/binaryformatter)
- [<span data-ttu-id="8f06b-111">Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8f06b-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](core-libraries/5.0/binaryformatter-serialization-obsolete.md)
