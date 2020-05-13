---
title: Emplacement d’assembly
description: L’emplacement d’un assembly .NET détermine la façon dont le CLR le trouve et s’il peut être partagé avec d’autres assemblys.
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 7ab3804b14b586e1430d654f4da32a310bcb6cc9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379891"
---
# <a name="assembly-location"></a><span data-ttu-id="98441-103">Emplacement d’assembly</span><span class="sxs-lookup"><span data-stu-id="98441-103">Assembly location</span></span>
<span data-ttu-id="98441-104">L’emplacement d’un assembly détermine si le common language runtime peut le localiser quand il est référencé, et il peut aussi déterminer si l’assembly peut être partagé avec d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="98441-104">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="98441-105">Vous pouvez déployer un assembly dans les emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="98441-105">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="98441-106">Répertoire ou sous-répertoires de l’application.</span><span class="sxs-lookup"><span data-stu-id="98441-106">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="98441-107">Il s’agit de l’emplacement le plus courant pour déployer un assembly.</span><span class="sxs-lookup"><span data-stu-id="98441-107">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="98441-108">Les sous-répertoires du répertoire racine d’une application peuvent être basés sur la langue ou la culture.</span><span class="sxs-lookup"><span data-stu-id="98441-108">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="98441-109">Si un assembly a des informations de l’attribut de culture, il doit se trouver dans un sous-répertoire sous le répertoire de l’application avec le nom de cette culture.</span><span class="sxs-lookup"><span data-stu-id="98441-109">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="98441-110">Le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="98441-110">The global assembly cache.</span></span>

     <span data-ttu-id="98441-111">Il s’agit d’un cache de code au niveau de la machine, qui est installé partout où le common language runtime est installé.</span><span class="sxs-lookup"><span data-stu-id="98441-111">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="98441-112">Dans la plupart des cas, si vous prévoyez de partager un assembly entre plusieurs applications, vous devez le déployer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="98441-112">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="98441-113">Sur un serveur HTTP.</span><span class="sxs-lookup"><span data-stu-id="98441-113">On an HTTP server.</span></span>

     <span data-ttu-id="98441-114">Un assembly déployé sur un serveur HTTP doit avoir un nom fort ; vous pointez vers l’assembly dans la section codebase du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="98441-114">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="98441-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98441-115">See also</span></span>

- [<span data-ttu-id="98441-116">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="98441-116">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="98441-117">Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="98441-117">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="98441-118">Comment le runtime localise les assemblys</span><span class="sxs-lookup"><span data-stu-id="98441-118">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
