---
title: MailAddressParser, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990386"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="cac53-102">MailAddressParser, classe</span><span class="sxs-lookup"><span data-stu-id="cac53-102">MailAddressParser class</span></span>

<span data-ttu-id="cac53-103">Analyse les adresses de messagerie comme indiqué dans le document RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="cac53-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="cac53-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="cac53-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="cac53-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="cac53-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cac53-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="cac53-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="cac53-107">Méthode ParseAddress</span><span class="sxs-lookup"><span data-stu-id="cac53-107">ParseAddress method</span></span>

<span data-ttu-id="cac53-108">Analyse une seule adresse e-mail à partir de la chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cac53-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="cac53-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cac53-109">Parameters</span></span>

<span data-ttu-id="cac53-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="cac53-110">`data` <xref:System.String></span></span>

<span data-ttu-id="cac53-111">Chaîne qui contient une adresse de messagerie à analyser.</span><span class="sxs-lookup"><span data-stu-id="cac53-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="cac53-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="cac53-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="cac53-113">Une adresse e-mail valide.</span><span class="sxs-lookup"><span data-stu-id="cac53-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="cac53-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="cac53-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="cac53-115">L’adresse de messagerie n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="cac53-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="cac53-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cac53-116">Requirements</span></span>

<span data-ttu-id="cac53-117">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="cac53-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="cac53-118">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="cac53-118">**Assembly:** System (in System.dll)</span></span>
