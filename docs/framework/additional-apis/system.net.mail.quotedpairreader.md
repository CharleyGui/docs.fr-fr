---
title: QuotedPairReader, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990374"
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

### <a name="return-value"></a>Valeur retournée

<xref:System.Int32?displayProperty=nameWithType>

`0`Si le caractère à l’index spécifié n’est pas placé dans une séquence d’échappement ; Sinon, le nombre de caractères entre guillemets consécutifs jusqu’à et y compris le caractère situé à `index` .

### <a name="exceptions"></a>Exceptions

<xref:System.FormatException?displayProperty=nameWithType>

Un caractère Unicode placé dans une séquence d’échappement a été trouvé, mais n’est pas autorisé.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
