---
title: Méthode MemoryStream. InternalGetOriginAndLength (System.IO)
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d82b5080e9fbd5fc6603f1cddae996c75a06d3a3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215463"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="e2272-102">MemoryStream. InternalGetOriginAndLength, méthode</span><span class="sxs-lookup"><span data-stu-id="e2272-102">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="e2272-103">Obtient les valeurs internes de l’origine et de la longueur du flux de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e2272-103">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="e2272-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2272-104">Parameters</span></span>

- <span data-ttu-id="e2272-105">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="e2272-105">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="e2272-106">Lorsque cette méthode est retournée, offset du tableau d’octets spécifié lors de la création d’un objet <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="e2272-106">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="e2272-107">Contient 0 si le tableau d’octets a été créé par <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="e2272-107">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="e2272-108">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="e2272-108">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="e2272-109">Lorsque cette méthode est retournée, nombre d’octets dans le flux de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e2272-109">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2272-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e2272-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e2272-111">La méthode `MemoryStream.InternalGetOriginAndLength` est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e2272-111">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e2272-112">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="e2272-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2272-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e2272-113">Requirements</span></span>

<span data-ttu-id="e2272-114">**Espace de noms :** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="e2272-114">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="e2272-115">**Assembly :** mscorlib. dll (dans mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="e2272-115">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="e2272-116">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="e2272-116">**.NET Framework versions:** Available since 2.0.</span></span>
