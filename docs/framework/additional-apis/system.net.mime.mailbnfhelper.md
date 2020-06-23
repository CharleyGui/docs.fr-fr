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
# <a name="mailbnfhelper-class"></a><span data-ttu-id="7d6d7-102">MailBnfHelper, classe</span><span class="sxs-lookup"><span data-stu-id="7d6d7-102">MailBnfHelper class</span></span>

<span data-ttu-id="7d6d7-103">Contient des méthodes utilitaires pour analyser des chaînes au format de message Internet.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-103">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="7d6d7-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="7d6d7-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7d6d7-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="7d6d7-107">Champ Ascii7bitMaxValue</span><span class="sxs-lookup"><span data-stu-id="7d6d7-107">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="7d6d7-108">Représente la valeur ASCII 7 bits maximale.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-108">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="7d6d7-109">Champ comme un</span><span class="sxs-lookup"><span data-stu-id="7d6d7-109">Atext field</span></span>

<span data-ttu-id="7d6d7-110">Représente les caractères autorisés dans les atomes.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-110">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="7d6d7-111">Champ CR</span><span class="sxs-lookup"><span data-stu-id="7d6d7-111">CR field</span></span>

<span data-ttu-id="7d6d7-112">Représente le caractère de retour chariot.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-112">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="7d6d7-113">Champ CTEXT</span><span class="sxs-lookup"><span data-stu-id="7d6d7-113">Ctext field</span></span>

<span data-ttu-id="7d6d7-114">Représente les caractères autorisés dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-114">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="7d6d7-115">Champ point</span><span class="sxs-lookup"><span data-stu-id="7d6d7-115">Dot field</span></span>

<span data-ttu-id="7d6d7-116">Représente le caractère d’arrêt complet ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="7d6d7-116">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="7d6d7-117">Champ d’en-dCom</span><span class="sxs-lookup"><span data-stu-id="7d6d7-117">EndComment field</span></span>

<span data-ttu-id="7d6d7-118">Représente le caractère qui spécifie la fin d’un commentaire.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-118">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="7d6d7-119">Champ LF</span><span class="sxs-lookup"><span data-stu-id="7d6d7-119">LF field</span></span>

<span data-ttu-id="7d6d7-120">Représente le caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-120">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="7d6d7-121">Champ espace</span><span class="sxs-lookup"><span data-stu-id="7d6d7-121">Space field</span></span>

<span data-ttu-id="7d6d7-122">Représente le caractère d’espacement.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-122">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="7d6d7-123">Champ StartComment</span><span class="sxs-lookup"><span data-stu-id="7d6d7-123">StartComment field</span></span>

<span data-ttu-id="7d6d7-124">Représente le caractère qui spécifie le début d’un commentaire.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-124">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="7d6d7-125">Champ d’onglet</span><span class="sxs-lookup"><span data-stu-id="7d6d7-125">Tab field</span></span>

<span data-ttu-id="7d6d7-126">Représente le caractère de tabulation.</span><span class="sxs-lookup"><span data-stu-id="7d6d7-126">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="7d6d7-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7d6d7-127">Requirements</span></span>

<span data-ttu-id="7d6d7-128">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7d6d7-128">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7d6d7-129">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="7d6d7-129">**Assembly:** System (in System.dll)</span></span>
