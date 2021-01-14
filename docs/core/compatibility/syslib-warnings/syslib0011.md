---
title: AVERTISSEMENT SYSLIB0011
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0011.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 85b5e07b1ecd6852d8c8e93cc3e89ced4b021ef9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189855"
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

Pour plus d’informations sur les actions recommandées, consultez [résolution des erreurs BinaryFormatter obsoletion et des erreurs de désactivation](../../../standard/serialization/binaryformatter-security-guide.md).

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [Résolution des erreurs BinaryFormatter obsoletion et de la désactivation](../../../standard/serialization/binaryformatter-security-guide.md)
- [Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
