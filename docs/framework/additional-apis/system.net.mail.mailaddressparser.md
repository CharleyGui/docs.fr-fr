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
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051348"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="69c52-102">MailAddressParser, classe</span><span class="sxs-lookup"><span data-stu-id="69c52-102">MailAddressParser class</span></span>

<span data-ttu-id="69c52-103">Analyse les adresses de messagerie comme indiqué dans le document RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="69c52-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="69c52-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="69c52-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="69c52-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="69c52-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="69c52-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="69c52-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="69c52-107">Méthode ParseAddress</span><span class="sxs-lookup"><span data-stu-id="69c52-107">ParseAddress method</span></span>

<span data-ttu-id="69c52-108">Analyse une seule adresse e-mail à partir de la chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="69c52-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="69c52-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69c52-109">Parameters</span></span>

<span data-ttu-id="69c52-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="69c52-110">`data` <xref:System.String></span></span>

<span data-ttu-id="69c52-111">Chaîne qui contient une adresse de messagerie à analyser.</span><span class="sxs-lookup"><span data-stu-id="69c52-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="69c52-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="69c52-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="69c52-113">Une adresse e-mail valide.</span><span class="sxs-lookup"><span data-stu-id="69c52-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="69c52-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="69c52-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="69c52-115">L’adresse de messagerie n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="69c52-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="69c52-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="69c52-116">Requirements</span></span>

<span data-ttu-id="69c52-117">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="69c52-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="69c52-118">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="69c52-118">**Assembly:** System (in System.dll)</span></span>
