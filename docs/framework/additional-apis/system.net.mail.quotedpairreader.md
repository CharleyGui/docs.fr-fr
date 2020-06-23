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
# <a name="quotedpairreader-class"></a><span data-ttu-id="10cb6-102">QuotedPairReader, classe</span><span class="sxs-lookup"><span data-stu-id="10cb6-102">QuotedPairReader class</span></span>

<span data-ttu-id="10cb6-103">Détermine quels caractères sont placés entre guillemets (dans une séquence d’échappement) dans une chaîne entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="10cb6-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="10cb6-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="10cb6-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="10cb6-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="10cb6-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="10cb6-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="10cb6-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="10cb6-107">Méthode CountQuotedChars</span><span class="sxs-lookup"><span data-stu-id="10cb6-107">CountQuotedChars method</span></span>

<span data-ttu-id="10cb6-108">Compte le nombre de caractères entre guillemets consécutifs, y compris les barres obliques inverses précédentes entre guillemets, dans la chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="10cb6-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="10cb6-109">Par exemple, étant donné la chaîne `a\\\b` et un index de `4` , la méthode retourne `4` , car `b` est placé entre guillemets et sont les trois barres obliques inverses précédentes.</span><span class="sxs-lookup"><span data-stu-id="10cb6-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="10cb6-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10cb6-110">Parameters</span></span>

- <span data-ttu-id="10cb6-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="10cb6-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="10cb6-112">Chaîne de données dans laquelle compter les caractères entre guillemets consécutifs.</span><span class="sxs-lookup"><span data-stu-id="10cb6-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="10cb6-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="10cb6-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="10cb6-114">Position dans la chaîne spécifiée jusqu’à laquelle inclure les guillemets consécutifs.</span><span class="sxs-lookup"><span data-stu-id="10cb6-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="10cb6-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="10cb6-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="10cb6-116">`true`pour autoriser les caractères Unicode à être placés dans une séquence d’échappement ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="10cb6-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="10cb6-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="10cb6-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="10cb6-118">`0`Si le caractère à l’index spécifié n’est pas placé dans une séquence d’échappement ; Sinon, le nombre de caractères entre guillemets consécutifs jusqu’à et y compris le caractère situé à `index` .</span><span class="sxs-lookup"><span data-stu-id="10cb6-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="10cb6-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="10cb6-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="10cb6-120">Un caractère Unicode placé dans une séquence d’échappement a été trouvé, mais n’est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="10cb6-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="10cb6-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="10cb6-121">Requirements</span></span>

<span data-ttu-id="10cb6-122">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="10cb6-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="10cb6-123">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="10cb6-123">**Assembly:** System (in System.dll)</span></span>
