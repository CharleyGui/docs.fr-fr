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
# <a name="quotedpairreader-class"></a><span data-ttu-id="bf5bb-102">QuotedPairReader, classe</span><span class="sxs-lookup"><span data-stu-id="bf5bb-102">QuotedPairReader class</span></span>

<span data-ttu-id="bf5bb-103">Détermine quels caractères sont placés entre guillemets (dans une séquence d’échappement) dans une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="bf5bb-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="bf5bb-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bf5bb-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="bf5bb-107">Méthode CountQuotedChars</span><span class="sxs-lookup"><span data-stu-id="bf5bb-107">CountQuotedChars method</span></span>

<span data-ttu-id="bf5bb-108">Compte le nombre de caractères entre guillemets consécutifs, y compris les barres obliques inverses précédentes entre guillemets, dans la chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="bf5bb-109">Par exemple, étant donné la chaîne `a\\\b` et un index de `4` , la méthode retourne `4` , car `b` est placé entre guillemets et sont les trois barres obliques inverses précédentes.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="bf5bb-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf5bb-110">Parameters</span></span>

- <span data-ttu-id="bf5bb-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="bf5bb-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="bf5bb-112">Chaîne de données dans laquelle compter les caractères entre guillemets consécutifs.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="bf5bb-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="bf5bb-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="bf5bb-114">Position dans la chaîne spécifiée jusqu’à laquelle inclure les guillemets consécutifs.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="bf5bb-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="bf5bb-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="bf5bb-116">`true`pour autoriser les caractères Unicode à être placés dans une séquence d’échappement ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="bf5bb-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="bf5bb-117">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bf5bb-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="bf5bb-118">`0`Si le caractère à l’index spécifié n’est pas placé dans une séquence d’échappement ; Sinon, le nombre de caractères entre guillemets consécutifs jusqu’à et y compris le caractère situé à `index` .</span><span class="sxs-lookup"><span data-stu-id="bf5bb-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="bf5bb-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="bf5bb-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="bf5bb-120">Un caractère Unicode placé dans une séquence d’échappement a été trouvé, mais n’est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="bf5bb-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf5bb-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf5bb-121">Requirements</span></span>

<span data-ttu-id="bf5bb-122">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="bf5bb-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="bf5bb-123">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="bf5bb-123">**Assembly:** System (in System.dll)</span></span>
