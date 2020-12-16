---
title: AVERTISSEMENT SYSLIB0011
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0011.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 36292cc5314e2b7677d705780880b7e25ae0dfb6
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596523"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a>SYSLIB0011 : la sérialisation BinaryFormatter est obsolète

En raison de [failles de sécurité](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) dans <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , les API suivantes sont marquées comme obsolètes, à partir de .net 5,0. Leur utilisation dans le code génère un avertissement `SYSLIB0011` au moment de la compilation.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a>Solutions de contournement

Envisagez d’utiliser ou à la <xref:System.Text.Json.JsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> place de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .

Pour plus d’informations sur les actions recommandées, consultez [résolution des erreurs BinaryFormatter obsoletion et des erreurs de désactivation](https://aka.ms/binaryformatter).

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [Résolution des erreurs BinaryFormatter obsoletion et de la désactivation](https://aka.ms/binaryformatter)
- [Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
