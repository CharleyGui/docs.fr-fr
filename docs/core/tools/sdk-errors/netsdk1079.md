---
title: 'NETSDK1079 : le package Microsoft. AspNetCore. All n’est pas pris en charge quand vous ciblez .NET Core 3,0 ou une version ultérieure.'
description: Comment résoudre la migration à partir de Microsoft. AspNetCore. app
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445779"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a><span data-ttu-id="9149b-103">NETSDK1079 : le package Microsoft. AspNetCore. All n’est pas pris en charge quand vous ciblez .NET Core 3,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9149b-103">NETSDK1079: The Microsoft.AspNetCore.All package is not supported when targeting .NET Core 3.0 or higher.</span></span>

<span data-ttu-id="9149b-104">**Cet article s’applique à :** ✔️ kit SDK .net Core 3.1.100 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9149b-104">**This article applies to:** ✔️ .NET Core SDK 3.1.100 and later versions</span></span>

<span data-ttu-id="9149b-105">Vous pouvez recevoir ce message d’erreur dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="9149b-105">You may receive this error message when:</span></span>

- <span data-ttu-id="9149b-106">Vous reciblez un projet de ASP.NET Core à partir de .NET Core 2,2 ou d’une version antérieure vers .NET Core 3,0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9149b-106">You retarget an ASP.NET Core project from .NET Core 2.2 or earlier to .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="9149b-107">Le projet utilise le package Microsoft. AspNetCore. All.</span><span class="sxs-lookup"><span data-stu-id="9149b-107">The project uses the Microsoft.AspNetCore.All package.</span></span>

<span data-ttu-id="9149b-108">Supprimez `PackageReference` pour Microsoft. AspNetCore. All.</span><span class="sxs-lookup"><span data-stu-id="9149b-108">Remove the `PackageReference` for Microsoft.AspNetCore.All.</span></span>  <span data-ttu-id="9149b-109">Vous devrez peut-être également ajouter des références de package pour les packages qui ont été référencés à partir de Microsoft. AspNetCore. All, mais qui ne sont pas inclus dans le ASP.NET Core Framework partagé.</span><span class="sxs-lookup"><span data-stu-id="9149b-109">You may also need to add package references for packages that were referenced from Microsoft.AspNetCore.All but are not included in the ASP.NET Core shared framework.</span></span>  <span data-ttu-id="9149b-110">Ces packages sont répertoriés ici : [migration de Microsoft. AspNetCore. All vers Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="9149b-110">These packages are listed here: [Migrating from Microsoft.AspNetCore.All to Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span></span>

<span data-ttu-id="9149b-111">Voir aussi [migrer de ASP.NET Core 2,2 à 3,0](/aspnet/core/migration/22-to-30)</span><span class="sxs-lookup"><span data-stu-id="9149b-111">See also [Migrate from ASP.NET Core 2.2 to 3.0](/aspnet/core/migration/22-to-30)</span></span>
