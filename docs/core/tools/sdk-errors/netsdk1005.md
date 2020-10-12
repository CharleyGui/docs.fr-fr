---
title: 'NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia'
description: La résolution du problème d’un fichier de ressources n’a pas de cible.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957151"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="d2479-103">NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia</span><span class="sxs-lookup"><span data-stu-id="d2479-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="d2479-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .NET 2.1.100 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="d2479-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="d2479-105">Lorsque le kit de développement logiciel (SDK) .NET émet une erreur NETSDK1005 ou NETSDK1047, le fichier de ressources du projet ne contient pas d’informations sur l’un de vos frameworks cibles.</span><span class="sxs-lookup"><span data-stu-id="d2479-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="d2479-106">Ce problème peut généralement être résolu en s’assurant que la restauration est exécutée et que la valeur cible manquante est incluse dans la `TargetFrameworks` propriété de votre projet.</span><span class="sxs-lookup"><span data-stu-id="d2479-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="d2479-107">Il y avait un problème connu avec les premières versions de .NET 5 Preview 8 lorsqu’il était utilisé avec les versions de Visual Studio 16,8 préliminaires qui ont provoqué cette erreur.</span><span class="sxs-lookup"><span data-stu-id="d2479-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="d2479-108">Plus précisément, si la cible manquante est `net5.0-windows7.0` ou `net5.0` , assurez-vous que vous avez mis à jour vers les dernières versions de Visual Studio et du kit de développement logiciel (SDK) .net 5.</span><span class="sxs-lookup"><span data-stu-id="d2479-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
