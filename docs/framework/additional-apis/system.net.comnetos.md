---
title: ComNetOS, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990401"
---
# <a name="comnetos-class"></a><span data-ttu-id="6ab67-102">ComNetOS, classe</span><span class="sxs-lookup"><span data-stu-id="6ab67-102">ComNetOS class</span></span>

<span data-ttu-id="6ab67-103">Fournit des informations sur le système d’exploitation actuel, telles que sa version et son type d’installation (client ou serveur).</span><span class="sxs-lookup"><span data-stu-id="6ab67-103">Provides information about the current operating system, such as its version and installation type (client or server).</span></span> <span data-ttu-id="6ab67-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="6ab67-104">This class cannot be inherited.</span></span>
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> <span data-ttu-id="6ab67-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6ab67-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6ab67-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="6ab67-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="iswin7orlater-field"></a><span data-ttu-id="6ab67-107">Champ IsWin7orLater</span><span class="sxs-lookup"><span data-stu-id="6ab67-107">IsWin7orLater field</span></span>

<span data-ttu-id="6ab67-108">Spécifie si la version du système d’exploitation est Windows 7 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6ab67-108">Specifies whether the operating system version is Windows 7 or later.</span></span>

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a><span data-ttu-id="6ab67-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ab67-109">Requirements</span></span>

<span data-ttu-id="6ab67-110">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6ab67-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6ab67-111">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="6ab67-111">**Assembly:** System (in System.dll)</span></span>
