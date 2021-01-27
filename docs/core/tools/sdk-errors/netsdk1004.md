---
title: 'NETSDK1004 : fichier de ressources introuvable'
description: En savoir plus sur l’erreur du kit de développement logiciel (SDK) .NET NETSDK1004, qui se produit lorsque l' project.assets.jssur le fichier est introuvable.
ms.topic: error-reference
ms.date: 01/26/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: ed42ad0e8ebef7362cc029125fe51d3f300acbae
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98900359"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="2399a-103">NETSDK1004 : fichier de ressources introuvable</span><span class="sxs-lookup"><span data-stu-id="2399a-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="2399a-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="2399a-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="2399a-105">Cette erreur se produit lorsque le fichier *de ressourcesproject.assets.jssur* est introuvable lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="2399a-105">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="2399a-106">Le message d’erreur complet est semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2399a-106">The full error message is similar to:</span></span>

<span data-ttu-id="2399a-107">**NETSDK1004 : le fichier de ressources' C:\IncorrectPath\project.assets.json’est introuvable. Exécutez une restauration de package NuGet pour générer ce fichier.**</span><span class="sxs-lookup"><span data-stu-id="2399a-107">**NETSDK1004: Assets file 'C:\IncorrectPath\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="2399a-108">Vous pouvez rencontrer un avertissement NETSDK1004 si vous exécutez la `dotnet build` commande à partir d’un chemin d’accès de répertoire contenant un `%` caractère.</span><span class="sxs-lookup"><span data-stu-id="2399a-108">One reason you might encounter warning NETSDK1004 is if you run the `dotnet build` command from a directory path that contains a `%` character.</span></span>
