---
title: QuotedPairReader, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 898c6e9d2d5dd02f3d5f9c096ad470b5dd445d1d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051309"
---
# <a name="quotedpairreader-class"></a>QuotedPairReader, classe

Détermine quels caractères sont placés entre guillemets (dans une séquence d’échappement) dans une chaîne entre guillemets. Cette classe ne peut pas être héritée.

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="countquotedchars-method"></a>Méthode CountQuotedChars

Compte le nombre de caractères entre guillemets consécutifs, y compris les barres obliques inverses précédentes entre guillemets, dans la chaîne spécifiée. Par exemple, étant donné la chaîne `a\\\b` et un index de `4` , la méthode retourne `4` , car `b` est placé entre guillemets et sont les trois barres obliques inverses précédentes.

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a>Paramètres

- `data` <xref:System.String>

  Chaîne de données dans laquelle compter les caractères entre guillemets consécutifs.

- `index` <xref:System.Int32>

  Position dans la chaîne spécifiée jusqu’à laquelle inclure les guillemets consécutifs.

- `permitUnicodeEscaping` <xref:System.Boolean>

  `true`pour autoriser les caractères Unicode à être placés dans une séquence d’échappement ; Sinon, `false` .

### <a name="return-value"></a>Valeur renvoyée

<xref:System.Int32?displayProperty=nameWithType>

`0`Si le caractère à l’index spécifié n’est pas placé dans une séquence d’échappement ; Sinon, le nombre de caractères entre guillemets consécutifs jusqu’à et y compris le caractère situé à `index` .

### <a name="exceptions"></a>Exceptions

<xref:System.FormatException?displayProperty=nameWithType>

Un caractère Unicode placé dans une séquence d’échappement a été trouvé, mais n’est pas autorisé.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
