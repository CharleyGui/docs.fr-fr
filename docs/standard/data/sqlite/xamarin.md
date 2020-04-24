---
title: Limitations de Xamarin
ms.date: 12/13/2019
description: Décrit certaines des limitations que vous pouvez rencontrer lors de l’utilisation de Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447166"
---
# <a name="xamarin-limitations"></a>Limitations de Xamarin

Les cibles Microsoft. Data. sqlite .NET Standard 2,0 et sont prises en charge sur Xamarin. Le tableau suivant indique les plateformes pour lesquelles le bundle SQLitePCLRaw par défaut fournit des binaires SQLite natifs. Pour plus d’informations sur l’utilisation d’un bundle différent ou la fourniture de vos propres binaires SQLite natifs, consultez [versions SQLite personnalisées](custom-versions.md) .

| Plateforme | Fichiers binaires SQLite |
| --- | --- |
| **Xamarin.Android** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | ✔ |
| **Xamarin.iOS** | ✔ |
| **Xamarin.Mac** | ✔ |
| **Xamarin. TVOS** | ✔ |
| **UWP** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |

## <a name="ios"></a>iOS

Microsoft. Data. sqlite tente d’initialiser automatiquement les bottes SQLitePCLRaw. Malheureusement, en raison des limitations de la compilation de l’AOA (Xamarin. iOS) pour. iOS, la tentative échoue et vous recevez l’erreur suivante.

> Vous devez appeler `SQLitePCL.raw.SetProvider()`. Si vous utilisez un package de Bundle, cette opération s’effectue en `SQLitePCL.Batteries.Init()`appelant.

Pour initialiser le bundle, ajoutez la ligne de code suivante à votre application avant d’utiliser Microsoft. Data. sqlite.

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a>Voir aussi

* [Limitations Async](async.md)
* [Versions SQLite personnalisées](custom-versions.md)
