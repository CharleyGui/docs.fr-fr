---
title: s_isDebuggerCheckDisabledForTestPurposes, champ
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: ad9bc0ecf4b7a8e5f3ef13fdff5aa59ca8915922
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634657"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="d7e62-102">s_isDebuggerCheckDisabledForTestPurposes, champ</span><span class="sxs-lookup"><span data-stu-id="d7e62-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="d7e62-103">Ce champ privé dans le `System.Windows.Diagnostics.VisualDiagnostics` classe est utilisée par Visual Studio pour déterminer si une vérification interne de débogueur actif sera effectuée.</span><span class="sxs-lookup"><span data-stu-id="d7e62-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7e62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7e62-104">Syntax</span></span>

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> <span data-ttu-id="d7e62-105">API dans le `System.Windows.Diagnostics.VisualDiagnostics` classe sont disponibles uniquement quand une application s’exécute sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d7e62-105">APIs in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="d7e62-106">Définissez `s_isDebuggerCheckDisabledForTestPurposes` à `true` pour accéder aux API en dehors d’un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d7e62-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>
>
> <span data-ttu-id="d7e62-107">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="d7e62-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7e62-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d7e62-108">Requirements</span></span>

<span data-ttu-id="d7e62-109">**Espace de noms :** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="d7e62-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="d7e62-110">**Assembly :** PresentationCore (dans PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="d7e62-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="d7e62-111">**Versions du .NET framework :** Disponible à partir de 4.6.</span><span class="sxs-lookup"><span data-stu-id="d7e62-111">**.NET Framework versions:** Available since 4.6.</span></span>
