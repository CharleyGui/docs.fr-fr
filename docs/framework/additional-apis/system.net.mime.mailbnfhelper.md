---
title: MailBnfHelper, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990369"
---
# <a name="mailbnfhelper-class"></a>MailBnfHelper, classe

Contient des méthodes utilitaires pour analyser des chaînes au format de message Internet. Cette classe ne peut pas être héritée.

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="ascii7bitmaxvalue-field"></a>Champ Ascii7bitMaxValue

Représente la valeur ASCII 7 bits maximale.

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a>Champ comme un

Représente les caractères autorisés dans les atomes.

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a>Champ CR

Représente le caractère de retour chariot.

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a>Champ CTEXT

Représente les caractères autorisés dans les commentaires.

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a>Champ point

Représente le caractère d’arrêt complet ( `.` ).

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a>Champ d’en-dCom

Représente le caractère qui spécifie la fin d’un commentaire.

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a>Champ LF

Représente le caractère de saut de ligne.

```csharp
internal static readonly char LF
```

## <a name="space-field"></a>Champ espace

Représente le caractère d’espacement.

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a>Champ StartComment

Représente le caractère qui spécifie le début d’un commentaire.

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a>Champ d’onglet

Représente le caractère de tabulation.

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
