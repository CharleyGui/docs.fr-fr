---
title: UnsafeNclNativeMethods, classe (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990324"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="bbe93-102">UnsafeNclNativeMethods, classe</span><span class="sxs-lookup"><span data-stu-id="bbe93-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="bbe93-103">Contient des classes qui importent des méthodes de mise en réseau natives non sécurisées.</span><span class="sxs-lookup"><span data-stu-id="bbe93-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="bbe93-104">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="bbe93-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="bbe93-105">Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="bbe93-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bbe93-106">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="bbe93-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="bbe93-107">NativePKI, classe</span><span class="sxs-lookup"><span data-stu-id="bbe93-107">NativePKI class</span></span>

<span data-ttu-id="bbe93-108">Contient les méthodes importées à partir de crypt32.dll.</span><span class="sxs-lookup"><span data-stu-id="bbe93-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="bbe93-109">Ces méthodes gèrent les certificats lors de l’utilisation du protocole HTTPs (Hypertext Transfer Protocol Secure).</span><span class="sxs-lookup"><span data-stu-id="bbe93-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="bbe93-110">Cette classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="bbe93-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="bbe93-111">Méthode NativePKI. FindClientCertificates</span><span class="sxs-lookup"><span data-stu-id="bbe93-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="bbe93-112">Détecte les certificats clients disponibles à envoyer au serveur.</span><span class="sxs-lookup"><span data-stu-id="bbe93-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="bbe93-113">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="bbe93-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="bbe93-114">Collection de certificats clients disponibles.</span><span class="sxs-lookup"><span data-stu-id="bbe93-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbe93-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bbe93-115">Requirements</span></span>

<span data-ttu-id="bbe93-116">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="bbe93-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="bbe93-117">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="bbe93-117">**Assembly:** System (in System.dll)</span></span>
