---
title: MailAddressParser, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051348"
---
# <a name="mailaddressparser-class"></a>MailAddressParser, classe

Analyse les adresses de messagerie comme indiqué dans le document RFC 2822. Cette classe ne peut pas être héritée.

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="parseaddress-method"></a>Méthode ParseAddress

Analyse une seule adresse e-mail à partir de la chaîne spécifiée.

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>Paramètres

`data` <xref:System.String>

Chaîne qui contient une adresse de messagerie à analyser.

### <a name="return-value"></a>Valeur retournée

<xref:System.Net.Mail.MailAddress>

Une adresse e-mail valide.

### <a name="exceptions"></a>Exceptions

<xref:System.FormatException?displayProperty=nameWithType>

L’adresse de messagerie n’est pas valide.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
