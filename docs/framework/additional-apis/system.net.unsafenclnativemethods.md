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
# <a name="unsafenclnativemethods-class"></a>UnsafeNclNativeMethods, classe

Contient des classes qui importent des méthodes de mise en réseau natives non sécurisées. Cette classe ne peut pas être héritée.

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="nativepki-class"></a>NativePKI, classe

Contient les méthodes importées à partir de crypt32.dll. Ces méthodes gèrent les certificats lors de l’utilisation du protocole HTTPs (Hypertext Transfer Protocol Secure). Cette classe ne peut pas être héritée.

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a>Méthode NativePKI. FindClientCertificates

Détecte les certificats clients disponibles à envoyer au serveur.

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a>Valeur retournée

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

Collection de certificats clients disponibles.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
