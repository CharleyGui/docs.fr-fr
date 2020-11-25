---
title: Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 9386918f3574720d90bda7e8da592fa0c91160e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708242"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="79615-102">Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="79615-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>

<span data-ttu-id="79615-103">L’[outil Type Library Exporter](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) charge une bibliothèque de liens dynamiques nommée TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="79615-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="79615-104">Cette DLL contient deux fonctions d’assistance et une interface que l’outil exportateur utilise pendant le processus de conversion de l’assembly à la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="79615-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79615-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="79615-105">In This Section</span></span>  

 [<span data-ttu-id="79615-106">Fonction GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="79615-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="79615-107">Fournit des informations sur la localisation et le système d’exploitation pour une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="79615-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="79615-108">LoadTypeLibWithResolver, fonction</span><span class="sxs-lookup"><span data-stu-id="79615-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="79615-109">Charge une bibliothèque de types à l’aide d’une implémentation de l’[interface ITypeLibResolver](itypelibresolver-interface.md) pour résoudre tous les types de bibliothèques référencés.</span><span class="sxs-lookup"><span data-stu-id="79615-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="79615-110">ITypeLibResolver, interface</span><span class="sxs-lookup"><span data-stu-id="79615-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="79615-111">Fournit la [méthode ResolveTypeLib](resolvetypelib-method.md), qui retourne le chemin d’accès complet d’une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="79615-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
